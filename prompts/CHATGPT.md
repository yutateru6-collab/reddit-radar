# Canonical ChatGPT Instruction

This file is the compact execution instruction for Reddit Radar.

When the user asks to use Reddit Radar:

1. Read the current repository rules, especially `SKILL.md`, `docs/SCORING.md`, and `docs/SAFETY.md` when available.
2. Use current web research to find actual Reddit posts; do not rely on stale examples from this repository.
3. Expand the user's topic into problem, intent, direct, and adjacent search terms.
4. Open the actual Reddit thread when possible instead of rating search snippets only.
5. Check the subreddit rules when promotion or external links might be involved.
6. Score candidates independently using the six-category Opportunity Score.
7. Evaluate Promotion Risk separately.
8. Prefer recent, open conversations where the user can add value without promotion.
9. For every recommended thread, explain why it is relevant and what action is appropriate.
10. Draft a value-first reply. Add a soft-mention version only when context and rules support it.
11. Never invent the user's personal experience, metrics, readership, sales, testimonials, or product usage.
12. Do not automatically post or DM. Human approval remains mandatory.

## Default result count

Return 5 strong candidates when available.

Do not fill the list with weak results merely to reach five. If only two good opportunities exist, return two.

## Default freshness

For opportunity discovery, prioritize recent posts. Broaden the time window only if current results are sparse.

For market research, include older high-signal discussions when they help identify recurring problems, but distinguish them from current opportunities.

## Default language

Analysis: Japanese.

Reddit reply drafts: language of the target thread, normally English for English-language threads.

## Default output

For each candidate:

```text
Score /100 — rating
subreddit — title
Freshness/status
Japanese summary
What the poster actually wants
Why it matches
Promotion Risk
Recommended action
Value-first reply
Soft mention reply (only if justified)
Source/reference
```

## Challenge step

Before finalizing each 80+ candidate, actively look for one reason it may be a bad opportunity.

If that counterargument is strong, lower the score or change the action to `REPLY WITHOUT PROMOTION`, `WATCH`, or `SKIP`.

## Market-research mode

Do not just list threads. Synthesize:

- recurring pain points
- alternatives people currently use
- complaints
- user language
- objections
- evidence against the product idea
- opportunities

Always note that Reddit users are not automatically representative of the whole market.
