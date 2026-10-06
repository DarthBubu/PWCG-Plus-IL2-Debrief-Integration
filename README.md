# PWCG+ ↔ IL-2 Campaign Tracker Debrief Integration

Public interoperability and validation workspace for integrating **PWCG+** with the factual debrief analyser supplied by Alexander Bleiholder (Arrow_1974), creator of **IL-2 Campaign Tracker**.

## Purpose

The intended user flow is:

```
PWCG+ Journal
  → Generate Story
  → exact PWCG mission log
  → il2_debrief.exe
  → factual schema-v1 JSON
  → PWCG+ reconciliation + compact fact payload
  → story provider
  → guardrail validation
  → existing editable PWCG Journal narrative
```

The central design rule is simple: **the debrief analyser is factual authority for logged combat events; PWCG+ remains authority for PWCG campaign context and the Journal.** Conflicts are resolved before any story model sees the facts.

This repository is **not** a fork or copy of the Campaign Tracker parser and is **not** the PWCG+ production source tree. It contains the shared integration contract, evidence, compatibility matrix, test cases and cross-project findings.

## Ownership boundary

- **IL-2 Campaign Tracker / il2_debrief**: raw IL-2 log parsing and factual debrief JSON.
- **PWCG+**: campaign identity/context, mission objective/briefing, PWCG pilot/squadron data, final campaign casualty adjudication, Journal UX and story generation.
- **This repository**: interoperability contract, reproducible evidence and compatibility validation.

## Current status — 7 Oct 2026

- Permission from Arrow to use and bundle the supplied executables: confirmed.
- Headless CLI contract: confirmed.
- Initial supported schema: **schema_version 1 only**.
- PWCG+ source architecture/Journaling path: audited.
- Provider-independent Java foundation: staged in PWCG+.
- Real PWCG log compatibility corpus: **pending**.
- Journal Generate Story UI: **not yet enabled**.
- Story/LLM provider: **not yet selected**.
- Release status: **not runtime-proven; do not describe as released**.

Start with [FOR_ARROW.md](FOR_ARROW.md) for the concise collaboration view and [docs/INTEGRATION_CONTRACT.md](docs/INTEGRATION_CONTRACT.md) for the frozen technical boundary.

## Safety / fail-soft rule

This is an optional enhancement. Failure or absence of the analyser or story provider must never prevent normal PWCG AAR completion, campaign persistence, mission generation or ordinary Journal use.

## Licensing

No Campaign Tracker parser source is copied here. Executable redistribution, when performed by PWCG+, must preserve the licences/notices required by the upstream author. See [docs/LICENSING_AND_PACKAGING.md](docs/LICENSING_AND_PACKAGING.md).

No repository-wide software licence has been assigned yet because this workspace contains interoperability documentation/evidence rather than a standalone software distribution.
