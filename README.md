# Yeehaw Skills

Low-token workflow skills for coding agents.

This repo is a portable skill catalog. It exists to make agents less likely to do confident wrong work without loading a heavy process by default.

## Why

General agents often fail in predictable ways:

- misunderstand the real intent;
- ask questions instead of inspecting code;
- plan forever but execute poorly;
- overbuild simple changes;
- fix symptoms without root cause;
- claim "done" without evidence;
- lose context between sessions.

Superpowers-style workflows help because they add process gates. They also cost a lot of tokens. This repo keeps the useful part: small skills that load only when they change the next action.

## What

The catalog is gate-based, not a mandatory lifecycle.

```text
INTENT  -> understand the real job
ROUTE   -> choose the smallest safe path
CONTEXT -> gather facts only when facts change action
DECIDE  -> resolve costly ambiguity
ACT     -> make the scoped change
PROVE   -> match evidence to the claim
CLOSE   -> report state, risk, next step
CAPTURE -> turn repeated patterns into skills
```

Most work should not load every gate. The right path is the smallest path that can succeed.

## Agent Quick Start

When using this catalog on a task:

1. If the request may be solved at the wrong level, use `intent`.
2. If work is non-trivial, use `routing-work`.
3. Pick `FAST`, `DISCIPLINE`, or `HEAVY`.
4. Load zero or one primary skill.
5. Execute the smallest useful slice.
6. Before claiming completion, use evidence that matches the claim.

Default posture:

```text
clear + tiny       -> act directly
clear + risky      -> one focused gate
unclear + costly   -> discover context first
done/fixed/ready   -> prove with fresh evidence
```

## How It Works

`routing-work` classifies work into one of three modes:

- `FAST`: clear, low-risk, reversible. Act directly, verify lightly.
- `DISCIPLINE`: clear task with one likely failure mode. Load one focused skill.
- `HEAVY`: ambiguous, risky, broad, or design-heavy. Discover context first, then decide or plan.

Rule: prefer zero or one primary skill. Add support skills only when crossing a real boundary.

Examples:

```text
small safe edit        -> FAST
bug/failure           -> debugging-work
slop-prone coding     -> karpathy-guidelines
test-first behavior   -> tdd
frontend feature      -> frontend-engineer
backend/API/data      -> backend-engineer
completion claim      -> verifying-work
session transfer      -> handoff
```

## Decision Table

| Situation | Primary skill |
| --- | --- |
| Vague, frustrated, or wrong-level request | `intent` |
| Non-trivial work after intent is clear | `routing-work` |
| Need facts from repo/docs before acting | `discovering-context` |
| Costly design ambiguity | `grill-me` |
| Clear multi-step implementation | `planning-work` |
| Slop-prone coding or refactor | `karpathy-guidelines` |
| Bug, failure, regression, unexplained behavior | `debugging-work` |
| Explicit test-first behavior change | `tdd` |
| Frontend feature/review | `frontend-engineer` |
| Backend/API/data feature/review | `backend-engineer` |
| Browser/UI proof | `playwright-cli` |
| Completion claim | `verifying-work` |
| Session transfer | `handoff` |
| Repeated workflow worth reusing | `capturing-workflow` |

## Failure Mode Map

| AI failure | Tripwire |
| --- | --- |
| Solves literal ask but misses real goal | `intent` |
| Loads too much process | `routing-work` |
| Asks instead of inspecting available context | `discovering-context` |
| Designs before terms are clear | `grill-me` |
| Writes broad plan but no execution path | `planning-work` |
| Overbuilds helpers or abstractions | `karpathy-guidelines` |
| Fixes symptom without root cause | `debugging-work` |
| Implements behavior without early feedback | `tdd` |
| Says done without proof | `verifying-work` |
| Loses state across sessions | `handoff` |

## Why It Is Useful

The useful pieces are:

- `intent`: stops wrong-level work before it starts.
- `routing-work`: prevents loading too much process.
- `karpathy-guidelines`: keeps coding surgical, readable, and scoped.
- `debugging-work`: forces root cause before fixes.
- `tdd`: catches behavior slop with red-green feedback.
- `verifying-work`: makes "done" mean evidence-backed.
- `handoff`: transfers state to another session without replaying the full chat.
- `caveman`: keeps communication compressed when tokens matter.

This is not a magic quality system. It is a set of tripwires around common AI failure modes.

## Non-Goals

This repo is not:

