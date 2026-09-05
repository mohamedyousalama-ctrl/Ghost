# 07 — Decision Register and Backlog

**Record date:** 5 September 2026  
**Status:** proposed founder revision and pre-build backlog  
**Build authorization:** none

## 1. Decision-state legend

| State | Meaning |
|---|---|
| **FOUNDER DIRECTION** | Explicitly stated by Mohamed; implementation details may remain open |
| **PROPOSED FOR RATIFICATION** | Recommended decision requiring explicit founder approval |
| **LOCKED** | Explicitly ratified by the founder in a later record |
| **OPEN** | Requires design/evidence/founder judgment |
| **BLOCKED** | Cannot proceed until predecessor decision/evidence closes |
| **DEFERRED** | Intentionally outside the immediate V1 path |
| **REJECTED/SUPERSEDED** | Preserved historically but no longer governing |

## 2. Founder direction recorded from 5 September 2026

### GFD-2026-09-05-01 — Two primary V1 functions

**State:** FOUNDER DIRECTION

Ghost V1 should have two main functions:

1. `READ`
2. `SEND`

Both should be usable manually and autonomously.

### GFD-2026-09-05-02 — Minimum autonomous interval

**State:** FOUNDER DIRECTION

Autonomous Read/Send operation begins at a minimum interval of five minutes, with longer intervals available.

### GFD-2026-09-05-03 — One Ghost continuity window

**State:** FOUNDER DIRECTION

One Ghost/Continuity window records and remembers relevant work across multiple LLM chat windows and dispatches governed prompts into target windows.

### GFD-2026-09-05-04 — Memory is not authority

**State:** FOUNDER DIRECTION / EXISTING CONSTITUTIONAL LAW

Ghost may remember broadly, but remembrance never becomes permission to act.

## 3. Proposed FD-11 — Ghost V1 commercial wedge

**State:** PROPOSED FOR RATIFICATION

> **Ghost V1 will combine cross-model continuity with bounded LLM-window text dispatch. It pulls a narrow, explicitly constrained action path forward from the former V1.5, but does not pull arbitrary external execution into V1.**

### Rationale

A continuity-only V1 risks feeling passive. A complete useful product loop is:

```text
READ
  -> UNDERSTAND / RECONCILE
  -> SEND
  -> READ RESULT
  -> CONTINUE
```

The action boundary remains narrow:

- target is a supported LLM chat window;
- the V1 effect is a governed text dispatch;
- unattended Send is limited to advisory or safely sandboxed targets;
- consequential downstream execution remains manual-only or requires independently enforced controls.

### Historical consequence

The August 2026 strategy placed the first governed connector in V1.5. Ratifying FD-11 would change the version boundary prospectively. It must not rewrite the historical strategy.

## 4. Four recommended decisions to lock

### GD-01 — Product shape

**State:** PROPOSED FOR RATIFICATION

> Ghost V1 has two primitives, `READ` and `SEND`; each has `NOW` and `AUTO` modes.

### GD-02 — Five-minute meaning

**State:** PROPOSED FOR RATIFICATION

> Five minutes is the minimum wake/read cadence. It never forces a Send. Send is triggered only by an approved state change and current authority.

### GD-03 — V1 action boundary

**State:** PROPOSED FOR RATIFICATION

> V1 Auto Send is limited to target-specific text dispatch into advisory or safely sandboxed LLM windows under an exact Automation Contract. Ungated consequential target Agents remain manual-only.

### GD-04 — Memory boundary

**State:** PROPOSED FOR RATIFICATION

> Ghost may observe all authorized changes in scope, but selective, sourced, correctable, revocable retention is the default. Full encrypted raw recall is explicit opt-in per Context.

## 5. Derived architecture decisions recommended for ratification

### GD-05 — Human Objective is above CP Intent

One broad Human Objective may coordinate many Work Units, but each target gets its own confirmed Context and verified Intent.

### GD-06 — Schedule/trigger/authority separation

