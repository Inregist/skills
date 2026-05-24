# Skill Architecture V2

Yeehaw treats the agent like an engineer learning company habits.

The goal is not to automate a rigid process. The goal is to shape behavior:

- understand vague human intent before acting;
- inspect repo evidence before asking;
- interview when work is big, ambiguous, or costly;
- make multi-step work visible so the human can steer;
- code small, readable, and maintainable changes;
- prove claims with system evidence;
- learn from repeated mistakes without bloating rules;
- report work before committing.

The human is the tech lead and product owner. Skills are coaching, role ownership, guardrails, review habits, and compact memory.

## Design Rules

Use the `write-a-skill` structure for every owned skill:

- frontmatter description is the product surface;
- description must include specific "Use when..." triggers;
- `SKILL.md` should stay under 100 lines;
- split rarely needed detail into one-level reference files;
- add scripts only for deterministic repeated work;
- review with the user before large skill migrations.

Add a skill only when it changes agent behavior. Do not add a skill for every incident. Capture repeated mistake classes.

## Core Skill Set

### 1. `intent-preflight`

Understands the user's real intent and chooses the next behavior. Use at the start of non-trivial work, when the user is vague/frustrated/corrective, when the request may be solved at the wrong level, or before loading narrower workflow skills.

Why it exists:

- user requests are often vague, emotional, incomplete, or symptom-shaped;
- agents otherwise solve the literal request and miss the real outcome;
- this is the front door for the workflow.

Expected output:

- intended outcome;
- literal request vs real goal;
- next path: direct action, inspect evidence, interview, plan, debug, execute, verify, or handoff.

### 2. `intent-interview`

Transfers big or ambiguous user intent into chat context through focused questioning and evidence checks. Use when work feels large, product/design/architecture ambiguity exists, wrong work would be expensive, the user is thinking aloud, or repo docs/domain language may matter.

Why it exists:

- big work needs shared context before implementation;
- users often forget to invoke an interview skill;
- docs mode should happen when the work is inside a repo or affects durable project language/behavior.

Expected output:

- clarified goal;
- decisions;
- constraints and non-goals;
- relevant repo evidence;
- open risks;
- implementation-ready context.

### 3. `implementation-plan`

Turns clarified context into visible, implementable tasks. Use when work spans multiple files, dependencies, steps, risks, agents, or when a third-party agent could implement from the plan.

Why it exists:

- agents plan privately and humans cannot steer early;
- task breakdown should be visible in the TUI;
- implementation plans should be sufficient for another teammate.

Expected output:

- visible task list;
- task goals and dependencies;
- files/areas;
- acceptance criteria;
- verification per task;
- risks and non-goals.

### 4. `engineering-discipline`

Guides code execution toward small, readable, maintainable changes. Use when writing or refactoring code, when implementation may drift, when readability/simplicity matter, or when past slop patterns are likely.

Why it exists:

- agents overbuild, add one-off helpers, silence types, invent fallbacks, and write clever code;
- this skill is the edit-time discipline and anti-pattern list.

Expected output:

- scoped change;
- existing patterns used first;
- anti-patterns avoided or justified;
- verification chosen before completion.

Rule format for anti-patterns:

```text
Pattern:
Avoid:
Prefer:
Allowed when:
```

### 5. `debug-discipline`

Finds root cause before fixes. Use for bugs, failures, regressions, flaky behavior, failing tests, build errors, runtime errors, or unexpected behavior.

Why it exists:

- agents guess fixes from symptoms;
- root cause and reproduction must come before patching.

Expected output:

- reproduction or observed failure;
- evidence;
- root-cause hypothesis;
- scoped fix;
- regression proof.

### 6. `verification-discipline`

Proves completion claims with fresh evidence. Use before saying done, fixed, working, passing, ready, safe, or verified.

Why it exists:

- agents claim success from stale, narrow, or missing checks;
- proof must match claim scope.

Expected output:

- exact claim;
- check run or inspected evidence;
- what the evidence proves;
- remaining risk.

### 7. `learning-loop`

Captures repeated mistakes into compact reusable rules. Use when the user identifies a repeated agent mistake, a slop pattern recurs, or workflow memory should prevent future mistakes.

Why it exists:

- the system should learn from mistakes;
- rules should be compact and hard-edged;
- one-off incidents should not bloat the catalog.

Expected output:

- repeated pattern;
- proposed compact rule;
- allowed exceptions;
- target skill to update.

### 8. `handoff`

Transfers session state to another agent or future session. Use when work pauses, the user goes AFK, context is long, or another session will continue.

Why it exists:

- long-running work needs state transfer without replaying the full chat;
- handoff should reference artifacts instead of duplicating them.

Expected output:

- current state;
- important decisions;
- changed files/commits;
- next action;
- suggested skills.

## Role Skills

Role skills are optional employee hats. They are not the workflow core.

Add or keep a role skill only when it contains ownership questions and standards that are specific to that role.

Recommended role skills:

- `product-designer`: product intent, user workflows, UX structure, acceptance criteria, product tradeoffs.
- `frontend-engineer`: React/UI implementation, state ownership, accessibility, forms, API consumption, browser proof.
- `backend-engineer`: API/data/auth/persistence boundaries, validation, typed errors, production safety.
- `devops-engineer`: deploy, CI/CD, infra, env, secrets, runtime safety.

Role skills should not duplicate the generic engineering discipline. They should apply it inside their role.

## Validation Skills

Validation skills change the method, not the whole workflow.

