# 04 — Ghost V1 Risk Register

**Status:** pre-build product and architecture risk record  
**Build authorization:** none

## 1. Risk model

Ghost V1 combines persistent continuity with recurring cross-model dispatch. That creates a risk surface larger than ordinary chat memory because the system can:

- read across multiple AI providers;
- preserve long-running Context;
- carry old decisions forward;
- act while the user is away;
- send instructions into windows that may themselves have tools.

The governing principle is:

> **Continuity can increase competence. It must never silently increase authority.**

Risk states:

- **P0 — constitutional / release-blocking:** can create unauthorized action, cross-context leakage, silent power growth, or irreconstructible responsibility.
- **P1 — major:** can materially corrupt continuity, produce duplicate work, leak sensitive data, or create unsafe cost/loop behavior.
- **P2 — operational:** reduces usability, trust, efficiency, or recoverability but is less likely to create a consequential external effect directly.

## 2. Authority and meaning risks

| ID | Risk | Severity | Failure example | Required mitigation |
|---|---|---:|---|---|
| G-RISK-001 | Memory becomes authority | P0 | An old approval or preference causes a new Send | Default `authority_effect=NONE`; current verified Intent or exact Automation Contract required |
| G-RISK-002 | Cross-context contamination | P0 | A VEIS instruction is applied to Ghost or one client/project leaks into another | One confirmed Context per target Work Unit; no implicit merge; Context hash/version on every proposal |
| G-RISK-003 | Broad objective becomes shared permission | P0 | “Finish Ghost” authorizes Claude Code, design, GitHub, and external messages equally | Human Objective compiles into isolated target-specific Intents and permits |
| G-RISK-004 | Stale approval reuse | P0 | Yesterday’s “continue” is reused after files, target, tools, or scope changed | Execution-time revalidation; expiry; target/context/version checks |
| G-RISK-005 | Content-as-command | P0 | A model output saying “send this now” is treated as user authority | Only authenticated human commitment or valid standing authority can authorize Send |
| G-RISK-006 | Silent Intent Inference | P0 | Ghost chooses a material interpretation while the user is absent | IPP detection; Guardian `Clarify`; persistent Friction |
| G-RISK-007 | Surfaced ambiguity decay | P0 | A question waiting for the user disappears in later cycles and execution proceeds | Friction persists until an allowed human/system resolution |
| G-RISK-008 | Standing instruction decay | P1 | A recurring five-minute rule fires once and is marked complete | Explicit recurrence object, next-due state, last-fired event, expiry, stop condition |
| G-RISK-009 | Agent substitution authority transfer | P0 | A dead Claude window is replaced by another model that inherits old authority | New Agent ID and capability snapshot; reauthorization unless exact substitution class was approved |
| G-RISK-010 | No-self-amplification failure | P0 | Ghost adds a provider, window, tool, permission, data destination, or action class | New capability/integration requires explicit approval; trusted base protects permissions |
| G-RISK-011 | Ghost verifies itself | P0 | The same model sends, judges success, and marks the result verified | Independent verifier or external evidence for material completion |
| G-RISK-012 | Personality changes reality/permission | P0 | Friendly Presence suppresses a warning or treats warmth as consent | Persona affects delivery only; truth, consent, permission, safety, and retention remain separate |
| G-RISK-013 | Model confidence presented as human commitment | P0 | “95% sure” becomes permission to dispatch | Confidence and authority stored separately; confidence never advances Responsibility Chain |
| G-RISK-014 | Context proposal silently activates | P0 | Ghost infers the user is in Project A and sends there without confirmation | Context Bud/proposal may prepare only; material Context requires confirmation |
| G-RISK-015 | Node/Pivot confusion | P1 | A non-binding note is treated as a permanent rule | Canonical types and visible binding state; only committed Node constrains action |
| G-RISK-016 | False user authorship | P0 | AI-generated text imported from history becomes “the user’s belief” | Actor provenance; imported model content begins as `REPORTED`/`INFERRED`, not user-confirmed |

## 3. Automation and distributed-system risks

