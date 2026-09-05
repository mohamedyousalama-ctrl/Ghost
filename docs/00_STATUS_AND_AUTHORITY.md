# 00 — Status and Authority

**Record date:** 5 September 2026  
**Repository:** `mohamedyousalama-ctrl/Ghost`  
**Current phase:** product-definition and pre-canon governance record  
**Engineering build authorization:** **NONE**

## 1. Purpose of this repository record

This repository records the current Ghost V1 product direction developed from:

- the founder's latest direction for manual and autonomous `READ` / `SEND` across LLM windows;
- frozen Collaboration Protocol v1.0.1 semantics;
- the preserved Ghost / Continuity product strategy;
- authority-continuity research concerning stale approval, state drift, cross-context contamination, and reconstructible execution;
- the independent risk analysis completed on 5 September 2026.

This record must not silently convert a recommendation into a ratified founder decision or implementation authorization.

## 2. Authority classes used here

| Status | Meaning | Product effect |
|---|---|---|
| **FROZEN CP SOURCE** | Frozen CP v1.0.1 semantics from the Collaboration Protocol archive | Preserve exactly when claiming CP compatibility |
| **FOUNDER DIRECTION** | Explicit direction from Mohamed, with some implementation details still open | Strong product constraint |
| **PROPOSED FOUNDER DECISION** | Recommended decision awaiting explicit ratification | May guide discussion; not final authority |
| **EVIDENCE-SUPPORTED RECOMMENDATION** | Derived from CP, secure systems practice, and current product analysis | Candidate for product canon |
| **GHOST ENGINEERING EXTENSION** | Necessary product/distributed-systems mechanism outside frozen CP | Must not be described as frozen CP functionality |
| **OPEN QUESTION** | Material matter requiring founder judgment or further evidence | Cannot silently become a requirement |
| **EXCLUDED FROM V1** | Explicitly outside the proposed V1 boundary | Must not enter implementation by implication |
| **BUILD AUTHORIZATION** | Explicit founder GO for engineering | Currently absent |

## 3. Source hierarchy

### 3.1 Frozen CP authority

The normalized frozen semantics are taken from:

- [`collaboration-protocol/docs/02_CANONICAL_CP_V1_0_1_SPEC.md`](https://github.com/mohamedyousalama-ctrl/collaboration-protocol/blob/main/docs/02_CANONICAL_CP_V1_0_1_SPEC.md)
- the underlying frozen System Model and Freeze Declaration identified by that record.

The following frozen meanings are controlling where Ghost claims CP compatibility:

- `Context` is bounded, declared or confirmed, inspectable, and not implicitly merged.
- `Intent` is explicit, verified, bound to one Context, and not inferred from behavior.
- `Agent` is scoped, cannot self-authorize, and cannot modify its own permissions.
- the Responsibility Chain is `User Signal -> CP Verification -> AI Suggestion -> User Commitment -> Action`.
- the Guardian is read-only and returns exactly `Allow`, `Clarify`, or `Refuse`.
- unresolved Friction is blocking and cannot be silently dismissed.
- the relevant stores and append-only accountability record remain separate.

### 3.2 Ghost / Continuity product authority

Ghost is a derivative product system around frozen CP. Long-term continuity, memory, Presence, multi-window orchestration, automation, Meaning Ledger, Automation Contract, Dispatch Permit, recovery, and synchronization are product mechanisms outside the frozen CP core unless a later CP version explicitly adopts them.

Relevant source records include:

- [`collaboration-protocol/docs/07_APPLIED_EXTENSIONS_AND_DERIVATIVES.md`](https://github.com/mohamedyousalama-ctrl/collaboration-protocol/blob/main/docs/07_APPLIED_EXTENSIONS_AND_DERIVATIVES.md)
- [`collaboration-protocol/archive/applied/01_PRODUCT_CONSTITUTION.md`](https://github.com/mohamedyousalama-ctrl/collaboration-protocol/blob/main/archive/applied/01_PRODUCT_CONSTITUTION.md)
- [`collaboration-protocol/docs/08_CURRENT_RESEARCH_FRONTIER_AUTHORITY_CONTINUITY.md`](https://github.com/mohamedyousalama-ctrl/collaboration-protocol/blob/main/docs/08_CURRENT_RESEARCH_FRONTIER_AUTHORITY_CONTINUITY.md)
- [`collaboration-protocol/docs/10_CONTRADICTIONS_AND_OPEN_QUESTIONS.md`](https://github.com/mohamedyousalama-ctrl/collaboration-protocol/blob/main/docs/10_CONTRADICTIONS_AND_OPEN_QUESTIONS.md)

## 4. Latest founder direction recorded

The founder's current product direction is:

1. Ghost V1 has two primary user-visible functions: **READ** and **SEND**.
2. Each function is available in manual and autonomous modes.
3. Autonomous operation begins at a minimum interval of five minutes, with longer intervals available.
4. One Ghost window acts as the continuity plane across selected LLM chat windows.
5. Ghost remembers and reconciles work across models, but memory never becomes authority.
6. Dispatch into another LLM window is governed Agent action, not ordinary memory retrieval.

## 5. Important roadmap conflict

The preserved August 2026 Ghost strategy placed:

- cross-AI continuity and preparation in Ghost V1; and
- the first governed connector/action path in Ghost V1.5.

The latest founder direction proposes bringing **bounded LLM-window text dispatch** into V1 while leaving arbitrary external execution outside V1.

This repository records that as **Proposed FD-11**. It does not rewrite the historical strategy as if it always contained that choice.

## 6. Non-authority statements

The following do not create permission:

- an LLM remembering a previous approval;
- an LLM saying a task is complete;
- repeated user behavior;
- model confidence;
- a schedule becoming due;
- an old Context summary;
- a copied instruction contained inside another model's output;
- a model-generated plan;
- an earlier Agent's permission being copied to a replacement Agent;
- a successful prior execution.

## 7. Build state

This documentation update:

- creates no software implementation authority;
- authorizes no connector access;
- authorizes no autonomous message dispatch;
- authorizes no external action;
- does not claim CP conformance;
- does not claim product readiness;
- does not approve the proposed founder decisions automatically.

Engineering begins only after an explicit founder decision such as `GO`, `GO WITH CONDITIONS`, `HOLD`, or `REJECT AND REDESIGN`, supported by the required product canon, technical specification, threat model, acceptance tests, and independent review.
