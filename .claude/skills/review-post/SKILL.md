---
name: review-post
description: "Review a single post file (summarize-news output) for factual accuracy against its source articles. Use this skill when the user wants to verify, review, or fact-check a specific news summary. Trigger when the user says things like 'review this post', 'fact-check this summary', 'verify this article', 'この記事をレビューして', 'この post を検証して', 'ファクトチェックして', or any request to check whether a specific summary accurately reflects its source articles. The user will specify which post file to review — if they don't, ask them."
allowed-tools: Agent, WebFetch, WebSearch, Read, Glob, Write, Edit, Bash
---

# Review Post

Review a single post file against its source articles to verify factual accuracy. The sole review criterion is whether the summary content faithfully reflects what the source articles actually say — flag any discrepancies, misrepresentations, or fabricated information.

**Review targets**: All text in the post file — frontmatter fields (`title`, `description`) AND the body text. Verify that the title and description do not contain named entities, events, or terms that are absent from the source articles.

## Process

### Step 1: Identify Target File

Determine the target post file from the user's request or conversation context. Read the file to confirm it exists and has the expected frontmatter structure (`title`, `description`, `references:` URL list).

If the user hasn't specified a file, ask them.

### Step 2–4: Iterative Review Loop

Steps 2, 3, and 4 run inside an iteration loop. Each iteration is a complete, independent review cycle.

**Convergence** requires zero confirmed fixes (score >= 7) for **two consecutive cycles**. A single zero-fix cycle is not enough — WebFetch results vary between fetches, so a second clean pass is needed to confirm convergence.

**Termination conditions** (whichever comes first):
- **Convergence**: Two consecutive cycles with zero confirmed fixes.
- **Max iterations**: 5 cycles.

**Early termination is strictly prohibited.** Do not stop the loop before one of the above conditions is met. Cost, time, token usage, or a subjective judgment that "the review has been thorough enough" are never valid reasons to skip remaining cycles. This is non-negotiable — the convergence mechanism exists precisely because a single clean pass is insufficient to guarantee accuracy.

**Cycle independence is absolute**: Each cycle's review subagent receives NO information about previous cycles — no prior findings, no list of previously fixed text, no "focus on these areas." Every cycle is a fresh, unbiased review of the post file in its current state (which may include fixes applied by earlier cycles). The parent agent tracks cycle metadata (fix counts, convergence status) purely for loop control and reporting — this metadata is never passed to the subagent.

The reason this matters: if the reviewer knows what was fixed last time, it will unconsciously anchor on those areas and miss problems elsewhere. Independent passes are the whole point of iterating.

#### Step 2: Review (One Subagent per Cycle)

Launch a single Agent subagent to perform a complete review of the post against ALL source articles. The subagent handles source fetching, cross-referencing, and finding generation in one pass. This design ensures the reviewer has full context across all sources — it can distinguish "claim comes from source B, not source A" from "claim is in no source at all."

Using a subagent (rather than reviewing inline) is essential for cycle independence: each cycle gets a fresh context window with no memory of previous findings or fixes.

**Agent prompt template:**

