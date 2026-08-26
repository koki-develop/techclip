---
name: summarize-news
description: Reads the full articles of one collected topic and writes them up as a detailed Hugo post under content/posts/<yyyy>/<mm>/<dd>/.
argument-hint: "[topic-file] [datetime]"
disable-model-invocation: true
---

# Summarize News

Read the full content of every article in a collected topic file (`collect-news` output), synthesize across the sources, and write a detailed summary as a Hugo post.

## Input

Topic file and datetime: $ARGUMENTS

A topic file path (`./topics/<yyyy>/<mm>/<dd>/<slug>.md`) and an ISO 8601 datetime (e.g. `2026-04-03T18:00:00+09:00`) that becomes the frontmatter `date`. If the topic file is ambiguous, ask which one to summarize.

## Process

1. **Read the topic file** — headline, tags, and each article's title, URL, and publication date. Take the date components and slug from the file path.

2. **Fetch each article** with WebFetch. If a fetch fails (paywall, 404, timeout), note it and continue with the rest. Extract core facts, technical details and benchmarks, quotes, background context, impact, and outlook.

3. **Write the summary** in Japanese, 3-5 paragraphs depending on the topic's complexity:
   - Lead with the most important takeaway.
   - Integrate all sources instead of summarizing each article in turn; note where sources differ or add context.
   - Keep technical details (versions, specs, benchmarks) and enough background that the reader sees why it matters. End with implications or outlook if the articles discuss them.
   - Use h2 subheadings, at least 2 sections, chosen to fit the topic. Never h1 — the frontmatter title fills that role.
   - It should read like a well-written tech news brief, not a concatenation of article excerpts.

   Also write a `title` — not the topic headline reused, but a headline reflecting the summary you actually wrote — and a one-sentence `description`. Both in Japanese.

4. **Save** to `./content/posts/[YYYY]/[MM]/[DD]/[SLUG].md` with the slug from the topic file path, creating directories as needed and overwriting any existing file:

```markdown
---
date: "2026-01-15T10:00:00+09:00"
title: "Exampleプロジェクト vX.Y がリリース、新機能Zで処理速度が大幅向上"
description: "ExampleプロジェクトがバージョンX.Yを正式リリースし、新機能Zによる処理速度の改善を発表した。"
tags:
  - OSS
  - Programming Languages
references:
  - "https://example.com/article1"
  - "https://example.com/article2"
---

## 概要

Exampleプロジェクトは1月15日、バージョンX.Yを正式にリリースした。...

## 技術的な詳細

新機能Zは従来の処理方式を刷新し、...
```

5. **Report** the output file path and any articles that could not be fetched.