- a full Superpowers clone;
- a mandatory step-by-step lifecycle;
- a reason to load every relevant skill;
- a generic code-quality guarantee;
- a substitute for tests, browser checks, or human product judgment.

Important boundaries:

- `tdd` catches behavior slop, not visual or architecture problems.
- `verifying-work` proves final claims; it is not replaced by TDD.
- `debugging-work` comes before TDD when the root cause is unknown.
- `caveman`, `handoff`, `caveman-commit`, and `pnpm-audit-fix` are explicit-use tools.

## Skill Map

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
caveman
caveman-commit
handoff
pnpm-audit-fix
```

Domain/support skills:

```text
frontend-engineer
backend-engineer
frontend-design
vercel-composition-patterns
vercel-react-best-practices
web-design-guidelines
playwright-cli
tdd
code-quality-principles
```

## Current Layout

```text
.codex-plugin/
  plugin.json
skills/
  <skill-name>/
    SKILL.md
```

Some skills include optional `references/`, `rules/`, or helper files. Load those only when the skill says they are needed.

## Use

As a Codex plugin, `.codex-plugin/plugin.json` points Codex at `./skills/`.

Codex installs plugins from a marketplace, not directly from a plugin root. This repo is currently a plugin root. To install it, either use a local marketplace wrapper or publish it inside a marketplace repo.

### Install From Local Checkout

Clone or keep this repo somewhere stable:

```bash
git clone https://github.com/inregist/skills ~/work/inregist/skills
```

Create a local marketplace wrapper:

```bash
mkdir -p ~/.agents/marketplaces/personal/plugins
ln -s ~/work/inregist/skills ~/.agents/marketplaces/personal/plugins/yeehaw
mkdir -p ~/.agents/marketplaces/personal/.agents/plugins
```

Create `~/.agents/marketplaces/personal/.agents/plugins/marketplace.json`:

```json
{
  "name": "personal",
  "interface": {
    "displayName": "Personal"
  },
  "plugins": [
    {
      "name": "yeehaw",
      "source": {
        "source": "local",
        "path": "./plugins/yeehaw"
      },
      "policy": {
        "installation": "AVAILABLE",
        "authentication": "ON_INSTALL"
      },
      "category": "Coding"
    }
  ]
}
```

Install:

```bash
codex plugin marketplace add ~/.agents/marketplaces/personal
codex plugin add yeehaw --marketplace personal
```

Restart Codex so the skills load.

### Install From GitHub Marketplace

For direct GitHub install, publish a marketplace repo with this shape:

```text
repo/
  .agents/
    plugins/
      marketplace.json
  plugins/
    yeehaw/
      .codex-plugin/
        plugin.json
      skills/
        ...
```

The marketplace file should point at `./plugins/yeehaw`:

```json
{
  "name": "yeehaw",
  "interface": {
    "displayName": "Yeehaw"
  },
  "plugins": [
    {
      "name": "yeehaw",
      "source": {
        "source": "local",
        "path": "./plugins/yeehaw"
      },
      "policy": {
        "installation": "AVAILABLE",
        "authentication": "ON_INSTALL"
      },
      "category": "Coding"
    }
  ]
}
```

Then install from GitHub:

```bash
codex plugin marketplace add owner/repo --ref main
codex plugin list --marketplace yeehaw
codex plugin add yeehaw --marketplace yeehaw
```

Update later:

```bash
codex plugin marketplace upgrade yeehaw
```

Normal sync flow:

1. Edit or add skills under `skills/`.
2. Validate the plugin shape.
3. Commit and push.
4. Pull on another machine.
5. Restart the agent so the skill list reloads.

Local validation used for this repo:

```bash
rtk python3 /home/inregist/.codex/skills/.system/plugin-creator/scripts/validate_plugin.py .
```

## Add A Skill

Add each new skill as a direct child of `skills/`:

```text
skills/
  my-skill/
    SKILL.md
    references/
    scripts/
```

Minimum `SKILL.md`:

```md
---
name: my-skill
description: Use when ...
---

# My Skill

Write the workflow here.
```

Good skills are short, specific, and trigger narrowly. Do not add a skill just because it might be useful. Add one when repeated use proves it changes agent behavior.

## Not Included By Default

Some installed skills are useful but intentionally not owned by this catalog yet:

- `systematic-debugging`: heavier debugging reference; current default is compact `debugging-work`.
- `improve-codebase-architecture`: heavy architecture review; useful only when explicitly doing architecture work.

See `docs/roadmap.md`, `docs/workflow-skills-checklist.md`, and `docs/installed-skills-audit.md` for current decisions.
