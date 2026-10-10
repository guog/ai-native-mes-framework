# Architecture Documentation Agent Instructions

This repository contains **architecture design documents only**; do not implement MES code or create deployment scripts unless expressly authorized in a separate request.

## Source of truth

1. User-accepted ADR-001 to ADR-130 are immutable first-version decisions. `adr/baseline-v1.md` is their normalized summary, **not a verbatim transcript**. If a summary conflicts with the confirmed conversation, the user's original confirmation takes precedence.
2. `docs/architecture.md` is the index of chapters 1–16. `contracts/` is a draft normative mapping, subject to architecture review.
3. `verification/` describes **tests to run in the future**. There are no executed tests or certified database combinations here.

## Safe editing rules

- Preserve all ADR numbering and accepted meaning; never silently reclassify or rewrite an ADR.
- Every proposed requirement must cite related ADRs or be explicitly marked `Draft` and subject to review.
- Do not claim Kysely + dmdb compatibility, HA zero-loss, GraphQL hot reload, security or performance testing is already proven.
- Keep Markdown prose readable, favor hierarchical bullet lists over wide tables.
- Avoid confidential production data or secrets; do not select new framework defaults as facts.
- When writing implementation tasks, include acceptance tests and key failure scenarios, without generating implementation code in this documentation-only phase.
