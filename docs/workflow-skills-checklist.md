# Workflow Skills Checklist

Use this checklist to keep the workflow light. The spine is not a lifecycle. It is a set of gates that stop the agent from doing confident wrong work.

## Gate Map

```text
INTENT  - understand the real job
ROUTE   - choose the smallest safe path
CONTEXT - gather facts only when facts change action
DECIDE  - resolve costly ambiguity
ACT     - make the scoped change or answer; use TDD only for testable behavior loops
PROVE   - use `verifying-work` to match evidence to the claim
CLOSE   - report state, risk, and next step
CAPTURE - make a reusable skill only after repetition
```

`CLOSE` is normal agent behavior. `handoff` is explicit session-transfer support. `ACT` uses `karpathy-guidelines` when implementation slop is likely, and `tdd` when a red-green loop is the right behavior tripwire.

## Core Skills

### 1. `intent`

- [ ] Trigger: request is vague, frustrated, broad, or easy to solve at the wrong level.
- [ ] Gate: can the next action be chosen without asking?
- [ ] Output: inferred intent, literal request, recommended next action.
- [ ] Next: `routing-work` or direct action.

### 2. `routing-work`

- [ ] Trigger: starting non-trivial work after intent is understood.
- [ ] Gate: classify as `FAST`, `DISCIPLINE`, or `HEAVY`.
- [ ] Output: mode, primary skill if any, first gate.
- [ ] Rule: zero or one primary skill by default.

### 3. `discovering-context`

- [ ] Trigger: repo docs, code, tests, or previous decisions may answer the question.
- [ ] Gate: enough context exists to avoid wrong-level action.
- [ ] Output: facts, constraints, contradictions, next action.
- [ ] Stop: do not keep exploring to feel thorough.

### 4. DECIDE: `grill-me`

- [ ] Trigger: design ambiguity makes wrong work costly.
- [ ] `grill-me`: branch-by-branch design interrogation.
- [ ] Docs mode is enabled only when project language, docs, code, or durable decisions matter.
- [ ] Gate: design direction or next action is clear.
- [ ] Output: decision, recommendation, remaining risk.

### 5. `planning-work`

- [ ] Trigger: clear work has multiple dependent steps, files, risks, or agents.
- [ ] Gate: tasks are ordered, scoped, and verifiable.
- [ ] Output: goal, task list, file scope, verification per task, first task.
- [ ] Stop: do not plan when direct action is safer.

### 6. `karpathy-guidelines`

- [ ] Trigger: implementation is likely to drift, overbuild, ignore scope, or produce slop.
- [ ] Gate: change is surgical, minimal, and verifiable.
- [ ] Output: assumptions, changed behavior/files, verification, remaining risk.
- [ ] Stop: if task becomes broad or ambiguous, route back to `planning-work` or `grill-me`.

### 7. `tdd`

- [ ] Trigger: user asks for TDD/test-first, or implementation deliberately needs a behavior tripwire.
- [ ] Gate: one public-interface behavior test fails for the expected reason before implementation.
- [ ] Output: RED result, GREEN result, refactor status, remaining behavior gaps.
- [ ] Stop: do not use for visuals, architecture, docs, or final completion proof.

### 8. `debugging-work`

- [ ] Trigger: bug, failing test, regression, flaky behavior, or unexplained technical behavior.
- [ ] Gate: failure, root-cause hypothesis, and evidence exist before fixing.
- [ ] Output: failure, root cause, fix, verification, risk.
- [ ] Note: after root cause, `tdd` may add a regression test for the behavior.

### 9. `verifying-work`

- [ ] Trigger: before saying done, fixed, passing, ready, or verified.
- [ ] Gate name: `PROVE`.
- [ ] Gate: evidence actually proves the exact claim.
- [ ] Output: check run, claim proven, remaining risk.

### 10. `capturing-workflow`

- [ ] Trigger: repeated successful pattern, repeated failure mode, or user asks to make it reusable.
- [ ] Gate: trigger and non-trigger are narrow.
- [ ] Output: skill name, description trigger, short workflow, avoided anti-patterns.

## Modes

### FAST

- [ ] Intent is clear.
- [ ] Risk is low.
- [ ] No workflow skill loads after intent is clear by default.
- [ ] Inspect only necessary context.
- [ ] Act directly.
- [ ] Verify lightly if files changed.

### DISCIPLINE

- [ ] Intent is clear enough to proceed.
- [ ] One focused gate prevents likely failure.
- [ ] Bugs/failures route to `debugging-work`.
- [ ] Clear multi-step work routes to `planning-work`.
- [ ] TDD/test-first routes to `tdd` only when explicit or deliberately chosen for behavior proof.
- [ ] Pnpm audit remediation uses `pnpm-audit-fix` only when explicitly invoked.
- [ ] Slop-prone implementation routes to `karpathy-guidelines`.
- [ ] Verification matches the final claim.

### HEAVY

- [ ] Work is ambiguous, risky, broad, or design-heavy.
- [ ] First gate is `discovering-context`.
- [ ] Design ambiguity routes to `grill-me`.
- [ ] Planning happens only after design is clear.
- [ ] Review/subagents/docs happen only when justified by risk.

## Invariants

- [ ] No skill loads just because it might apply.
- [ ] Each loaded skill changes the next action.
- [ ] A broad claim needs broad proof.
- [ ] A narrow check cannot prove a broad workflow claim.
- [ ] `validate_plugin.py` proves plugin shape only, not workflow correctness.
