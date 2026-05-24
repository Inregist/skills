---
name: create-skill
description: Design or revise agent skills as behavior-shaping protocols. Use when creating a new skill, improving an existing skill, turning principles into agent habits, or deciding whether knowledge belongs in a skill at all.
---

# Create Skill

Build skills that activate judgment, not encyclopedias.

## Mindset

A skill should make the agent enter the right working posture at the right time. Assume the agent already knows common concepts such as SOLID, DRY, YAGNI, accessibility, testing, and design patterns. The skill's job is to make those ideas present during execution: when to put on the hat, how to think, what boundaries not to cross, and what proof earns trust.

## Quick Start

1. Gather the task/domain, concrete use cases, and any reference material.
2. Decide whether the skill needs instructions only, references, scripts, or assets.
3. Name the behavior the skill should activate.
4. Write the trigger description first; this is the invocation surface.
5. Define the posture in one or two sentences.
6. Add concrete heuristics and failure guards.
7. Add output or verification expectations only when they change behavior.
8. Keep `SKILL.md` compact; move rare detail to one-level references.

## Trigger Description

The description is the main routing surface. Make it specific enough that the agent knows when to load the skill.

- Max 1024 characters.
- Write in third person.
- First sentence: what the skill does.
- Second sentence: `Use when...` with concrete triggers, task types, domains, files, or user phrases.

## Skill Anatomy

Use this shape unless the repo already has a stronger local convention:

```markdown
---
name: <skill-name>
description: <Use when... trigger surface>
---

# <Skill Name>

<One-sentence purpose>

## Mindset / Quick Start / Heuristics / Avoid / Output

<Use only sections that change behavior.>
```

## Good Skill Content

- Activation rules: when this skill should run.
- Posture: maintainer, reviewer, debugger, designer, operator, interviewer.
- Constraints: what the agent may not do without evidence or permission.
- Heuristics: short questions that guide judgment.
- Proof obligations: tests, screenshots, citations, reproduction, or explicit residual risk.
- Scripts for deterministic repeated work, validation, formatting, or fragile operations.
- References for detailed docs, schemas, examples, or rare advanced cases.

## Weak Skill Content

- Definitions the model already knows.
- Long explanations of broad principles.
- Generic advice like "be careful" or "write clean code."
- One-off incident rules that do not generalize.
- Huge checklists that will crowd out task context.
- Time-sensitive facts that will go stale.

## Files

Default layout, with optional folders only when needed:

```text
skill-name/
  SKILL.md
  references/topic.md
  scripts/helper.sh
  assets/
```

- `references/`: detail is rare, distinct by domain, or would push `SKILL.md` past about 100 lines.
- `scripts/`: work is deterministic, repeatedly generated, or needs consistent error handling.
- `assets/`: templates, images, fixtures, or boilerplate used as output material.

## Review Gate

Before adding or changing a skill, check:

- Would this change what the agent does, or only describe what it knows?
- Is the trigger specific enough to fire at the right time?
- Are the rules short enough to stay present during real work?
- Is there an allowed exception for any strong constraint?
- Are references one level deep from `SKILL.md`?
- Are scripts used only for deterministic repeated work?
- Does this belong in an existing skill instead of a new one?
