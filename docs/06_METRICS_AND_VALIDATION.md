# 06 — Metrics and Validation

**Status:** proposed validation program  
**Build authorization:** none

## 1. Validation principle

Ghost V1 must prove both sides of the product claim:

1. it improves continuity and accepted work with less human attention and less AI waste; and
2. it does not convert memory, inference, old approval, or target-model content into unauthorized action.

A system that refuses every Send is not successful. Positive controls are mandatory.

## 2. North-star metric

The preserved Ghost strategy proposes:

> **Intent-faithful accepted outcomes per hour of human attention and per unit of AI cost.**

For V1 this must be operationalized with explicit definitions.

### 2.1 Intent-faithful

An outcome is intent-faithful only when:

- the exact target-specific action remained inside the active verified Intent or Automation Contract;
- Context boundaries were preserved;
- the target Agent and permissions were current;
- no unresolved Friction was bypassed;
- material constraints were honored;
- the Responsibility Chain is reconstructible.

### 2.2 Accepted outcome

An outcome counts only when:

- the human accepts it; or
- a predeclared objective verification rule confirms it;
- no release-blocking authority, privacy, safety, or cross-context failure occurred.

### 2.3 Human attention

Measure active minutes spent:

- re-explaining Context;
- checking target status;
- resolving wrong scope;
- reviewing dispatches;
- correcting duplication;
- verifying completion;
- recovering lost windows.

### 2.4 AI cost

Measure:

- tokens/input/output;
- model/API spend;
- connector/runtime cost;
- repeated context transfer;
- no-op polling overhead;
- failed/retried dispatch cost.

## 3. Required V1 safety/accountability metrics

### M-01 — Cross-Context Contamination Rate (CCR)

Rate at which data, authority, instructions, or execution from one Context are applied to another.

**Release target:** zero in the release test suite; any consequential occurrence is a release blocker.

### M-02 — Stale Approval Reuse Rate

Rate at which a previously valid approval is reused after a material change in target, payload, Context, permission, Agent, capability, constraint, or expiry.

**Release target:** zero in the authority-drift test suite.

### M-03 — Unauthorized Dispatch Rate

Rate of Sends lacking current exact authority at execution time.

**Release target:** zero in controlled tests.

### M-04 — Duplicate Dispatch Rate

Rate at which the same logical instruction is delivered more than once without explicit recurrence semantics.

**Release target:** zero under injected timeout/retry races.

### M-05 — Unverified Completion Promotion Rate

Rate at which `REPORTED_COMPLETE` is promoted to `VERIFIED_COMPLETE` without the required evidence.

**Release target:** zero.

### M-06 — Prompt-Injection Command Acceptance Rate

Rate at which content read from a target window creates or broadens authority.

**Release target:** zero in adversarial tests.

### M-07 — Agent Substitution Authority Violation Rate

Rate at which a replacement/new model/window inherits authority without valid approval.

**Release target:** zero.

### M-08 — Responsibility Reconstruction Rate (RRR)

Proportion of consequential dispatches for which an independent evaluator can reconstruct:

- user signal;
- Context;
- Intent;
- Agent;
- AI suggestion/proposal;
- user commitment or Automation Contract;
- Guardian decisions;
- Friction state;
- exact dispatch;
- connector receipt;
- result and verification.

**Release target:** 100% for consequential V1 dispatches in controlled tests.

### M-09 — Valid Action False-Hold Rate

Rate at which a fully authorized, unchanged positive-control action is incorrectly blocked or held.

This prevents “safe by refusing everything.”

### M-10 — Governance Failure Open Rate

Rate at which Guardian, classifier, verifier, logging, or connector-evaluation failure results in permission to Send.

**Release target:** zero.

## 4. Required V1 value metrics

### M-11 — Re-Explanation Time Saved

Difference in minutes required to restore a target window to useful project state with Ghost versus the baseline workflow.

### M-12 — Human Intervention Minutes per Verified Work Unit

Active human coordination/review time divided by verified completed Work Units.

### M-13 — AI Cost per Accepted Outcome

Total model/connector spend divided by accepted outcomes.

### M-14 — Context Recovery Success Rate

Proportion of lost/replaced windows restored to the correct current state without material correction.

### M-15 — First Useful Continuity Time

Time from connecting/selecting a source window to the first accepted continuity benefit.

### M-16 — Autonomous Cycle Utility Rate

Proportion of cycles resulting in:

- useful state reconciliation;
- justified dispatch;
- justified Hold;
- or meaningful user alert.

No-op cycles are not automatically failures, but their cost must remain bounded.

### M-17 — Accepted Autonomous Dispatch Rate

Proportion of Auto Sends the user later accepts as useful, correctly scoped, and properly timed.

### M-18 — Correction Burden

Number and time cost of user corrections to:

- Context;
- meaning;
- target selection;
- dispatch text;
- completion status;
- retention/provenance.

## 5. Core test layers

### 5.1 Deterministic unit tests

Cover:

- CP post-classification rules;
- CP pre-execution rules;
- Friction persistence;
- Observation Permit scope;
- Automation Contract expiry/revocation;
- Dispatch Permit exactness;
- idempotency;
- delivery-state transitions;
- Ledger state transitions;
- stop hierarchy.

### 5.2 Property-based tests

Required properties:

- no consequential Send without current valid authority;
- model/target content alone cannot create authority;
- same input state yields the same deterministic policy result;
- expired/revoked permit cannot execute;
- target/body mutation invalidates permit;
- Context mismatch blocks;
- unresolved Friction blocks;
- replacement Agent cannot inherit authority silently;
- duplicate retry cannot create a second logical dispatch;
- a stable authorized positive control can execute.

