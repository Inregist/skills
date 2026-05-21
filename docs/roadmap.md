# Roadmap

## Milestone 0: Repair Current State

- [ ] Remove stale empty `executing-work` directory.
- [ ] Keep `karpathy-guidelines` as the ACT anti-slop gate.
- [ ] Validate plugin.
- [ ] Low-thinking subagent dogfood: slop-prone execution routes to `karpathy-guidelines`.
- [ ] Commit fix.

## Milestone 1: Stable V1 Spine

Core spine:

```text
intent
routing-work
discovering-context
grill-me
planning-work
karpathy-guidelines
debugging-work
verifying-work
capturing-workflow
```

Explicit-only tools:

```text
caveman-commit
```

Rule: one primary skill max unless the next action clearly needs support.

## Milestone 2: Domain Support Map

Frontend/backend specialists are not core spine.

```text
frontend build/review -> frontend-engineer / frontend-design / React / web-design skills
backend/API/db -> backend-engineer
browser proof -> playwright-cli
dependency audit -> pnpm-audit-fix when explicitly invoked
quality review -> code-quality-principles
```

Selected frontend/backend specialists are copied into this catalog. Other specialists stay installed-only unless repeated use justifies owning them here.

## Milestone 3: Real-Use Dogfood

Use the spine in real tasks:

- small edit;
- bug fix;
- slop-prone implementation.

Capture failures. Change the spine only after repeated pain.

## Milestone 4: Publish And Sync

- [ ] Push repo.
- [ ] Pull on another machine.
- [ ] Restart agent.
- [ ] Confirm skill list loads.

## Core Coding Standard

Readability and simplicity are first-class goals.

Use `karpathy-guidelines` when coding work risks slop:

- smallest readable change;
- every changed line traces to the user goal;
- existing primitives before new helpers;
- no speculative abstraction;
- concrete proof before completion claim.
