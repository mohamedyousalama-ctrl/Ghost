# 05 — Meaning Ledger and Provenance

**Status:** proposed Ghost V1 continuity/evidence model  
**Build authorization:** none

## 1. Why a Meaning Ledger is needed

Ghost must preserve continuity across LLM windows without flattening every message, inference, decision, and permission into one undifferentiated memory.

The core distinction is:

> **Memory answers what happened. Authority answers what may happen next.**

The Meaning Ledger is a product-level continuity and evidence projection. It is not a replacement for:

- the source provider's original message/event;
- frozen CP Context, Intent, Agent, Action, Friction, and Log stores;
- a current verified authorization.

## 2. Three-layer record model

### 2.1 Raw Event Archive

Purpose:

- preserve source-faithful authorized events or references;
- retain actor, provider, ordering, timestamps, and exact source location;
- support later correction and reconstruction;
- avoid rewriting history when interpretation changes.

Possible event types:

- human message;
- assistant message;
- system message;
- tool result;
- file/reference event;
- connector receipt;
- delivery acknowledgement;
- code/test result;
- user correction;
- revocation;
- policy decision.

### 2.2 Meaning Ledger

Purpose:

- derive structured continuity from source events;
- separate fact, report, inference, decision, commitment, authority, and unresolved state;
- connect work across windows without silently creating permission.

### 2.3 Optional Forensic Archive

Purpose:

- preserve fuller encrypted source material for selected Contexts when the user explicitly enables it;
- support legal, technical, or high-assurance reconstruction.

Default behavior should not silently enable indefinite total recall.

## 3. Default retention principle

> **Observe all authorized changes in scope; retain only what the applicable retention policy permits; preserve enough provenance to reconstruct material decisions.**

Full encrypted raw recall is explicit opt-in per Context.

## 4. Ledger item schema

Every Meaning Ledger item should include:

```text
Ledger Item ID
Source Event ID(s)
Source provider
Source account/workspace
Source conversation/window
Source actor type
Source actor identity (where available)
Source timestamp
Ingestion timestamp
Work Unit ID
Human Objective ID
Context ID/version
Claim type
Knowledge state
Content or normalized proposition
Confidence (if used)
Sensitivity class
Freshness/staleness state
Authority effect
Binding state
Contradiction links
Derived-from links
Supersedes/superseded-by links
Correction/revocation state
Retention policy
Expiry/review date
Verifier identity/status
Evidence attachments/references
Created-by model/rule version
```

## 5. Knowledge states

Recommended V1 states:

### `OBSERVED`

Ghost directly observed the source event. This says nothing yet about whether its content is true.

### `REPORTED`

A human, model, tool, or system asserted something.

Example:

> Claude Code reports that tests pass.

This is not equivalent to independently verified test evidence.

### `INFERRED`

Ghost derived a provisional interpretation from observed material.

Inference may help orient or propose, but it does not create authority.

### `CONFIRMED`

An authorized human or accepted verification process confirmed the proposition.

### `COMMITTED`

The authorized human committed a binding rule, Context, Intent, or decision.

### `CONTESTED`

Evidence or an authorized actor disputes the item.

### `SUPERSEDED`

A later decision or correction replaces the item's current operational relevance while preserving history.

### `REVOKED`

The relevant human/authority withdrew the item or permission.

### `EXPIRED`

The item no longer applies because time, condition, or review limit elapsed.

### `UNKNOWN`

The system lacks enough evidence to determine the state.

## 6. Claim types

Initial claim types may include:

- `FACT_CLAIM`
- `DECISION`
- `PROPOSAL`
- `COMMITMENT`
- `OPEN_LOOP`
- `BLOCKER`
- `COMPLETION_CLAIM`
- `VERIFICATION_RESULT`
- `AUTHORITY_GRANT`
- `AUTHORITY_REVOCATION`
- `CONSTRAINT`
- `CONTEXT_PROPOSAL`
- `CORRECTION`
- `CONTRADICTION`
- `CAPABILITY_CLAIM`
- `DELIVERY_RECEIPT`
- `RECOVERY_STATE`

## 7. Authority effects

Every item carries one explicit authority effect.

Recommended values:

```text
NONE
MAY_PROPOSE_CONTEXT
BINDS_CONTEXT
AUTHORIZES_READ
AUTHORIZES_SEND
AUTHORIZES_ONE_SHOT_ACTION
REVOKES_AUTHORITY
```

Default for imported, observed, AI-generated, and inferred items:

```text
authority_effect = NONE
```

Only an authenticated and valid authority path may create a non-`NONE` effect.

## 8. Binding state

Authority effect and binding state are related but not identical.

Recommended values:

```text
NON_BINDING
PROPOSED_BINDING
BINDING_CURRENT
BINDING_SUSPENDED
BINDING_REVOKED
BINDING_EXPIRED
```

Examples:

- a model recommendation: `NON_BINDING`;
- a proposed standing rule: `PROPOSED_BINDING`;
- a founder-confirmed rule: `BINDING_CURRENT`;
- a paused Automation Contract: `BINDING_SUSPENDED`.

## 9. Reported versus verified completion

Ghost must preserve at least these states:

