# Dogfood Checklist

Use this checklist to test whether the workflow prevents wrong work without recreating Superpowers-level ceremony.

## Scenarios

### FAST: Small Safe Edit

- [ ] `routing-work` chooses FAST.
- [ ] No workflow skill loads after intent is clear.
- [ ] Agent inspects only necessary context.
- [ ] Agent acts directly.
- [ ] Agent verifies lightly if files changed.

### DISCIPLINE: Bug Or Failure

- [ ] `routing-work` selects `debugging-work`.
- [ ] Agent reads the exact failure before proposing fixes.
- [ ] Agent states root-cause hypothesis and evidence.
- [ ] Agent makes one scoped fix.
- [ ] Agent verifies the original failure.

### DISCIPLINE: Clear Multi-Step Work

- [ ] `routing-work` selects `planning-work`.
- [ ] Plan has ordered tasks and verification per task.
- [ ] Slop-prone execution uses `karpathy-guidelines`.
- [ ] In live work, agent executes the first task directly after planning.
- [ ] In route-only dogfood, agent states the plan it would follow before judging pass/fail.
- [ ] Extra review is used only when risk warrants it.
- [ ] `verifying-work` proves the final claim.

### DISCIPLINE: Test-First Behavior Work

- [ ] User asks for TDD/test-first, or the agent states why a behavior tripwire is needed.
- [ ] `routing-work` selects `tdd` only in that case.
- [ ] Agent writes one public-interface behavior test.
- [ ] RED fails for the expected reason.
- [ ] GREEN uses the smallest readable implementation.
- [ ] `verifying-work` owns the final completion claim.
- [ ] Agent does not use TDD for visual UI, architecture, docs, or generic verification.

### DISCIPLINE: Slop-Prone Execution

- [ ] `routing-work` selects `karpathy-guidelines` when implementation drift is likely.
- [ ] Agent defines success with a concrete proof check before editing.
- [ ] Agent uses existing patterns before inventing helpers or abstractions.
- [ ] Agent stops if the task becomes broad or ambiguous.
- [ ] Verification proves the selected task, not the whole plan by vibe.

### EXPLICIT: Pnpm Audit Remediation

- [ ] User explicitly invokes `pnpm-audit-fix`.
- [ ] `routing-work` does not select `pnpm-audit-fix` only from meta discussion.
- [ ] Agent identifies vulnerable package and advisory.
- [ ] Agent inspects dependency path with `pnpm why`.
- [ ] Agent prefers normal updates before overrides.
- [ ] Agent verifies with `pnpm audit` and relevant local checks.

### HEAVY: Ambiguous Design

- [ ] `routing-work` chooses HEAVY.
- [ ] `discovering-context` reads relevant docs/code before questions.
- [ ] `grill-me` resolves the costly ambiguity.
- [ ] Questions are one at a time with recommended answers.
- [ ] Docs mode is used only when docs or ADRs matter.

### PROVE: Completion Claim

- [ ] Agent names the exact claim.
- [ ] Agent chooses evidence that can prove that claim.
- [ ] Agent reads fresh command output or current files.
- [ ] Agent does not use narrow evidence for broad claims.
- [ ] Agent reports remaining risk instead of pretending.

### CAPTURE: Repeated Failure

- [ ] `capturing-workflow` names the repeated situation.
- [ ] Trigger and non-trigger are explicit.
- [ ] New skill is worth future behavior change.
- [ ] `SKILL.md` stays efficient; heavy examples move to references.

## Pass Criteria

- [ ] Router chooses the lightest sufficient path.
- [ ] Each loaded skill changes the next action.
- [ ] Proof matches claim scope.
- [ ] Optional gates stay optional.
- [ ] New skill comes from repeated use, not speculation.
