# Ghost

## Governed Cross-Model Continuity and Dispatch

Ghost is a user-owned continuity and governed-dispatch product for supported LLM chat windows.

Its proposed V1 product wedge is intentionally simple on the outside:

- **READ** — manually or on an approved schedule.
- **SEND** — manually or autonomously when an approved trigger is satisfied.

Internally, continuity, interpretation, authority, orchestration, execution, evidence, and verification remain separate.

> **One human objective. Multiple separately governed AI work units. One continuity surface. Memory never becomes permission.**

## Current status

- **Repository state:** strategy and pre-canon product record.
- **Engineering build authorization:** **NONE**.
- **Founder instruction recorded:** document the proposed Ghost V1 direction and the Collaboration Protocol-based risk controls developed on 5 September 2026.
- **Decision status:** recommendations are recorded faithfully but are not silently promoted to final founder decisions unless explicitly marked as ratified.
- **CP status:** Ghost is a derivative/product system around frozen CP v1.0.1; this repository does not redefine frozen CP.

## Read in this order

1. [`docs/00_STATUS_AND_AUTHORITY.md`](docs/00_STATUS_AND_AUTHORITY.md)
2. [`docs/01_GHOST_V1_PRODUCT_AND_SCOPE.md`](docs/01_GHOST_V1_PRODUCT_AND_SCOPE.md)
3. [`docs/02_CP_GOVERNANCE_MAPPING.md`](docs/02_CP_GOVERNANCE_MAPPING.md)
4. [`docs/03_RUNTIME_AND_AUTOMATION.md`](docs/03_RUNTIME_AND_AUTOMATION.md)
5. [`docs/04_RISK_REGISTER.md`](docs/04_RISK_REGISTER.md)
6. [`docs/05_MEANING_LEDGER_AND_PROVENANCE.md`](docs/05_MEANING_LEDGER_AND_PROVENANCE.md)
7. [`docs/06_METRICS_AND_VALIDATION.md`](docs/06_METRICS_AND_VALIDATION.md)
8. [`docs/07_DECISION_REGISTER_AND_BACKLOG.md`](docs/07_DECISION_REGISTER_AND_BACKLOG.md)

## Governing product principles

1. **Memory is not authority.**
2. **A schedule is a wake-up condition, not permission to act.**
3. **One human objective compiles into separately governed target work units.**
4. **Every target window retains its own Context, Intent, Agent identity, permissions, evidence, and recovery path.**
5. **A target model's claim is reported evidence until independently verified where material.**
6. **The CP Guardian remains read-only and uses the frozen `Allow / Clarify / Refuse` vocabulary.**
7. **Distributed execution controls such as idempotency, replay protection, state-version checks, and compensation are Ghost engineering extensions, not silently attributed to frozen CP.**
8. **Ghost must fail closed for authority uncertainty and fail visibly for observation/execution uncertainty.**
9. **External tools execute; Ghost must not overstate control it cannot technically enforce.**
10. **History is corrected prospectively, never silently rewritten.**

## Collaboration Protocol source boundary

The source research archive is:

- [`mohamedyousalama-ctrl/collaboration-protocol`](https://github.com/mohamedyousalama-ctrl/collaboration-protocol)

Primary references used for this record:

- `docs/02_CANONICAL_CP_V1_0_1_SPEC.md`
- `docs/07_APPLIED_EXTENSIONS_AND_DERIVATIVES.md`
- `docs/08_CURRENT_RESEARCH_FRONTIER_AUTHORITY_CONTINUITY.md`
- `docs/10_CONTRADICTIONS_AND_OPEN_QUESTIONS.md`
- `docs/14_RESEARCH_DECISION_LOG.md`
- `archive/applied/01_PRODUCT_CONSTITUTION.md`
- `archive/applied/08_CP_GHOST_GOVERNANCE_AND_DECISION_PACKETS.md`
- the preserved Ghost strategy record `Ghost_Master_Strategy_Decisions_and_Backlog_2026-08-05_v2.1.md`

## Core V1 loop

```text
WAKE
  -> READ AUTHORIZED DELTAS
  -> RECORD SOURCE EVENTS
  -> RECONCILE MEANING
  -> FIND A VALID TRIGGER
  -> CHECK CURRENT CONTEXT / INTENT / AGENT / PERMISSIONS
  -> GUARDIAN: ALLOW / CLARIFY / REFUSE
  -> ISSUE ONE-SHOT DISPATCH PERMIT
  -> SEND
  -> VERIFY DELIVERY
  -> READ RESULT
  -> VERIFY MATERIAL COMPLETION
  -> UPDATE LEDGER
  -> SLEEP
```

## Important scope warning

This repository records a stronger Ghost V1 proposal that pulls **bounded LLM-window text dispatch** into V1. The preserved August 2026 strategy placed the first governed connector in V1.5. That roadmap change is recorded here as a **proposed founder revision**, not as a silent historical rewrite.