```
You are a fact-checker reviewing a tech news summary against its source articles.

Post file: [PATH]

## Critical context about WebFetch

WebFetch returns AI-summarized content, NOT the full article text. This means
information that IS in the original article may be ABSENT from the WebFetch
result. "Not found in WebFetch output" does NOT mean "not in the source article."

This distinction is the single most important thing in this entire prompt.
If you treat WebFetch output as the complete source, you WILL flag correct
information as fabricated. The targeted re-verification step (step 4) exists
specifically to prevent this.

Additionally, WebFetch results vary between fetches — the same URL fetched
twice with different prompts may return different subsets of the article's
content. A claim that is absent from one fetch may appear in another. This
is why targeted re-verification (step 4) exists: a single broad fetch that
doesn't mention a claim is weak evidence of absence. Only after a targeted
re-fetch specifically asking about the claim can you begin to consider it
potentially absent from the source.

## Instructions

1. Use the Read tool to read the post file at the path above.
   Extract the `title`, `description`, and `references:` URLs from the frontmatter,
   and the full body text. ALL of these are review targets.

2. **Initial source fetch** — Use WebFetch to retrieve each source article URL
   with a broad prompt like "Extract all key facts, quotes, names, numbers,
   dates, and technical details from this article."
   If a fetch fails (403, paywall, etc.), note it and proceed with successfully
   fetched articles.

3. **First-pass comparison** — Compare every claim in the summary (including
   title and description) against ALL fetched source content:
   - Numbers, percentages, dollar amounts, dates, version numbers
   - Names of people, companies, products, technologies, and specific terms
   - Technical specifications and benchmark results
   - Causal claims and characterizations
   - Quotes or paraphrased statements
   - Timeline and sequence of events

   Classify each claim as:
   - **Supported**: Clearly confirmed by at least one source
   - **Contradicted**: Directly conflicts with what a source says
   - **Not found**: Not present in any WebFetch output (but remember — this
     does NOT mean it's absent from the original articles)

4. **Targeted re-verification** — This step is mandatory for every claim
   classified as "not found" in step 3. For each such claim:

   a. Re-fetch the most relevant source article(s) with a TARGETED prompt that
      specifically asks about the claim in question. For example, if the summary
      attributes a quote to a person named Dr. X, re-fetch with: "Find any
      quotes by Dr. X in this article. Include the exact text of every quote
      attributed to Dr. X."

   b. If the targeted re-fetch still does not find the claim, try other source
      URLs with targeted prompts.

   c. If ALL listed source URLs returned 403/paywall in step 2, use WebSearch
      to search for the specific claim (e.g., search for key phrases or named
      entities from the claim). If a credible secondary source confirms the
      claim, do NOT flag it as fabrication.

   d. After re-verification, classify the claim as:
      - **Confirmed absent**: The targeted re-fetch returned relevant content
        about the topic but the specific claim was genuinely not there, OR
        the source directly provides different information
      - **Still not found**: The targeted re-fetch did not return content
        relevant enough to confirm or deny the claim
      - **Actually present**: The targeted re-fetch found the information
        (remove from findings)

   Only claims classified as "confirmed absent" should be flagged as findings.
   Claims that are "still not found" should go in the unverifiable list if
   the uncertainty is high, or be flagged with a lower validity score (5-6).

5. **Generate findings** — Report as a JSON array. Only include genuine issues.

   For contradictions (source says X, summary says Y):
   {
     "issue_type": "contradiction",
     "location": "title", "description", or "body",
     "quote_from_summary": "the problematic text",
     "source_evidence": "what the source actually says (quote the source)",
     "verification_method": "how you confirmed this — e.g., 'initial fetch of [URL]' or 'targeted re-fetch asking about X'",
     "validity_score": <1-10>,
     "suggested_fix": "concrete replacement text"
   }

   For fabrications (claim confirmed absent from all sources):
   {
     "issue_type": "fabrication",
     "location": "title", "description", or "body",
     "quote_from_summary": "the problematic text",
     "source_evidence": "what the targeted re-fetch returned instead, or 'confirmed absent after targeted re-fetch for [specific query]'",
     "verification_method": "describe the targeted re-fetch prompt you used",
     "validity_score": <1-10>,
     "suggested_fix": "concrete replacement text"
   }

   Scoring rules:
   - Number/date/version directly contradicts source → score 9+
   - Direct quote (in quotation marks) doesn't match actual quote → score 7+
   - Claim confirmed absent after targeted re-verification → score 7-8
   - Claim not found but re-verification was inconclusive → score 5-6
   - Reasonable paraphrase without quotes, meaning preserved → score 4 or lower

6. **List unverifiable claims** separately — claims where ALL of the following
   are true: (a) not confirmed by any accessible source, (b) all relevant
   source URLs failed to fetch, AND (c) WebSearch did not find a credible
   secondary source.
   {
     "unverifiable_claim": "the claim text",
     "reason": "why it could not be verified"
   }

7. Return your response in this exact format:

   POST: [filename]
   FETCH_FAILURES: [list of URLs that failed, or "none"]
   FINDINGS:
   ~~~json
   [array of findings, or empty array if no issues]
   ~~~
   UNVERIFIABLE:
   ~~~json
   [array of unverifiable claims, or empty array]
   ~~~

## Guiding principles

- **Precision over recall**: A false positive (flagging correct information as
  wrong) is MORE harmful than a false negative (missing an actual error). The
  parent agent will independently re-verify your findings, so err on the side
  of caution. If you're unsure, use a lower score or list as unverifiable.
- Do NOT flag stylistic choices, omissions of minor details, or reasonable
  paraphrasing.
- DO flag invented statistics, wrong numbers, incorrect attributions, fabricated
  quotes, or claims that contradict the source material.
- When sources are ambiguous, give the summary the benefit of the doubt.
- The most common mistake is treating "not in WebFetch summary" as "not in
  source article." Always do the targeted re-fetch before concluding fabrication.
```

#### Step 3: Verify Findings (Parent-Level Re-evaluation)

After the review subagent completes, the parent agent performs an independent verification of every finding with a validity score of **5 or higher**. This step exists because subagent scoring can be inconsistent — the parent re-reads the evidence and makes the final judgment.

