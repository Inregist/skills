# Yeehaw Skills

Agent coaching skills for real engineering work.

Yeehaw treats the agent like an engineer learning company habits. The goal is not a rigid workflow. The goal is behavior shaping: understand intent, use evidence, make work visible, code maintainably, prove claims, and learn from repeated mistakes.

## Philosophy

Good agent behavior:

- understand vague human intent before acting;
- inspect repo evidence before asking;
- interview when work is big, ambiguous, or costly;
- expose multi-step work in the TUI so the human can steer;
- code small, readable, maintainable changes;
- use tests, lint, typecheck, browser checks, and other system feedback;
- report work before committing;
- capture repeated mistake classes without bloating rules.

The human is the tech lead and product owner. Skills are coaching, role ownership, guardrails, review habits, and compact memory.

## Core Shape

Core skills:

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

Role skills:

```text
frontend-engineer
backend-engineer
product-designer
devops-engineer
```

Validation skills:

```text
tdd
browser-proof
code-review
```

Explicit tools:

```text
caveman
commit-planner
audit-fix
```

See [docs/skill-architecture-v2.md](docs/skill-architecture-v2.md) for the migration map from the old catalog.

## Migration Status

V2 is the active plugin surface. Superseded v1 workflow and reference-heavy skills were removed from `skills/` to reduce trigger noise. Git history remains the archive for deleted source material.

Next work:

1. Dogfood the v2 triggers against real coding work.
2. Tighten descriptions when invocation misses happen.
3. Add rules only for repeated mistake classes.
4. Refresh the installed plugin after an approved commit.

## How It Works

Start with `intent-preflight` for non-trivial work. It chooses the next behavior:

| Situation | Behavior |
| --- | --- |
| Clear, tiny, reversible | Direct action |
| Repo/docs/tests can answer | Inspect evidence |
| Big, vague, costly, or ambiguous | `intent-interview` |
| Clear multi-step implementation | `implementation-plan` |
| Coding/refactor risk | `engineering-discipline` |
| Bug/failure/regression | `debug-discipline` |
| Completion claim | `verification-discipline` |
| Repeated mistake pattern | `learning-loop` |
| Session transfer | `handoff` |

Do not load every relevant skill. Load the one skill that changes the next action.

## Skill Rules

Use the `write-a-skill` structure:

- frontmatter description is the invocation surface;
- description must include specific `Use when...` triggers;
- `SKILL.md` should stay under 100 lines;
- split rarely needed detail into one-level reference files;
- add scripts only for deterministic repeated work.

Add a skill only when it changes agent behavior. Do not add one rule per incident. Capture repeated mistake classes.

## Current Layout

```text
.codex-plugin/
  plugin.json
skills/
  <skill-name>/
    SKILL.md
docs/
  skill-architecture-v2.md
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
description: Does a specific capability. Use when specific triggers apply.
---

# My Skill

## Quick Start

Describe the shortest workflow that changes the next action.
```

Good skills are short, specific, and trigger narrowly.
