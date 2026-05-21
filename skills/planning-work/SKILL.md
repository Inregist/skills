---
name: planning-work
description: Turn an accepted design or clear multi-step task into executable work. Use when implementation spans multiple files, dependencies, steps, risks, or agents and needs ordering before editing.
---

# Planning Work

Plan only enough to execute without drift.

## Gate

Use this after intent/design is clear. If the design is still fuzzy, use `grill-me` first.

## Plan Shape

1. State the goal in one sentence.
2. List constraints and non-goals that affect implementation.
3. Map files or modules likely to change.
4. Split work by dependency order.
5. For each task, define:
   - outcome;
   - files or areas;
   - verification check;
   - whether TDD, review, or subagents are justified.
6. Identify the first executable task.

## Task Quality

Good tasks are:

- small enough to verify;
- large enough to produce meaningful behavior;
- ordered so earlier tasks unblock later tasks;
- scoped to avoid unrelated refactors;
- explicit about tests or manual checks.

Avoid artificial 2-minute tasks, placeholder steps, and plans that say “handle edge cases” without naming the edge case.

## Output

```text
Goal: <one sentence>
Plan:
1. <task> -> verify: <check>
2. <task> -> verify: <check>
Risks: <specific risks>
Start with: <first task>
```

Next action is the first executable task, or `using-subagents` only when tasks are genuinely independent.
