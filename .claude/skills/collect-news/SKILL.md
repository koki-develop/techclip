---
name: collect-news
description: Collects tech news for a date (JST) into topic files under topics/<yyyy>/<mm>/<dd>/, deduplicated against the previous 7 days.
argument-hint: "[YYYY/MM/DD]"
disable-model-invocation: true
---

# Collect News

Collect tech news as a flat list of topics tagged by category, one file per topic. This is highlight-gathering with a brief overview per topic, not deep summarization.

## Input

Target date: $ARGUMENTS

Explicit (`2026/03/13`, `2026-03-13`, `3月13日`) or relative (`today`, `昨日`). Resolve relative dates in JST (Asia/Tokyo), and default to today (JST) if none was given. The date range runs from 7 days before the target date through the target date, inclusive.

## Categories

These double as the topic tags:

- `AI` — LLMs, models, AI products, research, regulation
- `Security` — vulnerabilities, breaches, CVEs, security tooling, privacy
- `Cloud` — AWS/GCP/Azure, Kubernetes, serverless, infrastructure
- `Programming Languages` — language and framework releases, new libraries
- `OSS` — OSS releases, dev tools, IDEs, CI/CD, package managers
- `Other` — hardware, acquisitions, tech business, events

## Phase 1: Category search

Launch six `news-searcher` agents in parallel, one per category. Give each the category, the date range, and a target of up to 5 items.

## Phase 2: Consolidation

1. **Verify dates.** Discard anything outside the date range.
2. **Group into topics.** Articles covering the same event become one topic — a Patch Tuesday story from both BleepingComputer and The Hacker News is one topic with two articles.
3. **Assign tags.** A topic may carry several; an AI chip announcement can be both `AI` and `Other`.
4. **Exclude already-collected topics.** Both checks are required:
   - **URL check:** Grep `topics/` for each candidate article URL. Any hit means duplicate. Actually run Grep — do not rely on memory.
   - **Headline check:** Read the `# ...` headlines in `topics/YYYY/MM/DD/*.md` from the past 7 days and drop candidates describing the same event ("OpenAI releases GPT-5" ≡ "GPT-5が正式リリース"). Keep a follow-up only for a new official announcement, a materially different consequence, or a major escalation — not the same story reworded.
5. **Trim to the top 5 topics**, roughly 1-3 per category without forcing equal distribution. Prioritize impact, novelty (releases over opinion pieces), and breadth across categories.
6. **Order by significance**, not by category.
7. Write for each topic a **headline** (concise Japanese description of what happened, not the article title) and a **slug** (lowercase English, hyphens only, max ~5 words).

## Phase 3: Supplementary search

For each of the top 3 topics that has only one article, launch a `news-searcher` agent in parallel so readers get multiple perspectives. Give each the topic headline, the known article's title and URL, the date range, and a target of 1-2 additional articles on the same story from different sources.

## Output

Write each topic to `./topics/[YYYY]/[MM]/[DD]/[SLUG].md`, creating directories as needed. One topic per file:

```
# ExampleプロジェクトがバージョンX.Yをリリース、新機能Zを搭載
Tags: OSS, Programming Languages

- Example Project releases vX.Y with feature Z (2026-01-15)
  https://example.com/article1
- Example Project vX.Y: What's new and why it matters (2026-01-14)
  https://example.com/article2

ExampleプロジェクトがバージョンX.Yを正式リリース。主要な新機能として機能Zが追加され、処理速度の向上とAPIの改善が行われた。
```

Article titles stay in the original language; headline and overview are Japanese.

Do not fabricate news — if the searches come back sparse, write fewer topics. Report the output directory and the files written.
