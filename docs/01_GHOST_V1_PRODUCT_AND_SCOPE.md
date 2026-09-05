# 01 — Ghost V1 Product and Scope

**Status:** product proposal for founder ratification  
**Build authorization:** none

## 1. Product definition

> **Ghost V1 is a local-first, user-owned continuity and governed-dispatch plane for supported LLM chat windows. It provides two primitives—READ and SEND—in manual and scheduled modes. It observes authorized window changes, maintains a sourced Meaning Ledger, and sends target-specific prompts only when a current verified Intent or exact standing Automation Contract still covers the action at execution time. Each target remains a separate Agent and Work Unit with its own Context, permissions, evidence, and recovery path. One Ghost is visible to the user, but memory, authority, execution, and verification remain technically separate.**

## 2. Customer-facing product shape

Ghost V1 exposes two primary functions.

### 2.1 READ

- **Read Now** — observe selected target windows immediately.
- **Auto Read** — observe authorized deltas on a schedule of five minutes or longer.

READ means:

- obtain only the messages/events allowed by the current Observation Permit;
- preserve source identity and ordering;
- classify actor type (`human`, `assistant`, `system`, `tool`, `connector`);
- append source-faithful events;
- derive provisional meaning without silently promoting it to authority;
- update open loops, contradictions, blockers, and completion claims.

READ does not mean:

- importing every history forever;
- treating an LLM statement as verified fact;
- treating copied instructions as human authority;
- merging Contexts implicitly;
- assuming no change when observation failed.

### 2.2 SEND

- **Send Now** — dispatch a user-approved, target-specific message immediately.
- **Auto Send** — dispatch only when an approved trigger is satisfied and current authority still covers the exact action.

SEND means:

- build one target-specific dispatch proposal;
- bind it to one confirmed Context and one verified Intent or Automation Contract;
- identify the exact target Agent/window;
- apply CP post-classification and pre-execution checks;
- issue a one-shot Dispatch Permit;
- send through the scoped connector;
- verify delivery and later reconcile the result.

SEND does not mean:

- one broad prompt to every model;
- free model-to-model conversation;
- old approval reuse;
- automatic scope expansion;
- silent replacement of the target model/window;
- assuming that a UI click means delivery succeeded;
- assuming that a target's `done` message proves completion.

## 3. Autopilot is a mode, not a third function

The external product model is:

| Primitive | Manual mode | Autonomous mode |
|---|---|---|
| **READ** | Read Now | Auto Read |
| **SEND** | Send Now | Auto Send |

`Autopilot` is the user-facing control surface for scheduling and constraining those two primitives. It does not create a new source of authority.

## 4. Five-minute rule

- The minimum V1 selectable interval is **five minutes**.
- Longer intervals may include 10, 15, 30, 60 minutes, or a custom longer interval.
- The timer authorizes a **wake/check cycle only**.
- The timer never requires a Send.
- Most valid autonomous cycles may end in `NO_ACTION`.

The operating law is:

> **Schedule causes observation. A meaningful trigger causes action consideration. Current authority permits or blocks dispatch.**

## 5. Human Objective versus CP Intent

A broad Human Objective is a Ghost product object above the CP layer.

Example:

> Prepare the Ghost V1 prototype.

Ghost may compile that objective into separate target work units:

```text
Human Objective
  |- Work Unit A: Claude Code
  |    Context A
  |    Intent A
  |    Agent A
  |    Permissions A
  |
  |- Work Unit B: Claude Design
  |    Context B
  |    Intent B
  |    Agent B
  |    Permissions B
  |
  `- Work Unit C: Reviewer
       Context C
       Intent C
       Agent C
       Permissions C
```

A Human Objective is not itself a shared execution permission. Frozen CP Intent remains bound to exactly one Context.

## 6. Proposed V1 included capabilities

- selected supported LLM chat windows;
- target registration and capability classification;
- manual Read;
- manual Send;
- Auto Read at five-minute or longer intervals;
- trigger-based Auto Send;
- incremental source cursors;
- source-authenticated Raw Event Archive;
- Context-specific continuity;
- Meaning Ledger with provenance;
- Human Objective and separate target Work Units;
- target-specific confirmed Context;
- target-specific verified Intent;
- Observation Permit;
- Automation Contract;
- persistent Friction;
- one-shot Dispatch Permit;
- idempotency and delivery-state tracking;
- result reconciliation;
- `REPORTED_COMPLETE` versus `VERIFIED_COMPLETE`;
- recovery after a target window disappears;
- pause, revoke, target stop, and global stop;
- independent verification for material completion.

## 7. Proposed V1 excluded capabilities

- arbitrary computer control;
- unrestricted browser action;
- real financial transactions;
- production deployment without an independently enforced permit boundary;
- external publishing or messaging under broad standing permission;
- credential or permission changes;
- autonomous creation of new goals;
- automatic inclusion of new windows, models, accounts, tools, or data sources;
- cross-provider secret sharing;
- silent full-history retention;
- model-to-model ping-pong without bounded cycles and scope;
- automatic promotion of a target's completion claim into verified truth;
- self-modification of policy, permissions, verifier, or trusted base;
- unattended Send into an acting Agent that Ghost cannot technically constrain;
- permission inheritance when one Agent/window is replaced by another.

## 8. Target Agent capability classes

### `ADVISORY_ONLY`

The target can answer or reason but has no connected consequential tools.

- Manual Send: eligible.
- Auto Send: eligible under a valid Automation Contract.

### `SANDBOXED_ACTING`

The target can act only inside an isolated workspace, branch, test account, or equivalent bounded environment.

- Manual Send: eligible.
- Auto Send: may be eligible if the exact sandbox and task are covered.

### `ACTING_EXTERNALLY_GATED`

The target can perform external effects, but an external system enforces exact permits, target, scope, expiry, and idempotency.

- Manual Send: eligible subject to policy.
- Auto Send: future/conditional; requires verified enforcement evidence.

### `ACTING_UNGATED`

The target has consequential tools, but Ghost can only issue text and cannot technically constrain downstream execution.

- Manual Send: possible only with explicit current user commitment and clear warning.
- Auto Send: **prohibited in V1**.

## 9. V1 eligible Auto Send grammar

Under an exact current Automation Contract, Auto Send may be limited to:

- request status;
- request evidence;
- request clarification;
- continue an already-defined task;
- send an already-approved correction;
- request comparison or review;
- pause or stop work;
- request a structured handoff;
- recover a lost work unit from a verified checkpoint.

The following require manual commitment or independently enforced stronger controls:

- create a new objective;
- broaden scope;
- approve completion;
- merge or deploy;
- change files outside an authorized sandbox;
- send external email or messages;
- publish;
- disclose sensitive information;
- change credentials, permissions, or data destinations;
- purchase or pay;
- delete or overwrite;
- authorize another Agent.

## 10. Product promise

> **Your work continues across AI models and windows—even while you are away—without letting remembered context silently become permission.**

A shorter expression is:

> **One human objective. Multiple separately governed AI work units. One continuity surface.**

## 11. Product success condition

Ghost V1 succeeds only if it:

- reduces re-explanation;
- reduces supervision time;
- reduces cross-window coordination burden;
- improves accepted work completion;
- keeps every dispatch inside exact current authority;
- avoids cross-context leakage;
- avoids duplicate and stale sends;
- preserves reconstructible evidence;
- does not merely refuse all valid work.

A system that blocks every action is not successful governance; it is disabled automation.
