---
name: example-skill-name
description: Use when the user asks for work that needs this skill's specific workflow, standards, references, or tools.
---

# Example Skill Name

## When To Use

Use this skill when the task needs the specific guidance this skill provides. Keep the trigger clear and concrete so Claude Code and Codex can decide when to load it.

## Workflow

1. Read only the references needed for the current task.
2. Follow the project conventions before introducing new patterns.
3. Use bundled scripts or assets when they provide deterministic results.
4. Validate the output with the most relevant local check.

## Resources

- `references/`: Optional detailed docs to read only when needed.
- `scripts/`: Optional helper scripts for repeatable operations.
- `assets/`: Optional templates, images, or other files used in outputs.

## Validation

Before finishing, verify that the work followed this skill's workflow and that any generated or edited artifacts match the user's request.
