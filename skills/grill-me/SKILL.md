---
name: grill-me
description: Stress-test an idea, plan, or design through focused questioning. Use when the user asks to be grilled, wants design pressure, or the work is ambiguous enough that building the wrong thing is likely. Enable docs mode only when project language, ADRs, existing behavior, or durable decisions matter.
---

# Grill Me

Interrogate the design until the next action is clear.

## Loop

1. Use `discovering-context` if files or docs can answer first.
2. Ask one question at a time.
3. Include your recommended answer.
4. Test trade-offs, edge cases, constraints, and failure modes.
5. Resolve one branch before opening the next.
6. Stop when the design is accepted or the next action is obvious.

## Docs Mode

Use docs mode only when domain terms, `CONTEXT.md`, ADRs, existing behavior, or durable decisions matter.

1. Read relevant docs and code before asking.
2. Call out term conflicts immediately.
3. If code contradicts the user or docs, surface the contradiction.
4. Update `CONTEXT.md` only when a domain term is resolved.
5. Offer an ADR only when the decision is hard to reverse, surprising, and trade-off driven.

## Output

- decision reached;
- docs updated, if any;
- recommendation;
- remaining risk;
- next action: `planning-work` or direct action.

Do not turn this into a long interview when a small decision unlocks the work.
