---
name: intent
description: Understand the user's real intent before choosing what task to perform. Use when the user says intent, "understand my intent", "think first", "don't blindly ask", or when the request may be solved at the wrong level.
---

# Intent

Before acting, decide what problem the user is really asking you to solve.

1. Infer the intended outcome, not just the literal instruction.
2. Check whether the request is about creating, changing, explaining, diagnosing, or deciding.
3. Use available context, code, and docs before asking.
4. If multiple intents are plausible, choose the one best supported by context.
5. Ask only when choosing wrong would waste work or violate the user's goal.

If you ask, ask one direct question and include the recommended default. Prefer the smallest concrete action that satisfies the inferred intent. Use this skill before narrower workflow skills that might pull the task off target.
