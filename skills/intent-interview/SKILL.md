---
name: intent-interview
description: Interview the user and inspect evidence to transfer big or ambiguous intent into usable context. Use when work feels large, product/design/architecture ambiguity exists, wrong work would be expensive, the user is thinking aloud, or repo docs/domain language may affect the decision.
---

# Intent Interview

Use this to turn fuzzy intent into implementation-ready context.

## Quick Start

1. If inside a repo, inspect relevant docs/code before asking.
2. Ask one question at a time.
3. Include your recommended answer.
4. Resolve one decision branch before opening another.
5. Stop when the next action is clear enough to plan or execute.

## Interview Targets

- Goal: what outcome matters?
- User/workflow: who is affected and how?
- Constraints: what must stay true?
- Non-goals: what should not be built?
- Evidence: what do docs/code/tests already say?
- Risk: what would make wrong work expensive?

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
