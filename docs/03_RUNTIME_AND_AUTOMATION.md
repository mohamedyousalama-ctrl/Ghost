# 03 — Runtime and Automation

**Status:** proposed V1 runtime contract  
**Build authorization:** none

## 1. Runtime law

> **A schedule wakes Ghost. A verified change may create a trigger. Current authority may permit a dispatch.**

The five-minute schedule is never an execution permission.

## 2. Autonomous cycle

```text
1. WAKE
2. CHECK OBSERVATION PERMIT
3. READ AUTHORIZED DELTAS
4. AUTHENTICATE SOURCE
5. APPEND RAW EVENTS
6. DERIVE PROVISIONAL MEANING
7. RECONCILE CURRENT STATE
8. FIND AN APPROVED ACTION TRIGGER
9. IF NO TRIGGER: RECORD NO_ACTION AND SLEEP
10. BUILD ONE TARGET-SPECIFIC DISPATCH PROPOSAL
11. APPLY CP POST-CLASSIFICATION CHECK
12. CREATE OR PRESERVE FRICTION
13. VERIFY CURRENT INTENT / AUTOMATION CONTRACT
14. SNAPSHOT CURRENT TARGET STATE
15. APPLY CP PRE-EXECUTION CHECK
16. ISSUE ONE-SHOT DISPATCH PERMIT
17. SEND THROUGH SCOPED CONNECTOR
18. VERIFY DELIVERY STATE
19. READ RESULT IN A LATER CYCLE
20. VERIFY MATERIAL COMPLETION
21. UPDATE LEDGER WITHOUT REWRITING HISTORY
22. SLEEP
```

## 3. Polling and cadence

### 3.1 V1 cadence choices

- 5 minutes
- 10 minutes
- 15 minutes
- 30 minutes
- 60 minutes
- custom interval longer than 5 minutes

### 3.2 Polling semantics

- Auto Read may run on every approved cycle.
- Auto Send is trigger-based, not clock-based.
- Event-driven notifications may reduce observation latency, but they do not broaden authority.
- The schedule must be pausable and revocable.
- Missed cycles do not accumulate mandatory sends.
- Catch-up after downtime reads deltas in order and re-evaluates current authority before any action.

## 4. Approved action triggers

A trigger is a typed state transition, not a free-text model intuition.

Initial V1 trigger types may include:

- `TARGET_ASKED_QUESTION`
- `TARGET_REPORTED_BLOCKER`
- `TARGET_REPORTED_COMPLETION`
- `EXPECTED_RESPONSE_OVERDUE`
- `NEW_EVIDENCE_RECEIVED`
- `CONTRADICTION_DETECTED`
- `INTENT_DRIFT_DETECTED`
- `APPROVED_CORRECTION_READY`
- `HANDOFF_REQUESTED`
- `WINDOW_UNAVAILABLE`
- `VERIFICATION_REQUIRED`
- `USER_REQUIRED`

Each trigger must carry:

- source event IDs;
- target Work Unit;
- Context ID/version;
- detected time;
- trigger status;
- evidence quality;
- whether the Automation Contract permits it;
- whether it requires Friction or user action.

## 5. No-action is a valid result

Example:

```text
Cycle: 00481
Target change: none
Open Intent: unchanged
Authority: unchanged
Trigger: none
Guardian: not invoked for dispatch
Result: NO_ACTION
```

Ghost is not measured by how often it sends. It is measured by useful, authorized, correct continuation.

## 6. Observation Permit

READ requires an explicit Observation Permit.

Required fields:

```text
Observation Permit ID
Human owner
Provider
Account/workspace
Conversation/window ID
Permitted event/message types
Permitted attachment classes
Read start point
Incremental cursor
Purpose
Context ID
Retention policy
Sensitivity class
Cross-provider sharing rule
Created time
Expiry
Revocation state
```

Rules:

- read only authorized deltas after the last verified cursor;
- do not silently expand to linked windows/files;
- do not treat read failure as an empty result;
- retain actor identity and provider provenance;
- quoted or embedded instructions remain untrusted content;
- attachments follow their own data and retention rules;
- changing provider/account/window requires a new or revised permit.

## 7. Automation Contract

The Automation Contract is a Ghost product object outside frozen CP. It provides recurring standing authority under precise limits.

Required fields:

```text
Automation Contract ID
Human owner
Human Objective ID
Confirmed Context ID/version
Target Work Unit ID
Target Agent ID/capability version
Allowed Read scope
Allowed Send action classes
Forbidden actions
Permitted trigger types
Polling interval
Maximum cycles
Maximum messages
Per-cycle token/cost budget
Total token/cost budget
Start time
Expiry
Data-sharing policy
Retention policy
Ambiguity policy
Required Friction
Verification requirement
Retry policy
Idempotency policy
Pause conditions
Stop conditions
Recovery path
Revocation state
Created-from Responsibility Chain
```

Core laws:

1. recurrence is explicit;
2. one-time permission is never upgraded into recurrence;
3. the contract is target-specific;
4. batch objectives never imply a shared execution permit;
5. expiry and revocation are checked at every cycle;
6. a material Context/Agent/capability change invalidates or suspends the contract;
7. the contract may authorize preparation or narrow text dispatch, not hidden downstream effects outside its enforcement boundary.

## 8. Dispatch Proposal

