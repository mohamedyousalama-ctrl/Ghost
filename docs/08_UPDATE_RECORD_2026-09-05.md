# 08 — Update Record: Ghost V1 Read / Send Direction

**Date:** 5 September 2026  
**Change class:** product strategy and governance documentation  
**Implementation effect:** none  
**Build authorization:** none

## 1. Trigger for this update

The founder directed that Ghost V1 should center on:

- reading selected LLM chat windows;
- sending messages into selected LLM chat windows;
- performing both functions manually;
- performing both functions autonomously on a recurring schedule beginning at five minutes;
- using one Ghost continuity window to preserve meaning across models;
- ensuring that memory never becomes authority.

The founder then requested a full review against the Collaboration Protocol research archive and asked that the resulting improved V1 model, risks, mitigations, decisions, and backlog be recorded in this repository.

## 2. Sources reviewed

The review used the authority hierarchy in `mohamedyousalama-ctrl/collaboration-protocol`, including:

- `START_HERE.md`
- `docs/00_ARCHIVE_GUIDE.md`
- `docs/01_MASTER_RESEARCH_RECORD.md`
- `docs/02_CANONICAL_CP_V1_0_1_SPEC.md`
- `docs/03_TERMINOLOGY_AND_CONCEPT_INDEX.md`
- `docs/05_VERSION_AND_LINEAGE_MAP.md`
- `docs/06_IMPLEMENTATION_AND_EMPIRICAL_EVIDENCE.md`
- `docs/07_APPLIED_EXTENSIONS_AND_DERIVATIVES.md`
- `docs/08_CURRENT_RESEARCH_FRONTIER_AUTHORITY_CONTINUITY.md`
- `docs/10_CONTRADICTIONS_AND_OPEN_QUESTIONS.md`
- `docs/14_RESEARCH_DECISION_LOG.md`
- `archive/applied/01_PRODUCT_CONSTITUTION.md`
- `archive/applied/08_CP_GHOST_GOVERNANCE_AND_DECISION_PACKETS.md`
- `archive/applied/Ghost_Artifact_Authority_Index_2026-08-05_v1.0.md`
- the preserved split-source Ghost master strategy v2.1.

## 3. Main corrections to the initial V1 proposal

### 3.1 Autopilot is not a third function

Ghost V1 has two primitives:

- `READ`
- `SEND`

Each has manual and autonomous modes.

### 3.2 Five minutes is a wake cadence

The timer starts an observation/reconciliation cycle. It never creates permission or requires a Send.

### 3.3 One objective does not become one shared CP Intent

A Ghost-level Human Objective compiles into separate target Work Units. Each has its own:

- Context;
- Intent;
- Agent;
- permissions;
- evidence;
- recovery path.

### 3.4 Reading is permissioned and security-relevant

Auto Read requires an Observation Permit and incremental cursor. Read failures remain visible and do not become “no change.”

### 3.5 Sending text may create downstream consequences

Target windows are classified as advisory, sandboxed acting, externally gated acting, or ungated acting. V1 unattended Send is prohibited for ungated consequential targets.

### 3.6 Guardian vocabulary remains frozen

The CP Guardian remains read-only and returns exactly:

- `Allow`
- `Clarify`
- `Refuse`

Ghost runtime dispositions are separate product terms.

### 3.7 CP does not solve all distributed execution problems

Ghost engineering must separately implement and test:

- idempotency;
- replay protection;
- delivery uncertainty;
- state/version checks;
- concurrency;
- partial execution recovery;
- connector drift;
- loop and budget controls.

### 3.8 Total recall is not the default retention policy

The architecture separates:

- Raw Event Archive;
- Meaning Ledger;
- optional explicit Forensic Archive.

Selected, sourced, correctable, revocable retention remains the default.

## 4. New proposed product boundary

A new proposed founder decision, FD-11, is recorded:

> Ghost V1 combines cross-model continuity with bounded LLM-window text dispatch, while arbitrary external execution remains outside V1.

This is a prospective roadmap change. The historical August 2026 strategy remains preserved.

## 5. New documentation created

- `README.md`
- `docs/00_STATUS_AND_AUTHORITY.md`
- `docs/01_GHOST_V1_PRODUCT_AND_SCOPE.md`
- `docs/02_CP_GOVERNANCE_MAPPING.md`
- `docs/03_RUNTIME_AND_AUTOMATION.md`
- `docs/04_RISK_REGISTER.md`
- `docs/05_MEANING_LEDGER_AND_PROVENANCE.md`
- `docs/06_METRICS_AND_VALIDATION.md`
- `docs/07_DECISION_REGISTER_AND_BACKLOG.md`
- this update record.

## 6. Current ratification state

### Founder direction already recorded

- READ and SEND are the two main V1 functions.
- both have manual and autonomous modes.
- minimum autonomous cadence begins at five minutes.
- one Ghost continuity surface coordinates selected LLM windows.
- memory is not authority.

### Still awaiting explicit founder ratification

- proposed FD-11 version boundary;
- GD-01 through GD-04 core product decisions;
- GD-05 through GD-15 derived architecture decisions;
- exact first buyer, costly event, and provider/window pair;
- product ontology;
- local retention/sync/recovery posture;
- first Auto Send grammar and target classes;
- build authorization.

## 7. No hidden execution

No code, connector, model window, account, schedule, or autonomous action was created by this documentation update.