```text
NOT_STARTED
IN_PROGRESS
REPORTED_COMPLETE
VERIFICATION_PENDING
VERIFIED_COMPLETE
PARTIALLY_COMPLETE
BLOCKED
FAILED
SUPERSEDED
```

A target model may only create `REPORTED_COMPLETE`.

Promotion to `VERIFIED_COMPLETE` requires the applicable evidence, such as:

- file/commit exists;
- tests ran and output is available;
- artifact opened successfully;
- independent reviewer accepted it;
- provider receipt confirms delivery;
- state mutation can be observed directly.

## 10. Source actor and authority channel

Ghost must distinguish:

- `HUMAN_AUTHENTICATED`
- `HUMAN_UNVERIFIED`
- `ASSISTANT_MODEL`
- `SYSTEM_MESSAGE`
- `TOOL_RESULT`
- `CONNECTOR_EVENT`
- `EXTERNAL_DOCUMENT`
- `UNKNOWN_ACTOR`

Only the correct authenticated authority channel may create user commitment or current permission.

A human-like sentence inside model output remains `ASSISTANT_MODEL` content.

## 11. Context isolation

Every item must belong to:

- exactly one primary Context; or
- an explicit general/user-owned layer with no target execution effect.

Cross-Context references must be explicit and purpose-bound.

The Ledger must not:

- copy private material into another target Context by default;
- use one project's authority in another;
- merge similar tasks merely because embeddings are close;
- turn a general preference into a project rule without applicable scope.

## 12. Contradictions

When two sources conflict:

- preserve both source events;
- create a `CONTRADICTION` relation;
- do not silently pick one as truth;
- identify source quality and authority;
- trigger Friction if the conflict is material to action;
- allow later verification/correction to resolve current operational state;
- never delete the historical contradiction.

## 13. Correction without historical erasure

Example:

```text
T1: User says "Use Provider A."
T2: Ghost records COMMITTED / BINDING_CURRENT.
T3: User says "Provider A was only for Project X; use Provider B here."
T4: Original remains in history.
T5: A scoped correction supersedes its use in Project Y.
```

Ghost must never rewrite T1 as though it originally contained the later limitation.

## 14. Provenance views

### 14.1 Ordinary view

Show the user only what is useful now:

- current state;
- source label;
- whether confirmed or inferred;
- correction control.

### 14.2 Decision view

For a material decision, show:

- what was observed;
- what was inferred;
- what was confirmed;
- what became binding;
- unresolved conflicts;
- current authority.

### 14.3 Forensic view

For audit/reconstruction, show:

- exact source event IDs;
- actor identities;
- provider/window IDs;
- Context/Intent/Agent versions;
- Guardian decisions;
- Friction lifecycle;
- proposal/permit hashes;
- connector attempts/receipts;
- completion verification;
- corrections and revocations.

## 15. Responsibility Chain reconstruction

Ghost must derive chain integrity from linked events.

A chain is reconstructible only if an independent verifier can establish:

1. the authenticated User Signal;
2. CP Verification result;
3. the exact AI Suggestion/proposal;
4. explicit User Commitment or valid standing Automation Contract;
5. the exact Action/dispatch;
6. the target Agent and connector;
7. the delivery/outcome evidence;
8. any later correction or revocation.

The field `responsibility_chain_intact` must never be hard-coded.

## 16. Freshness and staleness

Each Ledger item may have:

- creation time;
- last-confirmed time;
- review condition;
- expiry time;
- source version;
- Context version;
- freshness class.

Stale information can still be remembered, but:

> **stale memory may orient; it may not silently authorize.**

## 17. Sensitivity and sharing

Suggested sensitivity classes:

```text
PUBLIC
INTERNAL
CONFIDENTIAL
SENSITIVE_PERSONAL
SECRET_CREDENTIAL
THIRD_PARTY_RESTRICTED
REGULATED
```

Before cross-provider Send:

- apply data minimization;
- inspect sensitivity and provider policy;
- exclude secrets/credentials;
- respect Context sharing rules;
- require stronger approval for sensitive disclosure;
- record exact fields disclosed.

## 18. Deletion and revocation

The user must be able to:

- inspect;
- correct;
- revoke;
- expire;
- delete where permitted;
- export continuity data.

Where an audit record must survive content deletion, preserve only the minimum deletion/revocation event and cryptographic/structural reference needed to explain why later execution stopped. The detailed policy remains an open legal/security design item.

## 19. Completeness honesty

Ghost should expose whether continuity is:

- complete for the approved source range;
- partial;
- summarized;
- missing attachments;
- cursor-broken;
- provider-unavailable;
- stale;
- reconstructed from secondary evidence.

Ghost must not present a coherent summary as proof that it observed the entire history.

## 20. Minimum Ledger acceptance tests

- model output cannot create user authority;
- conflicting sources remain visible;
- correction appends rather than rewrites;
- reported completion does not become verified automatically;
- cross-Context query does not leak private fields;
- stale item cannot authorize Send;
- revoked authority prevents future dispatch;
- source event remains traceable from a derived item;
- chain reconstruction fails visibly when a link is absent;
- deletion/revocation state is honored by Context compilation.
