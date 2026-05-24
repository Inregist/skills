---
name: implementation-plan
description: Convert clarified intent into visible, implementable tasks with a bias toward the first working vertical slice. Use when work spans multiple files, dependencies, steps, risks, or agents; when MVP/PRD work needs a release-critical workflow before scaffolding; when the human needs TUI-visible progress; or when a third-party agent should be able to implement from the plan.
---

# Implementation Plan

Plan enough for a teammate to implement without guessing.

## Quick Start

1. State the goal in one sentence.
2. List constraints and non-goals.
3. For MVP/PRD work, pick the first release-critical vertical slice before package or architecture expansion.
4. Identify files, modules, or systems likely to change.
5. Break work into dependency-ordered tasks.
6. Add acceptance criteria and verification for each task.
7. Create or update the visible TUI task plan before editing.

## Task Quality

Good tasks are:

- visible to the human;
- ordered by dependency;
- small enough to verify;
- large enough to produce meaningful behavior;
- explicit about files/areas and checks;
- free of unrelated cleanup.

Avoid placeholder tasks like "handle edge cases" unless the edge cases are named.

For MVP or broad product goals, apply [vertical-slice-rule.md](vertical-slice-rule.md) before planning sideways.

## Output

```text
Goal:
Plan:
1. <task> -> acceptance: <criteria> -> verify: <check>
2. <task> -> acceptance: <criteria> -> verify: <check>
Risks:
Start:
```

Next action: update the visible task plan, then execute the first task.
