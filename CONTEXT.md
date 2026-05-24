# Skills Catalog

This context defines the shared language for a public repository of reusable agent skills. The repo's job is to make skills easy to write, share, pull, and use across machines while keeping the active catalog small.

## Language

**Skills Catalog**:
A public repository containing one or more reusable agent skills.
_Avoid_: Package manager, marketplace package

**Skill**:
A reusable workflow instruction rooted at a directory containing `SKILL.md`.
_Avoid_: Prompt, rule, playbook

**Universal Skill**:
A skill intended to be usable by multiple agents without depending on one agent's plugin manifest.
_Avoid_: Codex skill, Claude skill

**Plugin Adapter**:
Minimal agent-specific metadata that points an agent at the **Skills** directory.
_Avoid_: Skill source

**Behavior Spine**:
The small core set of skills that shape ordinary agent behavior: understand intent, expose multi-step work, code maintainably, prove claims, and learn repeated lessons.
_Avoid_: Framework, mandatory ceremony, heavy router

## Relationships

- A **Skills Catalog** contains one or more **Skills**.
- A **Skill** may be a **Universal Skill** when it avoids agent-specific packaging assumptions.
- A **Plugin Adapter** exists only to make an agent load the repository's **Skills**.
- The **Behavior Spine** provides the default reusable workflow; role and validation skills remain optional tools selected only when they change the next action.
- The normal update workflow is Git: edit, commit, push, pull, restart the agent.

## Example dialogue

> **Dev:** "If I update a skill on machine A, how does machine B get it?"
> **Domain expert:** "Pull the **Skills Catalog** on machine B and restart the agent."

> **Dev:** "Is this repo a plugin?"
> **Domain expert:** "No. It is a **Skills Catalog**. Plugin files are just **Plugin Adapters**."

## Flagged ambiguities

- "plugin" was used to describe both skill source and installation packaging. Resolved: the repository is a **Skills Catalog**; plugin files are **Plugin Adapters**.