| ID | Risk | Severity | Failure example | Required mitigation |
|---|---|---:|---|---|
| G-RISK-020 | Timer becomes Send trigger | P0 | Ghost sends every five minutes regardless of need | Separate Wake from typed Action Trigger |
| G-RISK-021 | Duplicate dispatch | P0 | Retry posts the same prompt twice and causes duplicate downstream work | Idempotency key, exact body hash, delivery check, duplicate suppression |
| G-RISK-022 | Unknown delivery | P1 | Browser clicks Send, but the target never receives it | `SENT_UNCONFIRMED`/`DELIVERY_UNKNOWN`; adapter-specific receipts |
| G-RISK-023 | Retry bypasses governance | P0 | Error retry skips Context/Intent/Guardian checks | Every attempt re-enters full PC/PE path |
| G-RISK-024 | Time-of-check/time-of-use drift | P0 | Target tools or Context change after approval but before Send | Immediate final snapshot/version preconditions; refuse on drift |
| G-RISK-025 | Concurrent human action | P0 | User changes target conversation while Ghost prepares a prompt | Target lease/epoch; invalidate stale proposal on human activity |
| G-RISK-026 | Two Ghost cycles collide | P0 | Two schedulers send contradictory instructions to one window | One active outward dispatch per Work Unit; serialized target queue |
| G-RISK-027 | Model-to-model ping-pong | P1 | Two windows repeatedly ask each other for status/revision | Max cycles/messages, loop signatures, cooldown, Hold, global stop |
| G-RISK-028 | Runaway token/cost use | P1 | Five-minute polling repeatedly invokes expensive models | Per-cycle, daily, and objective budgets; no-op cycles; event filters |
| G-RISK-029 | Window/session disappearance | P1 | The active target dies and project state is lost | Recovery Capsule; last verified checkpoint; explicit replacement handoff |
| G-RISK-030 | Incomplete/truncated context treated as complete | P0 | Ghost sends based on a partial summary | Completeness state, cursor continuity, source coverage markers, `UNKNOWN` where missing |
| G-RISK-031 | Provider UI/API drift | P1 | Adapter reads the wrong element or sends to the wrong conversation | Versioned adapters, canary tests, target identity verification, fail closed |
| G-RISK-032 | Agent capability changes silently | P0 | Advisory window gains code/deploy tools between cycles | Capability snapshot/version checked before Send |
| G-RISK-033 | Partial downstream execution | P0 | Target edits files and then fails before tests/recovery | Partial state evidence, checkpointing, recovery/compensation plan |
| G-RISK-034 | Overblocking positive controls | P1 | Ghost avoids every risk by refusing all valid work | Positive control suite; false-hold metric; value gate |
| G-RISK-035 | Recurrence catch-up storm | P1 | After downtime, every missed interval fires as a separate Send | Coalesce missed wakes; evaluate only current state and trigger |
| G-RISK-036 | Target response misassociation | P0 | A response is linked to the wrong dispatch or Work Unit | Correlation ID, provider message IDs, causal links, target verification |
| G-RISK-037 | One outward voice violation | P1 | Two Agents send contradictory external messages for one target | Single active outward owner/permit per target |
| G-RISK-038 | Queue starvation | P2 | One noisy Work Unit consumes all cycles and attention | Fair scheduling, urgency/materiality policy, budget isolation |
| G-RISK-039 | Clock/expiry inconsistency | P0 | Permit appears valid because provider clocks disagree | Trusted time source, issued/received times, bounded skew policy |

## 4. Security, privacy, and evidence risks

| ID | Risk | Severity | Failure example | Required mitigation |
|---|---|---:|---|---|
| G-RISK-040 | Prompt injection from a target window | P0 | Read content instructs Ghost to expose secrets or change scope | Treat all target content as untrusted data; separate authority channel |
| G-RISK-041 | Cross-provider secret leakage | P0 | Credentials/private data are sent from one model to another | Secret detection, field minimization, provider sharing rules, redaction |
| G-RISK-042 | Total-recall central breach | P0 | One vault compromise exposes every project and relationship | Per-Context encryption/compartmentalization; selective retention; protected keys |
| G-RISK-043 | Third-party data overcollection | P1 | Other people’s messages/files are retained without need | Purpose limitation, sensitivity classification, retention/deletion controls |
| G-RISK-044 | Source/provenance loss | P0 | A summary becomes detached from original actor/message | Immutable source pointer, provider ID, timestamp, hash, derivation links |
| G-RISK-045 | Historical rewriting | P0 | Ghost edits old memory to appear correct | Append corrections; preserve superseded state and chronology |
| G-RISK-046 | False completion propagation | P0 | Target says “done”; every window treats it as verified | Separate `REPORTED_COMPLETE` and `VERIFIED_COMPLETE` |
| G-RISK-047 | False Responsibility Chain claim | P0 | UI displays “chain intact” without reconstruction | Compute chain from linked events; independent reconstruction test |
| G-RISK-048 | Deletion versus audit conflict | P1 | User deletion breaks required accountability references | Data minimization, crypto-shredding, minimal deletion event, policy design |
| G-RISK-049 | Trusted-base compromise | P0 | Ghost edits policy, keys, verifier, or evidence roots | Separate protected service/keys; signed releases; no model write access |
| G-RISK-050 | Connector token overprivilege | P0 | Read-only need receives write/admin OAuth scope | Least privilege, per-connector scopes, periodic review/revocation |
| G-RISK-051 | Account/window identity confusion | P0 | Same-named chats or workspaces cause wrong-target send | Stable provider IDs, account IDs, visual confirmation, target digest |
| G-RISK-052 | Sensitive data in logs | P1 | Append-only logs become a second secret store | Store hashes/typed evidence where possible; encrypt sensitive payloads; access policy |
| G-RISK-053 | Malicious or compromised verifier | P0 | Verifier falsely promotes completion | Separation, verifier identity, evidence requirements, independent audit path |
| G-RISK-054 | Provider terms/policy incompatibility | P1 | Automated reading/sending violates platform terms or access rules | Capability/legal review per adapter; disable unsupported mode |
| G-RISK-055 | Local-is-secure fallacy | P0 | Device compromise exposes supposedly safe local memory | Encryption, protected keys, device-loss plan, lock/recovery, threat model |

