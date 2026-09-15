# Architecture Decisions

This file records product decisions so the project does not accidentally drift back into unnecessary complexity.

## Decision 001 — ChatGPT-first, not standalone SaaS

**Status:** Accepted

### Initial idea

A standalone Reddit Radar web app was considered with:

- Reddit/Devvit search
- AI scoring
- Japanese summaries
- reply generation
- dashboards
- saved opportunities

### Why this was not chosen for Phase 1

The user's actual workflow is to use normal ChatGPT directly.

A standalone app would add:

- API-key management
- separate billing risk
- deployment
- authentication
- maintenance
- another UI to open

Those costs are not justified before validating whether the Radar workflow itself is useful.

### Current solution

```text
GitHub = rules / project profiles / scoring
ChatGPT = current Reddit research + reasoning + drafts
Human = final posting decision
```

---

## Decision 002 — No user-supplied OpenAI API key

**Status:** Accepted

The Phase 1 workflow must not require the user to create or fund an OpenAI API account.

Normal ChatGPT usage is the intended interface.

If a future standalone application is proposed, separate API billing must be explicitly discussed before implementation.

---

## Decision 003 — Human approval is mandatory

**Status:** Accepted

Reddit Radar will not optimize for autonomous posting.

Reasons:

- community norms vary substantially
- subreddit rules can change
- a technically relevant post may still be socially inappropriate for promotion
- AI-generated personal claims can be wrong
- human judgment is useful before publishing under a real account

---

## Decision 004 — Opportunity Score and Promotion Risk are separate

**Status:** Accepted

A thread can be highly relevant but still be a bad place to promote.

Example:

- User has exactly the expertise the poster needs: high Opportunity Score
- subreddit bans self-promotion: HIGH Promotion Risk

Therefore the system must never collapse both concepts into one score.

---

## Decision 005 — Reddit is initially a research source, not just a traffic source

**Status:** Accepted

The project should create value even when no link is ever posted.

Useful outputs include:

- recurring pain points
- vocabulary users use to describe problems
- existing alternatives
- objections
- product ideas
- content ideas
- reader expectations

---

## Decision 006 — Existing OSS is reference material, not the foundation yet

**Status:** Accepted

Projects such as RedSignal, Harken and RedoraAI demonstrate useful patterns, but adopting them now would reintroduce infrastructure/API complexity.

Revisit only if manual ChatGPT-based use proves that persistent tracking is needed.

---

## Decision 007 — Future Devvit work must be optional and isolated

**Status:** Accepted

If Reddit-native functionality becomes useful later, implement it separately under a dedicated directory or branch.

Do not make Devvit a prerequisite for the core ChatGPT workflow.