- `tdd`: behavior tripwire during implementation. Not final verification.
- `browser-proof`: Playwright/screenshot/interaction proof for UI behavior.
- `code-review`: quick independent review for risky or non-trivial changes. Not mandatory for tiny edits.

External design input from `thananon/9arm-skills` engineering skills:

- Adapt `debug-mantra` ideas into `debug-discipline`: reproduce first, trace the fail path, falsify hypotheses, keep a short breadcrumb ledger.
- Adapt `scrutinize` into `code-review`: question whether the change should exist, trace real code paths rather than only diffs, verify claims, cite evidence, and produce actionable findings.
- Adapt `post-mortem` into `learning-loop`: only after a bug is fixed and validated; require root cause, mechanism, fix, validation, why it slipped, and a prevention rule.
- Do not import these skills wholesale; they are useful design input but too verbose and ritual-heavy for low-token Yeehaw.

## Explicit Tools

Explicit tools are useful but should not auto-trigger as workflow core.

- `caveman`: terse communication mode.
- `commit-planner`: commit only when the user asks; inspect dirty tree; group changes for teammate review; split commits when that improves understanding.
- `audit-fix`: dependency audit remediation only when explicitly invoked.

## Current Skill Migration Map

| Current skill | V2 disposition | Reason |
| --- | --- | --- |
| `intent` | Rename/reshape to `intent-preflight` | Best-performing skill; make it the front door. |
| `grill-me` | Rename/reshape to `intent-interview` | "Grill" is too user-invoked; interview should trigger for big ambiguous work. |
| `planning-work` | Rename/reshape to `implementation-plan` | Must require visible TUI task breakdown and third-party implementability. |
| `karpathy-guidelines` | Rename/reshape to `engineering-discipline` | Keep anti-slop edit-time guardrails; preserve hard blacklist. |
| `debugging-work` | Rename/reshape to `debug-discipline` | Strong specific failure mode; keep as core. |
| `verifying-work` | Rename/reshape to `verification-discipline` | Strong specific failure mode; keep as core. |
| `capturing-workflow` | Rename/reshape to `learning-loop` | Capture repeated mistakes, not every incident. |
| `handoff` | Keep | Explicit and useful for session transfer. |
| `routing-work` | Remove or explicit-only | Too meta; inline tiny routing belongs in intent preflight. |
| `frontend-engineer` | Keep as role skill | Useful role ownership context. |
| `backend-engineer` | Keep as role skill | Useful role ownership context. |
| `frontend-design` | Merge into `product-designer` or keep explicit | Useful only for visual/product work; not core. |
| `code-quality-principles` | Merge into `engineering-discipline` or keep review-only | Overlaps with discipline; avoid duplicate generic advice. |
| `tdd` | Keep as validation skill | Method for behavior feedback, not a general proof skill. |
| `playwright-cli` | Rename/keep as `browser-proof` | UI proof tool; useful when visual/interaction evidence matters. |
| `caveman` | Keep explicit | Personal communication mode. |
| `caveman-commit` | Rename/reshape to `commit-planner` | Commit should be explicit and review-oriented. |
| `pnpm-audit-fix` | Keep explicit | Narrow dependency remediation tool. |
| `vercel-composition-patterns` | Move out of core catalog or reference-only | Specialist framework reference; high trigger noise. |
| `vercel-react-best-practices` | Move out of core catalog or reference-only | Specialist framework reference; high trigger noise. |
| `web-design-guidelines` | Merge into product/frontend role or keep explicit review | Specialist review lens; not workflow core. |
| `discovering-context` | Fold into `intent-preflight` and `intent-interview` | "Use evidence before asking" should be default behavior. |

## Active Catalog Shape

Core:

```text
intent-preflight
intent-interview
implementation-plan
engineering-discipline
debug-discipline
verification-discipline
learning-loop
handoff
```

Role:

```text
product-designer
frontend-engineer
backend-engineer
devops-engineer
```

Validation:

```text
tdd
browser-proof
code-review
```

Explicit:

```text
caveman
commit-planner
audit-fix
```

Removed from active catalog:

```text
routing-work
discovering-context
vercel-composition-patterns
vercel-react-best-practices
web-design-guidelines
frontend-design
code-quality-principles
```

## Completed Migration

1. Reviewed the v2 architecture with the user.
2. Created the new core, role, validation, and explicit skills.
3. Kept descriptions trigger-focused; this is the invocation surface.
4. Removed superseded and reference-heavy v1 skills from the active plugin catalog.
5. Validated the plugin shape after cleanup.
6. Leave install refresh and commit for explicit user approval.

## Active Surface Cleanup

V2 is now the active surface. Superseded or reference-heavy v1 skills were removed from `skills/` to reduce trigger noise. Git history is the archive for deleted source material.

Removed from active plugin skills:

```text
capturing-workflow
caveman-commit
code-quality-principles
debugging-work
discovering-context
frontend-design
grill-me
intent
karpathy-guidelines
planning-work
playwright-cli
pnpm-audit-fix
routing-work
vercel-composition-patterns
vercel-react-best-practices
verifying-work
web-design-guidelines
```

Keep active:

```text
audit-fix
backend-engineer
browser-proof
caveman
code-review
commit-planner
debug-discipline
devops-engineer
engineering-discipline
frontend-engineer
handoff
implementation-plan
intent-interview
intent-preflight
learning-loop
product-designer
tdd
verification-discipline
```

Keep future cleanup biased toward fewer active skills. Add back a deleted skill only if it changes behavior better than the v2 core, not because the old text is available.
