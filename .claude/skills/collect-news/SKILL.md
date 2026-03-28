---
name: collect-news
description: "Collect and organize tech news for a specific date (JST) by category (AI, Security, Cloud, Programming, OSS, etc.). Use this skill when the user wants to check tech news, asks 'what happened in tech today/yesterday', wants a news roundup, or mentions collecting/gathering tech news for a date. Also trigger when the user says things like 'today's tech news', 'news from March 10', or 'latest tech updates'. Results are saved as individual topic files under ./topics/<yyyy>/<mm>/<dd>/<slug>.md."
allowed-tools: Agent, WebFetch, WebSearch, Read, Glob, Write, Edit, Bash
---

# Collect News

Collect tech news for a specified date (JST timezone), organized as a flat topic list tagged with categories. The goal is to gather, pick highlights, and present a brief overview per topic — not deep summarization. Each topic is saved as an individual file.

## Input

The user specifies a date. It can be:
- Explicit: "2026-03-13", "3月13日"
- Relative: "today", "yesterday", "今日", "昨日"

Resolve relative dates using JST (Asia/Tokyo). If no date is given, default to today (JST).

## Categories

1. **AI / Machine Learning** — LLM releases, model benchmarks, AI products, research papers, AI regulation
2. **Security** — Vulnerabilities, breaches, CVEs, security tools, privacy regulations
3. **Cloud / Infrastructure** — AWS/GCP/Azure updates, Kubernetes, serverless, infrastructure tooling
4. **Programming Languages / Frameworks** — Language releases, framework updates, new libraries, language ecosystem news
5. **OSS / Dev Tools** — Open source project releases, developer tools, IDE updates, CI/CD, package managers
6. **Other** — Hardware, industry acquisitions, notable tech business news, events

## Collection Process (4 phases)

### Phase 0: Check Existing Topics

Before searching for new news, scan the `topics/` directory for recently collected topics to avoid duplication. Topics covering the same event or story that were already collected on a previous day should not appear again.

1. **Determine the scan range.** Look back 7 days from the target date. For target date 2026-03-13, scan `topics/2026/03/07/` through `topics/2026/03/13/`.

2. **Read existing topic files.** Use Glob to find all `./topics/YYYY/MM/DD/*.md` files within the scan range, then Read each file. Extract:
   - The topic headline (the `# ...` line)
   - All article URLs listed in the file

3. **Build an exclusion list.** Compile the collected headlines and URLs into a list. This list will be used in Phase 2 for deduplication.

### Phase 1: Category-based Parallel Search

Launch 6 parallel search agents (one per category) using the Agent tool. Each agent uses WebSearch to find news for the target date.

**Search agent instructions:**

Each agent should:

1. **Run 2-3 WebSearch queries** with varied phrasing to get good coverage. Include the date in the query. Examples for the AI category on 2026-03-13:
   - `"AI news March 13 2026"`
   - `"LLM machine learning news 2026-03-13"`
   - `"AI announcement March 2026"` (broader, catches items from that week)

2. **Filter by publication date — strict 1-week window.** Only include articles published within 7 days before the target date (inclusive). For 2026-03-13, that means articles from 2026-03-07 to 2026-03-13. Articles older than this window must be excluded, even if they are relevant to the topic. When the publication date cannot be determined from the search results, use WebFetch or check the article page to confirm. If the date still cannot be determined, exclude the article.

3. **Determine the publication date for every article.** This is mandatory — every returned article must include its publication date. Check the search result snippet, article URL (many contain dates like `/2026/03/13/`), or the page content. If an article's date cannot be determined with reasonable confidence, exclude it.

4. **Prefer trustworthy sources.** Prioritize established tech publications, official blogs, and reputable news outlets:
   - General tech: TechCrunch, The Verge, Ars Technica, Wired, ZDNet
   - Developer-focused: Hacker News, InfoQ, Publickey, Gihyo, Dev.to
   - AI-specific: The Batch, MIT Technology Review, arXiv (for papers)
   - Security: Krebs on Security, BleepingComputer, The Hacker News (thehackernews.com)
   - Cloud/Infra: Official cloud provider blogs, The New Stack
   - Japanese sources: ITmedia, GIGAZINE, Publickey, Impress Watch, @IT
   - Avoid: unverified blog posts, content farms, SEO-optimized aggregator sites.

5. **Select up to 5 items** for the category — cast a wide net at this stage; deduplication happens in Phase 2. Prioritize by impact, novelty, and breadth.

6. **Return results** in this exact format:
   ```
   - **[Title]**
     [URL]
     Published: [YYYY-MM-DD]
     [1-2 sentence overview in Japanese]
   ```

**Agent prompt template:**

```
You are collecting tech news for [CATEGORY] on [DATE] (JST).

Use WebSearch to find up to 5 significant news items in this category from that date.
Run 2-3 search queries with varied phrasing to get good coverage. Include the date in queries.

IMPORTANT — Date filtering:
- Only include articles published within 7 days before [DATE] (inclusive).
  For [DATE], the valid range is [DATE-7] to [DATE].
- You MUST determine and include the publication date for every article.
  Check the URL path (e.g., /2026/03/13/), search snippet, or article content.
- If you cannot determine the publication date, exclude the article.

Prefer trustworthy, established sources. Avoid content farms and unverified blogs.

For each item, provide:
- Title (in the language of the original article)
- URL
- Publication date (YYYY-MM-DD)
- 1-2 sentence overview in Japanese

Return EXACTLY this format for each item:
- **[Title]**
  [URL]
  Published: [YYYY-MM-DD]
  [1-2 sentence overview in Japanese]

If fewer than 5 noteworthy items exist within the date range, return only what you find.
Do not pad with irrelevant or out-of-range items.
```