**Every finding must reach a definitive verdict — there is no "flagged for review" middle ground.** The parent must investigate thoroughly enough to either confirm (and auto-fix) or dismiss each finding. This is essential for full automation without human intervention.

For each finding (score >= 5):

1. **Read the post file** to locate the exact text flagged by the subagent.
2. **Fetch the relevant source article(s)** using WebFetch to independently verify the subagent's claim. Do not trust the subagent's summary of the source — re-fetch it.
3. **Three-way comparison**: Compare the following three elements:
   - The **subagent's finding** (issue description, source evidence, suggested fix)
   - The **actual source article content** (freshly fetched)
   - The **post text** being reviewed
4. **Render a final verdict** for each finding:
   - **Confirmed**: The subagent's finding is valid. Assign a final score (may differ from the subagent's score).
   - **Overturned**: The subagent was wrong — the post is actually accurate, or the issue is too minor to act on. Drop the finding.
   - **Revised**: The finding is partially valid but the scope, score, or suggested fix needs adjustment.

**For findings originally scored 5-6 by the subagent**, the parent must invest extra effort to resolve the ambiguity. Use multiple WebFetch calls with different prompts, try WebSearch for corroboration, and cross-reference across all source URLs. The goal is to either:
- **Promote to score 7+** if deeper investigation reveals the issue is genuine → proceed to auto-fix
- **Dismiss** if deeper investigation confirms the post is accurate or the issue is too minor → drop the finding

Do not leave any finding in a 5-6 limbo state. If, after exhaustive investigation, the evidence remains truly inconclusive (e.g., all sources are paywalled and WebSearch yields nothing), classify the claim as **unverifiable** rather than leaving it as a pending finding.

Only findings that are **Confirmed** with a final score of **7 or higher** proceed to Step 4.

#### Step 4: Apply Fixes

For each confirmed finding with final score >= 7:

1. Use the Edit tool to apply the fix to the post file:
   - Use the `quote_from_summary` as the `old_string` to locate the text
   - Use the `suggested_fix` (potentially revised during verification) as the `new_string`
   - If the exact quote cannot be found (e.g., due to slight formatting differences), skip the fix and report it to the user

After applying fixes, record how many fixes were applied in this cycle. Then update convergence status:

- If this cycle applied **zero fixes** AND the previous cycle also applied **zero fixes** → **converged** (stop). Cycle 1 can never converge because there is no previous cycle — this ensures at least two independent passes.
- If this is cycle **5** → **stop** (max iterations reached).
- Otherwise → **go back to Step 2** for the next cycle. The next cycle's subagent receives the same prompt as always, with absolutely no knowledge of what happened in previous cycles.

#### End of Iteration Loop

### Step 5: Report to User

Report with:
- **Iteration summary**: How many cycles ran, why the loop terminated (convergence or max iterations), and how many fixes were applied per cycle
- Number of source articles reviewed and how many could not be fetched
- **Applied fixes** (final score >= 7): Issues that were automatically corrected, showing the before/after, verification reasoning, and which cycle found them
- **Overturned findings**: Total count of findings that the subagent flagged but the parent dismissed during verification, with 2-3 representative examples to illustrate the types of false positives caught
- **Unverifiable claims**: Claims that could not be verified in ANY cycle across the entire review. If a claim was unverifiable in one cycle but successfully verified (confirmed or denied) in another cycle, it is not unverifiable — use the cycle where verification succeeded
- Whether the post passed review with no issues found

## Important Notes

- The parent verification step (Step 3) is sequential by nature — each finding needs independent source re-fetching and comparison. To manage efficiency, batch WebFetch calls for findings that share the same source URL.
- Some source articles may be behind paywalls or block automated access. When a source cannot be fetched, list the affected claims as "unverifiable" rather than silently skipping them.
- The review focuses exclusively on factual accuracy against sources. Do not review writing quality, style, structure, or completeness.
- When multiple sources cover the same fact differently (e.g., slightly different numbers due to rounding), this is not an error in the summary as long as the summary's version matches at least one source.
- **Cycle independence**: Never pass previous cycle results, findings, or fix history to the subagent. The subagent prompt must be identical across cycles — the only difference is the current content of the post file (which may have been modified by earlier cycles).
- **Subagent prompt integrity**: When launching the subagent in later cycles, you may shorten the prompt for efficiency, but the following elements must NEVER be omitted: (1) the WebFetch variability warning, (2) the targeted re-verification step (step 4 in the template), and (3) the scoring rules. These are the core safeguards against false positives. Omitting the targeted re-verification step in particular leads to the subagent treating "not found in initial fetch" as "fabricated," which dramatically increases false positive rates.
