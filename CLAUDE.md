# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Tech Clip is a Hugo-based tech news blog that automatically collects, summarizes, and publishes daily tech news. The site uses the PaperMod theme (git submodule) and is deployed to GitHub Pages. Content is written in Japanese.

## Development Commands

```bash
# Local dev server
hugo server

# Build for production
hugo build --gc --minify

# Create new content
hugo new posts/2026/03/28/my-slug.md
```

Tool versions are managed by mise (see `mise.toml`): Hugo 0.159.1.

## Architecture

### Automated News Pipeline

The CI workflow (`.github/workflows/posts.yml`) runs daily at 02:00, 10:00, 18:00 JST and executes a 4-stage pipeline using Claude Code skills:

1. **Collect** (`/collect-news`) — Searches for tech news across 6 categories (AI, Security, Cloud, Programming, OSS, Other), deduplicates against the last 7 days, and saves topic files
2. **Summarize** (`/summarize-news`) — Reads full articles for each topic and writes a detailed Hugo post (runs in parallel per topic)
3. **Review** (`/review-post`) — Fact-checks each summary against source articles through iterative review cycles (runs in parallel per topic)
4. **Create PR** — Opens and auto-merges a PR with all new posts

### Content Structure

- `topics/<yyyy>/<mm>/<dd>/<slug>.md` — Raw collected topics (headline, tags, article URLs, brief overview)
- `content/posts/<yyyy>/<mm>/<dd>/<slug>.md` — Published Hugo posts with frontmatter (`date`, `title`, `description`, `tags`, `references`)

### Post Frontmatter

Posts use these frontmatter fields:
- `date`: Publication datetime as `"YYYY-MM-DDTHH:MM:SS+09:00"`
- `title`: Japanese article title
- `description`: One-sentence Japanese summary
- `tags`: Array of category tags (AI, Security, Cloud, Programming Languages, OSS, Other)
- `references`: Array of source article URLs (rendered as a "Sources" section via custom layout)

### Layout Customizations

The project overrides the PaperMod theme's `single.html` to add a references/sources section at the bottom of each post. Custom CSS for this section lives in `assets/css/extended/references.css`.