### Phase 2: Topic Extraction and Consolidation

After all 6 agents return, consolidate their results into topics:

1. **Verify dates.** Before processing, double-check that all returned articles fall within the 1-week window. Discard any that don't.

2. **Identify topics.** Group articles that cover the same event, announcement, or story into a single topic. For example, if "Microsoft Patch Tuesday" appears from both BleepingComputer and The Hacker News, that's one topic with two articles.

3. **Assign tags.** Each topic gets one or more tags. A single topic can belong to multiple tags — for instance, an "AI chip announcement" might be tagged both AI and Other (hardware).

4. **Deduplicate.** Each topic appears only once in the output.

5. **Exclude already-collected topics.** Compare each candidate topic against the exclusion list from Phase 0. For each candidate, check both conditions:

   **URL check (mandatory, mechanical):** Use Grep to search the existing topic files for each candidate article URL. If any URL from a candidate topic already appears in any existing topic file, the topic is a duplicate. This is a string-match check — do not rely on memory, actually run Grep against `topics/` for each URL.

   **Headline check (semantic):** If URLs don't match, also check whether the candidate's headline describes the same event/announcement as an existing topic headline. Use semantic similarity — e.g., "OpenAI releases GPT-5" and "GPT-5が正式リリース" are the same story.

   Remove duplicates from the candidate list. A topic is only considered "new" if it covers a genuinely different development — not just the same story reworded or with minor additional details. The bar for keeping a "follow-up" should be high: a new official announcement, a materially different consequence, or a major escalation. Simply having a slightly different summary of the same event does not qualify.

6. **Prioritize and trim.** Select the top 10 topics overall, aiming for roughly 1-3 per category but not forcing equal distribution. Prioritize by:
   - Impact and significance to the tech community
   - Novelty (new releases/announcements over opinion pieces)
   - Breadth across categories (avoid filling the list with one dominant category)

7. **Order topics by significance.** Sort the final list by overall importance, not by category. The most impactful topics come first.

8. **Write a topic headline** — a concise Japanese description of what happened (not just the article title).

9. **Generate a slug** for each topic — a short, URL-friendly English identifier derived from the topic content. Use lowercase, hyphens only, no special characters, max ~5 words.

### Phase 3: Supplementary Article Search

For topics that have only 1 article, launch parallel search agents to find additional coverage. This helps readers see multiple perspectives and find the source they prefer. Focus on the top 3 single-article topics to keep cost and time reasonable.

**Agent prompt template for supplementary search:**

```
Search for additional articles about this topic published between [DATE-7] and [DATE]:

Topic: [TOPIC HEADLINE]
Known article: [EXISTING ARTICLE TITLE AND URL] (Published: [YYYY-MM-DD])

Use WebSearch with 1-2 queries. Find 1-2 additional articles from different, trustworthy sources covering the same story.

IMPORTANT: Only return articles published between [DATE-7] and [DATE].
Include the publication date for each article.

Return EXACTLY this format for each article found:
- [Title]
  [URL]
  Published: [YYYY-MM-DD]

If no additional trustworthy articles are found within the date range, return: NONE
```

## Output Format

Write each topic as an individual file under `./topics/[YYYY]/[MM]/[DD]/[SLUG].md`. Create the directories if they don't exist.

Each topic file uses this structure:

```
# [Topic headline in Japanese]
Tags: AI, Security

- [Article title] ([YYYY-MM-DD])
  [URL]
- [Article title] ([YYYY-MM-DD])
  [URL]

[1-2 sentence overview of the topic in Japanese]
```

**Example:** `./topics/2026/01/15/example-project-release.md`

```
# ExampleプロジェクトがバージョンX.Yをリリース、新機能Zを搭載
Tags: OSS, Programming Languages

- Example Project releases vX.Y with feature Z (2026-01-15)
  https://example.com/article1
- Example Project vX.Y: What's new and why it matters (2026-01-14)
  https://example.com/article2

ExampleプロジェクトがバージョンX.Yを正式リリース。主要な新機能として機能Zが追加され、処理速度の向上とAPIの改善が行われた。
```

**Format rules:**
- Each file contains exactly one topic.
- The h1 heading is the topic headline in Japanese.
- The `Tags:` line lists all tags the topic belongs to.
- Each article line includes the publication date in parentheses after the title.
- Article titles should be in the original language of the article.
- Topic headlines and overviews should be in Japanese.

## Important Notes

- Phase 1 searches MUST run in parallel via the Agent tool for efficiency.
- Phase 3 supplementary searches MUST also run in parallel.
- Do not fabricate news. If search results are sparse, report fewer topics rather than inventing content.
- This skill is for collection only. A separate summarization skill handles deeper analysis.
- After writing all files, report the output directory path and the list of generated files to the user.
