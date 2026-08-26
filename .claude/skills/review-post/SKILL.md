---
name: review-post
description: "Review a single post file (summarize-news output) for factual accuracy against its source articles. Use this skill when the user wants to verify, review, or fact-check a specific news summary. Trigger when the user says things like 'review this post', 'fact-check this summary', 'verify this article', 'この記事をレビューして', 'この post を検証して', 'ファクトチェックして', or any request to check whether a specific summary accurately reflects its source articles. The user will specify which post file to review — if they don't, ask them."
---

# Review Post

Review a single post file against its source articles. The sole criterion is whether the summary faithfully reflects what the sources actually say. Review targets are the frontmatter `title` and `description` as well as the body text.

## Step 1: Identify the target file

Determine the post file from the user's request or the conversation, and read it. If the user hasn't specified one, ask.

## Steps 2-4: Review loop

Run **exactly 2 cycles** — no more, no less. Early termination is prohibited: cost, time, token usage, or a judgment that "the review has been thorough enough" are never valid reasons to skip the second cycle.

Each cycle's subagent receives NO information about previous cycles — no prior findings, no list of fixed text, no "focus on these areas". A reviewer that knows what was fixed anchors on those areas and misses problems elsewhere; independent passes are the whole point of iterating. The subagent prompt is identical every cycle; the only difference is the post file's current content.

### Step 2: Review subagent

Launch one Agent subagent per cycle to review the post against ALL sources in a single pass, so it can distinguish "the claim comes from source B, not source A" from "the claim is in no source at all". Using a subagent is what gives each cycle a fresh context with no memory of earlier findings.

```
You are a fact-checker reviewing a tech news summary against its source articles.

Post file: [PATH]

## Critical context about WebFetch

WebFetch returns AI-summarized content, NOT the full article text — information
that IS in the original article may be ABSENT from the WebFetch result. Results
also vary between fetches: the same URL fetched with a different prompt returns
a different subset of the article. "Not found in WebFetch output" does NOT mean
"not in the source article". If you treat WebFetch output as the complete
source, you WILL flag correct information as fabricated. Step 4 below exists
specifically to prevent this.

## Instructions

1. Read the post file. The `title`, `description`, and full body text are all
   review targets; take the source URLs from `references:`.

2. **Initial fetch** — WebFetch each source URL with a broad prompt such as
   "Extract all key facts, quotes, names, numbers, dates, and technical details
   from this article." Note any failure (403, paywall) and proceed with the rest.

3. **First-pass comparison** — check every claim, title and description
   included, against ALL fetched content: numbers, percentages, amounts, dates,
   version numbers; names of people, companies, products, technologies; specs
   and benchmark results; causal claims and characterizations; quotes and
   paraphrased statements; timeline and sequence of events. Classify each claim
   as Supported, Contradicted, or Not found.

4. **Targeted re-verification** — mandatory for every "not found" claim:
   a. Re-fetch the most relevant source with a prompt asking specifically about
      the claim (e.g. "Find any quotes by Dr. X in this article. Include the
      exact text of every quote attributed to Dr. X").
   b. If it still isn't found, try the other source URLs with targeted prompts.
   c. If every source URL failed to fetch, use WebSearch for the specific claim.
      If a credible secondary source confirms it, do NOT flag it.
   d. Then classify: **Actually present** (drop it), **Confirmed absent** (the
      re-fetch returned relevant content and the claim genuinely wasn't there,
      or the source gives different information), or **Still not found** (the
      re-fetch wasn't relevant enough to confirm or deny).

   Only "confirmed absent" claims may be flagged as fabrication. "Still not
   found" goes to the unverifiable list, or a finding scored 5-6.

5. **Findings** — a JSON array, genuine issues only:
   {
     "issue_type": "contradiction" | "fabrication",
     "location": "title" | "description" | "body",
     "quote_from_summary": "the problematic text",
     "source_evidence": "what the source actually says, quoted — or 'confirmed absent after targeted re-fetch for [query]'",
     "verification_method": "how you confirmed it, e.g. the targeted re-fetch prompt you used",
     "validity_score": <1-10>,
     "suggested_fix": "concrete replacement text"
   }

   Scoring rules:
   - Number/date/version directly contradicts source → 9+
   - Direct quote doesn't match the actual quote → 7+
   - Confirmed absent after targeted re-verification → 7-8
   - Not found but re-verification inconclusive → 5-6
   - Reasonable paraphrase without quotes, meaning preserved → 4 or lower

6. **Unverifiable claims** — only where the claim is unconfirmed by any
   accessible source, every relevant source URL failed to fetch, AND WebSearch
   found no credible secondary source:
   {"unverifiable_claim": "the claim text", "reason": "why it could not be verified"}

7. Return your response in exactly this format:

   POST: [filename]
   FETCH_FAILURES: [URLs that failed, or "none"]
   FINDINGS:
   ~~~json
   [array of findings, or empty array]
   ~~~
   UNVERIFIABLE:
   ~~~json
   [array of unverifiable claims, or empty array]
   ~~~

## Guiding principles

- **Precision over recall**: a false positive is MORE harmful than a false
  negative, and the parent agent independently re-verifies your findings. When
  unsure, score low or list the claim as unverifiable.
- Do NOT flag stylistic choices, omissions of minor details, or reasonable
  paraphrasing. DO flag invented statistics, wrong numbers, incorrect
  attributions, fabricated quotes, and claims contradicting the source.
- When sources are ambiguous, give the summary the benefit of the doubt.
- The most common mistake is treating "not in the WebFetch summary" as "not in
  the source article". Always do the targeted re-fetch before concluding
  fabrication.
```

### Step 3: Verify findings

Independently verify every finding scored **5 or higher** — subagent scoring is inconsistent, so the parent makes the final judgment. For each finding: locate the flagged text in the post, re-fetch the relevant source articles yourself (do not trust the subagent's account of them), and compare the finding, the fresh source content, and the post text. Verdict:

- **Confirmed** — valid; assign a final score, which may differ from the subagent's.
- **Overturned** — the post is accurate, or the issue is too minor to act on. Drop it.
- **Revised** — partially valid; adjust the scope, score, or suggested fix.

Every finding must reach a verdict — there is no "flagged for review" middle ground, since this runs without human intervention. For findings scored 5-6, invest extra effort — multiple WebFetch prompts, WebSearch corroboration, cross-referencing all source URLs — until the finding is promoted to 7+ or dismissed. Only if the evidence remains genuinely inconclusive (all sources paywalled, WebSearch empty) classify the claim as unverifiable rather than leaving it pending.

Findings **Confirmed at 7 or higher** proceed to Step 4.

### Step 4: Apply fixes

Edit the post file using `quote_from_summary` as `old_string` and the (possibly revised) `suggested_fix` as `new_string`. If the exact quote cannot be found — slight formatting differences, say — skip that fix and report it to the user.

Record how many fixes this cycle applied. After cycle 1, go back to Step 2. After cycle 2, stop.

## Step 5: Report to user

- Fixes applied per cycle, with before/after, verification reasoning, and the cycle that found each
- How many source articles were reviewed and how many could not be fetched
- Count of overturned findings, with 2-3 examples illustrating the false positives caught
- Claims unverifiable in every cycle — a claim resolved in either cycle is not unverifiable
- Whether the post passed review with no issues found

## Notes

- During Step 3, batch WebFetch calls for findings that share a source URL.
- The review covers factual accuracy only — not writing quality, style, structure, or completeness.
- Sources differing slightly on the same fact (e.g. rounding) is not an error, as long as the summary matches at least one source.