## 5. Product and usability risks

| ID | Risk | Severity | Failure example | Required mitigation |
|---|---|---:|---|---|
| G-RISK-060 | User cannot tell what Ghost may do | P0 | Presence looks powerful but connector is advisory only | Capability Manifest per target/action |
| G-RISK-061 | Too much friction | P1 | User spends more time approving than coordinating manually | Least intrusive sufficient intervention; standing narrow contracts; measure burden |
| G-RISK-062 | Too little friction | P0 | Material ambiguity is silently resolved to maintain flow | Consequence-sensitive Friction; hard authority floors |
| G-RISK-063 | Live Work Field overload | P1 | Many episodes hide priority or cause target mistakes | Stable positions, filters, accessible list baseline, overload limits |
| G-RISK-064 | Magical relevance hides provenance when needed | P1 | User cannot understand why Ghost acted after a dispute | Magic by default; one-gesture correction; provenance on request/material action |
| G-RISK-065 | Emotional dependence/manipulation | P0 | Presence pressures user to stay, disclose, or grant more power | Anti-dependency policy; no engagement optimization; easy departure |
| G-RISK-066 | Ghost seems like another chat window | P2 | User does not experience continuity/action value | Read/Send/Autopilot primitives; live Work Units; situated Presence |
| G-RISK-067 | User cannot recover from wrong dispatch | P1 | No cancel, pause, correction, or replacement path | Reversibility, stop hierarchy, recovery capsules, compensation where possible |
| G-RISK-068 | Misleading “total recall” promise | P1 | User expects perfect complete memory despite retention/source gaps | Truthful completeness indicators and retention choices |

## 6. Known historical implementation lessons

The Collaboration Protocol archive preserves several defects from prior applied implementations. Ghost V1 must make them explicit anti-patterns:

1. **Guardian fail-open on error** — prohibited.
2. **Monitoring continuation on parse/evaluation error** — prohibited for consequential Send.
3. **Retry path skipping normal governance** — prohibited.
4. **Hard-coded `responsibility_chain_intact=true`** — prohibited.
5. **Implementation artifact silently redefining frozen semantics** — prohibited.
6. **Prompt-described governance treated as external enforcement** — prohibited.

## 7. Release-blocking invariants

Ghost V1 cannot release Auto Send unless the implementation can demonstrate:

- no Send without current exact authority;
- no Context merge by default;
- no Agent substitution authority inheritance;
- no retry path bypass;
- duplicate suppression;
- prompt injection cannot create authority;
- material completion is not self-verified;
- every consequential dispatch chain is reconstructible;
- global stop and contract revocation work;
- a valid positive control can proceed without unreasonable false holds.

## 8. Falsification conditions

The proposed V1 wedge should be narrowed, delayed, or rejected if:

- manual coordination is faster or more reliable for the target users;
- Auto Read creates unacceptable privacy/retention burden;
- Auto Send cannot be technically constrained for the chosen targets;
- false holds eliminate time savings;
- cross-context or stale-approval failures cannot be driven to the release floor;
- connector instability makes target identity/delivery unreliable;
- the product requires broader provider permissions than users will grant;
- a simpler conventional workflow provides equivalent continuity and authority protection;
- users do not repeatedly use or pay for the complete Read -> Send -> Read Result loop.
