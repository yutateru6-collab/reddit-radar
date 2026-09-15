# Changelog

## 2026-09-16 — Initial ChatGPT-first design

### Added

- Project README
- Core Reddit Radar Skill
- Opportunity Score rubric
- Search/verification/reply workflow
- Standard output formats
- Anti-spam and safety rules
- Architecture decisions
- Existing OSS research
- Roadmap
- ChatGPT quickstart
- Canonical ChatGPT execution prompt
- Public project-profile rules
- Project template
- Zarigani English fiction profile
- Contributor / agent guidance

### Product direction change

The first concept considered a standalone Devvit + AI application.

That direction was deliberately replaced with a simpler Phase 1:

```text
GitHub rules + normal ChatGPT research + human posting
```

Reasons:

- no user-supplied OpenAI API key
- no separate API billing
- no Codex-only dependency
- no autonomous posting
- lower maintenance burden
- faster real-world validation

### Next validation

Run real Reddit Radar searches for:

1. English web fiction / Inkitt
2. English-learning products
3. New app ideas / pain-point discovery

Use those results to recalibrate scoring instead of adding infrastructure first.