- schedule wakes;
- typed trigger justifies action consideration;
- current authority permits or blocks dispatch.

### GD-07 — Target Agent identity and capability are versioned

A provider/model/window/tool change can invalidate prior authority.

### GD-08 — One outward dispatch per target at a time

Prevent conflicting prompts, duplicates, and ownership races.

### GD-09 — Completion requires evidence

A target may report completion, but material completion is promoted only through the applicable verification rule.

### GD-10 — Governance fails closed

Guardian, policy, log, permit, or authority-evaluation failure cannot default to Send.

### GD-11 — Observation failure is visible

Read failure becomes `OBSERVATION_UNAVAILABLE`, not “nothing changed.”

### GD-12 — No silent Agent substitution

A replacement target requires capability comparison and reauthorization unless an exact substitution class was preapproved.

### GD-13 — Prompt content is not authority

Instructions inside target messages, files, webpages, tools, or quoted text remain untrusted content.

### GD-14 — Correction is prospective

Corrections and revocations update current operational state while preserving prior events.

### GD-15 — Distributed controls are Ghost extensions

Idempotency, replay protection, state/version checks, delivery confirmation, concurrency, and recovery are required product engineering but are not claimed as frozen CP functionality.

## 6. Product-canon backlog

| ID | Item | State | Required outcome |
|---|---|---|---|
| GV1-CAN-001 | Ratify or revise FD-11 | OPEN | Final V1/V1.5 product boundary |
| GV1-CAN-002 | Ratify GD-01 through GD-04 | OPEN | Customer-facing V1 product law |
| GV1-CAN-003 | Ratify derived decisions GD-05 through GD-15 | OPEN | Internal architecture law |
| GV1-CAN-004 | Confirm whether `Ghost`, `Work Unit`, `Work Episode`, `Thread`, `Task`, and `Knot` are canonical or aliases | BLOCKED by ontology work | One object vocabulary |
| GV1-CAN-005 | Produce Ghost V1 CP compatibility statement | OPEN | Exact CP use/non-use and conformance claim limits |
| GV1-CAN-006 | Update Ghost master strategy prospectively | BLOCKED by founder ratification | New version preserving historical v2.1 |
| GV1-CAN-007 | Update artifact authority index | BLOCKED by canon | Identify current authority/supersession state |

## 7. Product and market backlog

| ID | Item | State | Required outcome |
|---|---|---|---|
| GV1-MKT-001 | Select first buyer segment | OPEN | Repeated costly multi-LLM coordination problem and willingness to pay |
| GV1-MKT-002 | Select first recurring costly event | OPEN | One observable event Ghost reduces/prevents |
| GV1-MKT-003 | Select first supported provider/window pair | OPEN | Stable read/send access and truthful capabilities |
| GV1-MKT-004 | Define first ten-minute magic moment | OPEN | User experiences cross-window continuity/action value quickly |
| GV1-MKT-005 | Define V1 pricing hypothesis | DEFERRED pending value evidence | Packaging tied to saved attention/cost and accepted work |
| GV1-MKT-006 | Define V1 onboarding promise | OPEN | Minimal ceremony plus useful first connection |

## 8. Architecture/specification backlog

| ID | Item | State | Required outcome |
|---|---|---|---|
| GV1-ARC-001 | Canonical object model | OPEN | Objective, Work Unit, Context, Intent, Agent, permits, Ledger, recovery |
| GV1-ARC-002 | Observation Permit specification | OPEN | Exact Read scope, cursor, retention, expiry, revocation |
| GV1-ARC-003 | Automation Contract specification | OPEN | Recurrence, triggers, limits, budgets, stop/recovery |
| GV1-ARC-004 | Dispatch Proposal and Permit specification | OPEN | Exact target/body/authority/version/idempotency |
| GV1-ARC-005 | Agent Capability Manifest | OPEN | Advisory/sandboxed/gated/ungated and proof per capability |
| GV1-ARC-006 | Runtime state machines | OPEN | observation, trigger, Friction, dispatch, delivery, result, completion |
| GV1-ARC-007 | Concurrency and target ownership model | OPEN | One outward action, leases/epochs, human override |
| GV1-ARC-008 | Meaning Ledger schema | OPEN | states, authority effect, contradictions, provenance, retention |
| GV1-ARC-009 | Recovery Capsule specification | OPEN | safe window replacement and checkpoint recovery |
| GV1-ARC-010 | Trusted base and independent verifier | OPEN | keys, policy, updates, evidence, no self-approval |
| GV1-ARC-011 | Stop/revocation hierarchy | OPEN | target, contract, Auto Send, all automation, provider, global stop |
| GV1-ARC-012 | Local storage/sync/recovery decision | OPEN | encrypted local-first implementation and device-loss posture |

