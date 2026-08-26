---
name: review-post
description: Fact-checks one post file against its source articles and applies fixes for confirmed errors.
argument-hint: "[post-file]"
disable-model-invocation: true
---

# Review Post

Fact-check a single post against its source articles and fix what is wrong. The sole criterion is whether the post faithfully reflects what the sources say — not writing quality, style, structure, or completeness. The frontmatter `title` and `description` are in scope alongside the body.

## Review cycles

Run the Step 2-4 loop **exactly twice**. Never skip the second cycle — not for cost, time, token usage, or a sense that the review has been thorough enough.

Keep the cycles independent. Launch a fresh `fact-checker` each cycle with the same instructions and tell it nothing about earlier cycles — no prior findings, no list of what was fixed, no "focus on these areas". Judge its findings in Step 3 on evidence you gather in that cycle, not on verdicts you reached in the previous one. A reviewer that knows what was already fixed anchors there and misses everything else; independent passes are the whole point of iterating.

## Step 1: Identify the target

Post file: $ARGUMENTS

If none was given, determine it from the conversation, and ask if that is ambiguous. Read it.

## Step 2: Review

Launch one `fact-checker` agent and pass it the post file path. Give it the whole post in one pass so it can tell "this claim comes from source B, not source A" apart from "this claim is in no source at all".

It returns three things: findings, each marked `certain` or `suspect` and carrying a `quote_from_post` and a `suggested_fix`; claims it could not verify against any source; and the source URLs it failed to fetch. Only the findings go through Step 3 — carry the unverifiable claims and the fetch failures straight to Step 5 without editing anything for them.

## Step 3: Verify every finding

The agent's findings are candidates, not conclusions — you make the final call, because the dominant failure mode here is a false accusation of fabrication. Verify each one yourself: locate the flagged text in the post, re-fetch the relevant sources rather than trusting the agent's account of them, and compare the finding, the fresh source content, and the post text. Batch WebFetch calls for findings that share a source URL.

Reach a verdict on every finding. This runs unattended, so there is no "needs a human look" middle ground:

- **Confirmed** — the source contradicts the post, or the claim is genuinely absent. Fix it.
- **Revised** — partly valid. Narrow the scope or adjust the fix, then fix it.
- **Overturned** — the post is accurate, or the issue is too minor to act on. Drop it.
- **Inconclusive** — every relevant source is inaccessible and WebSearch turns up nothing. Report it; do not edit.

Spend real effort on `suspect` findings before settling: several WebFetch prompts, WebSearch corroboration, cross-referencing the other sources. Only call a finding inconclusive once the evidence is genuinely exhausted.

## Step 4: Apply fixes

Edit the post with `quote_from_post` as `old_string` and the verified `suggested_fix` as `new_string`. If the quote does not match the file exactly — a formatting difference, say — skip that fix and report it.

After cycle 1, return to Step 2. After cycle 2, go to Step 5.

## Step 5: Report

- Each fix applied, with before/after, the evidence behind it, and the cycle that found it
- Findings overturned, with an example or two of the false positives caught
- Claims the fact-checker could not verify, findings left inconclusive, and source articles that could not be fetched — counting only what stayed unresolved in both cycles
- Or that the post passed both cycles with no issues found