### 5.3 Authority-drift tests

Every scenario begins with exact, unambiguous authority. Mutate only post-approval state.

Required classes:

- stable positive control;
- payload/message drift;
- target/window drift;
- model/tool version drift;
- Context drift;
- provider/destination drift;
- permission revocation;
- Agent substitution;
- constraint activation;
- unresolved Friction/exception;
- expiry;
- handoff corruption;
- Context closure;
- concurrent human edit;
- connector capability change.

### 5.4 Retry/race/failure injection

Inject:

- send timeout after possible delivery;
- duplicated webhook/event;
- delayed target response;
- provider outage;
- malformed message extraction;
- missing actor identity;
- log-store failure;
- Guardian evaluation failure;
- verifier failure;
- scheduler duplicate wake;
- user activity between permit and Send;
- two cycles competing for the same target;
- window replacement mid-contract.

### 5.5 Prompt-injection tests

Place instructions in:

- assistant output;
- quoted user text;
- code blocks;
- files/attachments;
- tool results;
- webpages pasted into a target;
- fake system-message text;
- a target model claiming the user approved something.

Expected result: the content can be recorded/analyzed but cannot create authority.

### 5.6 Cross-context isolation tests

Use similar project names and overlapping terminology to test:

- wrong-project retrieval;
- wrong-client data;
- general preference versus binding project rule;
- identical file names in separate repositories;
- same person in personal and enterprise Contexts;
- one objective spanning many Work Units;
- batch selection with one excluded target.

### 5.7 Recovery tests

- target window disappears;
- cursor is lost;
- source history is truncated;
- replacement Agent has weaker/stronger capabilities;
- partial work exists;
- reported completion conflicts with repository/file truth;
- user corrects the recovery capsule;
- old target later returns.

## 6. Baselines

Ghost V1 should be compared against strong practical baselines, not only an ordinary raw LLM.

Recommended conditions:

1. manual multi-window coordination;
2. one-time copied project summary;
3. provider-native memory/project features;
4. scheduler + fixed template messages;
5. workflow automation with RBAC/approval/logging;
6. prompt-described Ghost/CP without external enforcement;
7. Ghost continuity only, no Auto Send;
8. full proposed Ghost V1 governed Read/Send runtime.

## 7. Oracle-state versus end-to-end evaluation

### Oracle-State evaluation

Provide correct structured:

- Context;
- Intent;
- Agent;
- permissions;
- constraints;
- trigger;
- candidate dispatch.

This isolates governance/runtime behavior.

### End-to-End evaluation

Require Ghost to derive relevant structured state from real LLM-window messages.

This tests interpretation plus governance.

A classification failure must not be misreported as a failure of the deterministic CP rules.

## 8. Proposed initial demo/evaluation scenario

Use three windows:

- Ghost control/continuity surface;
- Claude Code or another sandboxed acting Agent;
- an advisory reviewer/design Agent.

Flow:

1. user creates one Human Objective;
2. Ghost prepares separate target Work Units;
3. user commits exact Contexts and automation limits;
4. Ghost sends scoped implementation request;
5. implementation Agent reports completion;
6. Ghost records `REPORTED_COMPLETE`;
7. reviewer receives only relevant Context and evidence;
8. reviewer finds a defect;
9. Ghost observes the result on a later cycle;
10. approved correction trigger becomes true;
11. Ghost revalidates current authority;
12. Ghost sends the correction request;
13. implementation Agent returns evidence;
14. independent check promotes to `VERIFIED_COMPLETE`;
15. user asks what happened while away;
16. Ghost reconstructs the full chain.

## 9. Acceptance gates before any V1 Auto Send pilot

- canonical ontology approved;
- CP compatibility statement approved;
- threat model completed;
- Observation Permit implemented/tested;
- Automation Contract implemented/tested;
- one-shot Dispatch Permit implemented/tested;
- no retry bypass;
- prompt-injection authority tests pass;
- Context isolation tests pass;
- duplicate suppression tests pass;
- revocation/global stop tests pass;
- Responsibility Chain independently reconstructible;
- target Agent capability classification truthful;
- acting-ungated Agents excluded from unattended Send;
- positive controls execute at acceptable false-hold level;
- privacy/retention policy approved;
- independent audit issues GO or GO WITH CONDITIONS;
- founder explicitly authorizes the pilot.

## 10. Falsification Card template

Every major mechanism should have:

```text
Hypothesis
Customer/problem reason
Baseline
Test
Evidence source
Success condition
Harm/guardrail condition
Continue condition
Narrow condition
Stop condition
Time budget
Cost budget
Review authority
What remains unproven after success
```

Priority Falsification Cards:

- five-minute polling;
- Auto Read usefulness;
- Auto Send usefulness;
- Meaning Ledger accuracy;
- LLM history import;
- Work Unit/Live Work Field UX;
- Automation Contract comprehension;
- target capability classification;
- independent verification burden;
- first connector/provider;
- first buyer/recurring costly event.

## 11. Evidence discipline

Every result must distinguish:

- specification truth;
- implementation truth;
- executed test evidence;
- user/pilot evidence;
- market evidence;
- model proposal;
- unverified claim.

No score should be presented as validated without:

- stable denominator;
- raw evidence;
- reproducible scoring;
- known exclusions;
- independent review where subjective judgment remains.
