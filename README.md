# Inregist Skills

Shared low-token workflow skills for agents.

The catalog is gate-based, not a mandatory lifecycle. Load a skill only when it changes the next action.

This repo is the source of truth for skills. Update skills on one machine, push to Git, pull on another machine, then restart the agent.

## Layout

```text
.codex-plugin/
  plugin.json        # lets Codex load ./skills/
skills/
  caveman-commit/
    SKILL.md
  capturing-workflow/
    SKILL.md
  debugging-work/
    SKILL.md
  discovering-context/
    SKILL.md
  grill-me/
    SKILL.md
  intent/
    SKILL.md
  planning-work/
    SKILL.md
  routing-work/
    SKILL.md
  verifying-work/
    SKILL.md
```

Current spine:

```text
intent
routing-work
discovering-context
grill-me
planning-work
debugging-work
verifying-work
capturing-workflow
```

Explicit-only tools:

```text
caveman-commit
```

Direct action, review, commit messages, and closeout are normal agent behavior unless a specialized skill is explicitly useful or explicitly invoked.

Add each new skill as a direct child of `skills/`:

```text
skills/
  my-skill/
    SKILL.md
    references/
    scripts/
```

Each `SKILL.md` needs YAML frontmatter with at least `name` and `description`.

## Workflow

1. Edit or add skills under `skills/`.
2. Commit and push.
3. Pull the repo on another machine.
4. Restart the agent.

## Skill Template

```md
---
name: my-skill
description: Use when ...
---

# My Skill

Write the workflow here.
```

Keep skills portable. Agent-specific files such as `.codex-plugin/plugin.json` are only adapters that point agents at `./skills/`.
