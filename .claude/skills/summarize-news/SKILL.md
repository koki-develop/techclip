---
name: summarize-news
description: "Summarize a single collected tech news topic in detail by reading full article content. Use this skill after collect-news has been run. Takes a topic file path (./topics/<yyyy>/<mm>/<dd>/<slug>.md) and generates a detailed summary as a Hugo post. Trigger when the user says things like 'summarize this topic', 'read the articles', 'detailed summary', 'summarize the news', '要約して', '詳しく読んで', '記事の内容をまとめて', or any request to dig deeper into a specific collected news topic."
allowed-tools: Agent, WebFetch, WebSearch, Read, Glob, Write, Edit, Bash
---

# Summarize News

Read the full content of each article from a single previously collected news topic (output of the `collect-news` skill), synthesize information across multiple sources covering the topic, and write a detailed summary as a Hugo post.

## Input

The user specifies a topic file path (e.g., `./topics/<yyyy>/<mm>/<dd>/<slug>.md`). If ambiguous, ask the user which topic file to summarize.

The topic file contains:
- A topic headline in Japanese (h1)
- Tags
- One or more article links with titles, URLs, and publication dates
- A brief 1-2 sentence overview

## Process

### Step 1: Read Topic File

Read the specified topic file and extract:
- Topic headline
- Tags
- All reference URLs, titles, and publication dates

Also extract the date components and slug from the file path. For `./topics/<yyyy>/<mm>/<dd>/<slug>.md`:
- Date: `<yyyy>/<mm>/<dd>`
- Slug: `<slug>`

### Step 2: Fetch and Analyze Articles

Use WebFetch to retrieve the full content of each article URL in the topic. If a fetch fails (paywall, 404, timeout), note it and proceed with the articles that were successfully fetched.

Extract the key information from each article:
- Core facts and announcements
- Technical details, specifications, benchmarks
- Quotes from key people
- Background context and history
- Impact and implications
- Future outlook or next steps mentioned

### Step 3: Write Summary

Combine the information from all articles into a single, coherent summary. The summary should:
- Lead with the most important takeaway
- Integrate information from all sources rather than summarizing each article separately
- Include technical details when present (versions, specs, benchmarks, etc.)
- Provide background context so the reader understands why this matters
- Note differing perspectives or additional context from different sources
- End with implications or outlook if the articles discuss them
- Be written in Japanese
- Target 3-5 paragraphs depending on the complexity and significance of the topic
- Use h2 (##) subheadings to break the summary into logical sections. Every summary must have at least 2 headed sections — choose headings that fit the topic (e.g., overview, technical details, background, future outlook). Do not write the body as plain paragraphs without any headings. Do not use h1 — the frontmatter title serves that role.

Also write:
- A title for the frontmatter `title` field. Do NOT reuse the topic headline as-is. Craft a title that accurately reflects the content of your synthesized summary — concise, informative, and suitable as an article headline. Written in Japanese.
- A one-sentence description for the frontmatter `description` field. This should concisely capture what happened, in Japanese.

### Step 4: Save Post File

Save the result to `./content/posts/[YYYY]/[MM]/[DD]/[SLUG].md`, using the same slug from the topic file path. Create the directories if they don't exist.

Use this exact format:

```markdown
---
date: "[YYYY-MM-DD]"
title: "[記事の内容に基づいて考えた適切なタイトル]"
description: "[1文でトピックの内容を説明]"
tags:
  - [CATEGORY1]
  - [CATEGORY2]
references:
  - "[ARTICLE1 URL]"
  - "[ARTICLE2 URL]"
---

## 概要

[Summary paragraph]

## 技術的な詳細

[Details paragraph]
```

**Example:** `./content/posts/2026/01/15/example-project-release.md`

```markdown
---
date: "2026-01-15"
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

### Step 5: Report Results

Report to the user:
- The output file path
- Any articles that could not be fetched (so the user is aware of gaps)

## Important Notes

- Some articles may be behind paywalls or block automated access. This is expected. Work with whatever content you can fetch and note any failures.
- The summary should feel like reading a well-written tech news brief, not a mechanical concatenation of article excerpts.
- If the post file for the same slug already exists, overwrite it.
