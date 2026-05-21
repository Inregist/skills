# Reverse Engineering Superpowers

This note reverse engineers Superpowers through the lens of this repo's goal: keep reusable workflow discipline, but avoid a token-heavy always-on methodology.

## Intent Filter

The target is not a clone of Superpowers.

The target is a small **Skills Catalog** that:

- keeps skills as plain `skills/*/SKILL.md` files;
- uses Git for update and sync;
- loads only the workflow needed for the task;
- keeps high-cost rituals opt-in;
- treats plugin files as thin **Plugin Adapters** only.

## What Superpowers Is

Superpowers has two layers:

1. **Adapter and distribution layer**
   - Agent-specific plugin manifests.
   - Marketplace/install instructions.
   - Skill loading metadata.
   - In newer versions, a split between plugin shim and skills repository.

2. **Methodology layer**
   - A set of composable skills for brainstorming, planning, TDD, debugging, subagent execution, code review, worktrees, and branch finishing.
   - A bootstrap skill that tells the agent to check and invoke relevant skills before work.
   - Several hard gates that force design, planning, verification, and review steps.

The value is mostly in the methodology layer. The distribution layer is useful only if you need marketplace install, auto-update, or cross-agent packaging.

## Basic Workflow Model

Superpowers' public workflow is roughly:

1. brainstorm before code;
2. create or verify an isolated worktree;
3. write a detailed implementation plan;
4. execute the plan inline or with subagents;
5. use TDD during implementation;
6. request code review between tasks;
7. finish the branch with verification and a merge/PR decision.

This is coherent for large feature work. It is too much for small fixes, small repo edits, or quick skill authoring.

## Token Cost Sources

The token cost does not mainly come from the plugin manifest. It comes from behavior.

- **Broad activation rules**: the bootstrap skill says to invoke relevant skills before any response or action, with a very low threshold.
- **Large skill bodies**: the local cached Superpowers copy has about 16.6k words across top-level `SKILL.md` files before supporting references and prompt templates.
- **Mandatory gates**: brainstorming, design approval, spec writing, plan writing, review, and finishing steps can all trigger additional context.
- **Subagent loops**: subagent-driven development can run implementer, spec reviewer, and code quality reviewer loops per task.
- **Supporting prompts**: implementer/reviewer templates add more context when subagents are used.
- **Persuasion language**: many skills spend tokens preventing the agent from rationalizing shortcuts.

Superpowers' own skill-writing guidance acknowledges this cost: frequently loaded skills should be tiny, details should move to references or command help, and force-loading references burns context early.

## What To Keep

Keep these ideas:

- **Skills as workflow modules**: one directory, one `SKILL.md`, optional references/scripts.
- **Strong triggers**: descriptions should say when to load a skill, not summarize the workflow.
- **Progressive disclosure**: keep details in separate files and read them only when needed.
- **Evidence gates**: do not claim success without a fresh verification command.
- **One-question design pressure**: when requirements are fuzzy, ask one high-value question at a time.
- **Subagents for true parallelism**: use them when work is independent or review needs fresh context.
- **Git as sync layer**: edit, commit, push, pull, restart.

## What To Drop

Drop or weaken these ideas for this repo:

- always checking for skills before every response;
- mandatory brainstorming for trivial changes;
- mandatory design docs and committed specs for every task;
- default subagent-driven development;
- mandatory review after every small task;
- auto-update infrastructure;
- plugin-manager behavior;
- marketplace compatibility as a first-order design goal;
- long motivational or persuasion sections.

## Smaller Architecture

Use a three-tier workflow:

### Tier 0: Default Agent Behavior

For simple questions and small edits:

- inspect relevant files;
- make the change;
- run the smallest useful verification;
- summarize.

No skill load unless the user names one or the task clearly matches a high-value trigger.

### Tier 1: Focused Workflow Skill

For recurring medium-complexity work:

- load exactly one skill;
- follow its short checklist;
- open references only if the checklist says they are needed.

Current focused skills include:

- `debugging-work`
- `planning-work`
- `verifying-work`
- `verifying-work`
- `capturing-workflow`

### Tier 2: Heavy Process

For large, risky, or ambiguous work:

- use planning;
- optionally create docs;
- optionally dispatch subagents;
- run broader verification.

This tier should be explicit: user asks for it, or the task is clearly too broad/risky for Tier 1.

## Proposed Trigger Policy

Use skills when one of these is true:

- the user names the skill;
- the task matches a narrow trigger in skill frontmatter;
- the task has repeated past failure modes that the skill prevents;
- the task is high-risk enough that a small process cost is justified.

Do not use skills just because there is a 1% chance one might apply.

## Proposed Word Budgets

- Startup or always-visible instructions: 100-200 words total.
- Frequently used skill: 200-500 words.
- Specialized skill: 500-900 words.
- Heavy reference: separate file, loaded only on demand.

If a skill needs more than 900 words, split it into:

- short `SKILL.md`;
- one or more `references/*.md`;
- optional `scripts/*` for mechanical work.

## Current Workflow Spine

The catalog now implements a lightweight **Workflow Spine**. It is gate-based, not a mandatory lifecycle:

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

Direct action, review, and closeout remain normal agent behavior unless a specialized skill is explicitly useful.

Optional heavy skills such as subagent orchestration and worktree management should wait until repeated real use proves they are worth the extra process cost.

## Design Principle

Superpowers optimizes for disciplined autonomous software development.

This catalog should optimize for **low-token reusable judgment**: small workflow modules that correct predictable agent failures without turning every task into a full methodology run.
