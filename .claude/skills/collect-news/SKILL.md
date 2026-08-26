---
name: collect-news
description: "Collect and organize tech news for a specific date (JST) by category (AI, Security, Cloud, Programming, OSS, etc.). Use this skill when the user wants to check tech news, asks 'what happened in tech today/yesterday', wants a news roundup, or mentions collecting/gathering tech news for a date. Also trigger when the user says things like 'today's tech news', 'news from March 10', or 'latest tech updates'. Results are saved as individual topic files under ./topics/<yyyy>/<mm>/<dd>/<slug>.md."
---

# Collect News

Collect tech news for a specified date (JST) as a flat topic list tagged with categories. Gather and pick highlights with a brief overview per topic — not deep summarization. Each topic is saved as an individual file.

## Input

A date, explicit ("2026-03-13", "3月13日") or relative ("today", "昨日"). Resolve relative dates in JST (Asia/Tokyo). Default to today (JST).

## Categories

1. **AI / Machine Learning** — LLM releases, model benchmarks, AI products, research papers, AI regulation
2. **Security** — vulnerabilities, breaches, CVEs, security tools, privacy regulations
3. **Cloud / Infrastructure** — AWS/GCP/Azure updates, Kubernetes, serverless, infrastructure tooling
4. **Programming Languages / Frameworks** — language releases, framework updates, new libraries
5. **OSS / Dev Tools** — OSS releases, developer tools, IDEs, CI/CD, package managers
6. **Other** — hardware, acquisitions, tech business news, events

## Phase 1: Category Search

Launch 6 search agents in parallel via the Agent tool, one per category:

```
You are collecting tech news for [CATEGORY] on [DATE] (JST).

Use WebSearch (2-3 queries, varied phrasing, include the date) to find up to 5
significant news items in this category.

Date filtering:
- Only include articles published between [DATE-7] and [DATE] inclusive.
- You MUST determine the publication date for every article — check the URL path
  (e.g. /2026/03/13/), the search snippet, or the page content via WebFetch.
- If you cannot determine the publication date, exclude the article.

Prefer established tech publications, official blogs, and reputable outlets
(TechCrunch, The Verge, Ars Technica, Wired, InfoQ, Publickey, Gihyo,
BleepingComputer, The Hacker News, Krebs on Security, official cloud provider
blogs, arXiv, ITmedia, GIGAZINE, Impress Watch). Avoid content farms, SEO
aggregators, and unverified blogs.

Return EXACTLY this format for each item:
- **[Title, in the language of the original article]**
  [URL]
  Published: [YYYY-MM-DD]
  [1-2 sentence overview in Japanese]

If fewer than 5 noteworthy items exist in range, return only what you find.
Do not pad with irrelevant or out-of-range items.
```

## Phase 2: Consolidation

1. **Verify dates.** Discard anything outside the 1-week window.
2. **Group into topics.** Articles covering the same event become one topic — e.g. a Patch Tuesday story from both BleepingComputer and The Hacker News is one topic with two articles.
3. **Assign tags.** A topic may carry several (an AI chip announcement can be both AI and Other).
4. **Exclude already-collected topics.** Both checks are required:
   - **URL check:** Grep `topics/` for each candidate article URL. Any hit means duplicate. Actually run Grep — do not rely on memory.
   - **Headline check:** Read the `# ...` headlines in `topics/YYYY/MM/DD/*.md` from the past 7 days and drop candidates describing the same event ("OpenAI releases GPT-5" ≡ "GPT-5が正式リリース"). Keep a follow-up only for a new official announcement, a materially different consequence, or a major escalation — not the same story reworded.
5. **Trim to the top 5 topics**, roughly 1-3 per category without forcing equal distribution. Prioritize impact, novelty (releases over opinion pieces), and breadth across categories.
6. **Order by significance**, not by category.
7. Write for each topic a **headline** (concise Japanese description of what happened, not the article title) and a **slug** (lowercase English, hyphens only, max ~5 words).

## Phase 3: Supplementary Search

For the top 3 topics that have only one article, launch parallel agents so readers get multiple perspectives:

```
Search for additional articles about this topic published between [DATE-7] and [DATE]:

Topic: [TOPIC HEADLINE]
Known article: [TITLE AND URL] (Published: [YYYY-MM-DD])

Use WebSearch (1-2 queries) to find 1-2 additional articles on the same story
from different, trustworthy sources. Only return articles in the date range,
with their publication date.

Return EXACTLY this format for each article:
- [Title]
  [URL]
  Published: [YYYY-MM-DD]

If none are found in range, return: NONE
```

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

Do not fabricate news — if search results are sparse, report fewer topics. After writing, report the output directory and the list of generated files.