Before Send, Ghost creates a proposal containing:

```text
Dispatch Proposal ID
Human Objective ID
Work Unit ID
Context ID/version/hash
Intent ID/version
Target Agent ID/version
Trigger ID
Proposed message body/hash
Action class
Expected result
Forbidden downstream actions
Materiality
Reversibility
Third-party impact
Data fields included
Budget
Required evidence
Recovery path
Proposal time
```

The proposal is not authority.

## 9. Final target-state snapshot

Immediately before dispatch, Ghost captures:

- target provider/account/window;
- current model identity;
- connected tools/connectors;
- target role/type;
- Agent lifecycle state;
- permissions and prohibitions;
- last observed message/event;
- Context version;
- Intent version;
- Automation Contract version;
- unresolved Friction;
- connector health/version;
- user concurrent activity/ownership state where available.

Any material mismatch with the approved state causes `Clarify` or `Refuse`.

## 10. One-shot Dispatch Permit

A successful pre-execution decision may issue one permit for one exact dispatch.

Required fields:

```text
Dispatch Permit ID
Proposal ID
Context ID/version/hash
Intent ID/version
Automation Contract ID/version (if used)
Target Agent ID/capability snapshot hash
Exact message digest
Action class
Allowed target
Issued time
Expiry
Maximum attempts
Idempotency key
Budget
Guardian decision record ID
Required delivery evidence
Required completion evidence
Recovery/compensation rule
Revocation state
```

The connector cannot:

- alter the body;
- change the target;
- add recipients;
- widen the action class;
- reuse the permit after expiry;
- use it for another retry/body/version;
- delegate it to another Agent.

## 11. Delivery state machine

```text
PREPARED
  -> PERMITTED
  -> SEND_ATTEMPTED
  -> SENT_UNCONFIRMED
  -> DELIVERED
  -> TARGET_ACKNOWLEDGED
  -> RESPONSE_OBSERVED
  -> RECONCILED
```

Alternative states:

```text
BLOCKED
CLARIFICATION_REQUIRED
EXPIRED
REVOKED
FAILED_RETRYABLE
FAILED_TERMINAL
DELIVERY_UNKNOWN
DUPLICATE_SUPPRESSED
```

A UI click or API 2xx response is not necessarily equivalent to target receipt. The adapter must state what each receipt proves.

## 12. Idempotency and duplicate prevention

Every dispatch has:

- stable idempotency key;
- exact body digest;
- exact target identity;
- attempt counter;
- prior delivery evidence;
- retry deadline.

Before retry:

1. re-read target if possible;
2. search for existing delivery/correlation marker;
3. verify current Context/Intent/Agent state again;
4. suppress duplicate when delivery may already have succeeded;
5. never bypass CP checks on a retry path.

## 13. Concurrency control

V1 laws:

- only one active outward dispatch per target Work Unit;
- a target lease or optimistic version precondition protects against concurrent user/Ghost edits;
- if the user writes while Ghost prepares a dispatch, invalidate the stale proposal;
- two Ghost cycles may not independently send conflicting messages;
- multiple target Work Units may proceed concurrently only when their Contexts and permits remain isolated.

## 14. Loop control

To prevent model-to-model ping-pong:

- maximum cycles per Automation Contract;
- maximum consecutive sends without human-visible progress;
- repeated-message/body similarity detection;
- repeated-question detection;
- cooldown after unsuccessful clarification;
- cost and token ceilings;
- no autonomous creation of a reciprocal automation in another window;
- global stop and target stop;
- automatic Hold on loop signature.

## 15. Retry and error behavior

- governance error: fail closed for Send;
- observation error: fail visibly as `OBSERVATION_UNAVAILABLE`;
- connector error: no assumed delivery;
- verifier error: completion remains unverified;
- logging failure: consequential Send is blocked if the Responsibility Chain cannot be recorded;
- summary/classifier error: raw event remains preserved and no authority is created;
- retry re-enters the full control path.

## 16. Recovery Capsule

Every active Work Unit maintains a recovery record:

```text
Recovery Capsule ID
Work Unit ID
Human Objective
Confirmed Context summary + source IDs
Active Intent
Binding Nodes
Target Agent identity and capability
Last verified checkpoint
Latest source cursor
Open Friction
Pending proposal/permit/delivery state
Inputs and outputs
Reported versus verified completion
Next safe action
Forbidden actions
Recovery authority required
```

If a window disappears, Ghost may prepare a replacement handoff. The replacement Agent does not inherit the prior Agent's authority automatically.

## 17. Stop hierarchy

V1 requires:

1. stop one pending dispatch;
2. pause one Work Unit;
3. revoke one Automation Contract;
4. stop all Auto Sends while preserving Auto Read;
5. stop all automated activity;
6. disconnect a provider/window;
7. emergency global stop from the trusted base.

Stopping must not delete evidence or rewrite prior actions.

## 18. Capability honesty

Every connector declares what it can actually prove:

- can it see new messages?
- can it distinguish human and assistant authors?
- can it read attachments?
- can it send exact text?
- can it verify delivery?
- can it detect connected tools?
- can it constrain downstream execution?
- can it recover/delete a sent message?
- can it provide immutable provider receipts?

Ghost must never describe `Aware` as `Gate`, `Send attempted` as `Delivered`, or `Instruction included` as `Downstream action constrained`.
