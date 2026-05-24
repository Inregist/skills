---
name: intent-interview
description: Turn fuzzy intent into usable constraints with the fewest high-leverage questions. Use when the user is thinking aloud, shaping principles or working style, asking how to approach something, product/design/architecture ambiguity exists, wrong work would be expensive, or repo docs/domain language may affect the decision.
---

# Intent Interview

พูดน้อยต่อยหนัก: ask less, land harder.

## Quick Start

1. If inside a repo, inspect relevant docs/code before asking.
2. State the strongest current read of the user's intent.
3. Ask at most one question unless multiple answers are truly blocking.
4. Include your recommended answer or default direction.
5. Convert the answer into constraints, non-goals, or next action.
6. Stop as soon as the next move is clear enough to plan or execute.

## Interview Targets

- Goal: what outcome matters?
- Taste: what working style or principle should shape the result?
- User/workflow: who is affected and how?
- Constraints: what must stay true?
- Non-goals: what should not be built?
- Evidence: what do docs/code/tests already say?
- Risk: what would make wrong work expensive?

## Question Quality

Ask questions that change the work. Avoid broad discovery, questionnaires, or asking for facts repo evidence can answer.

Good:

```text
My read: you want this skill to act like an operating principle, not a tutorial. Should it optimize for strict trigger reliability or compactness?
```

Weak:

```text
Can you tell me more about what you want?
```

## Docs Mode

Docs mode is default when repo language, ADRs, existing behavior, or durable decisions matter.

- Read relevant `CONTEXT.md`, ADRs, docs, tests, or code first.
- Surface contradictions between user intent and repo evidence.
- Update durable docs only after the user accepts the decision.

## Output

```text
Goal:
Decisions:
Constraints:
Non-goals:
Evidence:
Risks:
Next:
```
