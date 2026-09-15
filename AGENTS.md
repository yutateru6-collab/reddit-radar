# AGENTS.md

This repository is a **ChatGPT-first Reddit research and reply-assistance knowledge base**.

## Core product decision

Do not turn this repository into an API-dependent autonomous marketing bot unless the user explicitly changes the product direction.

Current architecture:

```text
GitHub = canonical rules and scoring
ChatGPT = search, analysis, drafting
Human = final judgment and posting
```

## Non-negotiable defaults

- No OpenAI API key requirement.
- No paid API dependency by default.
- No automatic Reddit posting.
- No automatic DMs.
- No account rotation.
- No ban-evasion features.
- No fake personal experiences in generated replies.
- Human review remains mandatory.

## When changing scoring

Read:

- `SKILL.md`
- `docs/SCORING.md`
- `docs/WORKFLOW.md`
- `docs/SAFETY.md`

Any scoring change should explain:

1. Which failure mode it addresses.
2. Why the old weighting was insufficient.
3. What real Reddit examples motivated the change.
4. Whether it increases false positives or false negatives.

Do not optimize scoring merely to produce more 90+ results.

## When adding integrations

Before adding an external service, answer:

- Can normal ChatGPT already perform the task?
- Does this require another API key?
- Does it create separate billing?
- Does it increase spam risk?
- Does it create user-account security risk?
- Is the maintenance burden justified by actual usage data?

If the answer is unclear, keep the ChatGPT-first workflow.

## Reddit research quality

Never evaluate a candidate using only a search snippet when the actual thread can be opened.

Check where possible:

- title
- body
- date
- subreddit
- comments
- thread status
- community rules
- self-promotion rules

Unverified facts must be labeled as unverified.

## Writing style for Reddit replies

Replies should:

- answer the actual question first
- sound like a normal person
- be concise unless detail is useful
- avoid marketing language
- avoid exaggerated praise
- avoid unnecessary calls to action
- mention a product/project only when context makes it natural

## Public repository caution

This repository is public. Do not commit:

- API keys
- passwords
- OAuth tokens
- Reddit cookies
- private student/customer information
- unpublished sensitive personal data
- credentials of any kind

## Optional future Devvit implementation

If a Devvit implementation is later added, keep it isolated under a dedicated directory or branch and do not silently replace the ChatGPT-first workflow.