## 9. Security and privacy backlog

| ID | Item | State | Required outcome |
|---|---|---|---|
| GV1-SEC-001 | Threat model | OPEN | prompt injection, cross-context, secrets, adapters, trusted base, insider risk |
| GV1-SEC-002 | Provider permission minimization | OPEN | least OAuth/API/browser scope per adapter |
| GV1-SEC-003 | Secret detection/redaction | OPEN | prevent cross-provider credential/data leakage |
| GV1-SEC-004 | Context compartmentalization | OPEN | encryption and access separation per Context |
| GV1-SEC-005 | Retention/deletion/export policy | OPEN | user ownership and audit compatibility |
| GV1-SEC-006 | Third-party data policy | OPEN | purpose, minimization, sharing, deletion |
| GV1-SEC-007 | Adapter terms/legal review | OPEN | confirm permitted automated read/send behavior |
| GV1-SEC-008 | Signed update and rollback policy | OPEN | no silent policy/capability growth |

## 10. Validation backlog

| ID | Item | State | Required outcome |
|---|---|---|---|
| GV1-VAL-001 | Deterministic CP Reference Runtime decision | OPEN | use/rebuild external enforcement from frozen source |
| GV1-VAL-002 | PC/PE conformance tests | OPEN | executable coverage of frozen rules used |
| GV1-VAL-003 | Zero-ambiguity authority-drift suite | OPEN | stale approval, target/context/permission/model drift |
| GV1-VAL-004 | Retry/replay/idempotency suite | OPEN | no duplicate or governance bypass |
| GV1-VAL-005 | Prompt-injection authority suite | OPEN | read content cannot create authority |
| GV1-VAL-006 | Cross-context isolation suite | OPEN | no data/authority leakage |
| GV1-VAL-007 | Positive-control suite | OPEN | valid work proceeds with acceptable false holds |
| GV1-VAL-008 | Responsibility reconstruction test | OPEN | independent 100% reconstruction for consequential V1 dispatches |
| GV1-VAL-009 | Recovery/window-replacement suite | OPEN | continuity restoration without authority inheritance |
| GV1-VAL-010 | First connector capability audit | OPEN | actual versus claimed Read/Send/Gate/Prove capabilities |
| GV1-VAL-011 | V0/V0.5 user simulation | OPEN | test comprehension, targeting, authority, correction before build |
| GV1-VAL-012 | Independent pre-build audit | BLOCKED by specification | GO / GO WITH CONDITIONS / HOLD / REJECT |

## 11. Recommended execution sequence

```text
Founder ratifies/revises V1 decisions
  -> update product canon and authority index
  -> resolve ontology
  -> choose first buyer/event/provider pair
  -> write CP compatibility statement
  -> write technical reference architecture
  -> write V1 specification and threat model
  -> build executable conformance and failure tests
  -> independent pre-build audit
  -> founder GO / GO WITH CONDITIONS / HOLD / REJECT
  -> engineering
```

## 12. Explicit current hold

This record does **not** authorize:

- code creation;
- provider login/connection;
- browser automation;
- scheduled polling;
- autonomous Send;
- production data import;
- full-history retention;
- changes to the frozen Collaboration Protocol repository;
- external claims of CP conformance or Ghost production readiness.
