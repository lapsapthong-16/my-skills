# My Skills

Personal AI-agent skills for Claude Code and Codex.

This repository is the source of truth for reusable skills. Keep skill source files here, then install selected skills into whichever agent you are using. By default, install skills globally so application repositories do not get extra generated files.

## Repository Layout

```text
.
├── skills/
│   └── <skill-name>/
│       ├── SKILL.md
│       ├── references/
│       ├── scripts/
│       └── assets/
└── templates/
    └── skill/
        ├── SKILL.md
        ├── references/
        ├── scripts/
        └── assets/
```

The portable contract is:

- One skill per `skills/<skill-name>/` directory.
- Skill directory names use kebab-case, for example `api-review`.
- Every skill has a `SKILL.md`.
- Default skills use portable frontmatter with `name` and `description`.
- Optional supporting files live inside the skill directory.

## Add A New Skill

1. Pick a kebab-case skill name:

   ```bash
   export SKILL_NAME=api-review
   ```

2. Copy the template:

   ```bash
   mkdir -p "skills/$SKILL_NAME"
   cp -R templates/skill/. "skills/$SKILL_NAME/"
   ```

3. Edit `skills/<skill-name>/SKILL.md`:

   ```md
   ---
   name: api-review
   description: Use when reviewing API design, request/response contracts, versioning, or compatibility risks.
   ---

   # API Review

   ## When To Use

   Use this skill when ...
   ```

4. Add only the resources the skill needs:

   - `references/` for detailed docs that should be read only when relevant.
   - `scripts/` for repeatable helper scripts.
   - `assets/` for templates, images, fixtures, or other files used in outputs.

5. Commit and push the skill:

   ```bash
   git add skills/<skill-name>
   git commit -m "Add <skill-name> skill"
   git push
   ```

## Install Skills Globally

Global installation is the recommended default. It installs skills into the agent's user-level skill directory instead of the current project.

Install one skill for both Claude Code and Codex:

```bash
npx skills add lapsapthong-16/my-skills \
  --skill api-review \
  --agent claude-code \
  --agent codex \
  --global
```

Install multiple skills:

```bash
npx skills add lapsapthong-16/my-skills \
  --skill api-review \
  --skill frontend-design \
  --agent claude-code \
  --agent codex \
  --global
```

Short flags may also work depending on the installer version:

```bash
npx skills add lapsapthong-16/my-skills -s api-review -a claude-code -a codex -g
```

Restart Claude Code or Codex after installing new skills so the agent reloads available skill metadata.

## External Skills

Some skills are installed directly from upstream projects instead of stored in this repository. Track those install commands in [EXTERNAL-SKILLS.md](./EXTERNAL-SKILLS.md).

## Import Skills For A Project

Prefer global installation and document project expectations in the project README:

````md
This project uses skills from lapsapthong-16/my-skills:

- api-review
- frontend-design

Install them globally:

```bash
npx skills add lapsapthong-16/my-skills -s api-review -s frontend-design -a claude-code -a codex -g
```
````

If a project needs local skill folders, keep Git behavior explicit.

For local-only excludes that do not affect teammates:

```bash
printf ".claude/skills/\n.codex/skills/\n" >> .git/info/exclude
```

For a team-wide rule, add this to the project `.gitignore`:

```gitignore
.claude/skills/
.codex/skills/
```

Only commit `.claude/skills/` or `.codex/skills/` when the project intentionally vendors the skill source and the team agrees to maintain those copies.

## Cross-Agent Compatibility

Portable skills should start with only:

```md
---
name: skill-name
description: Use when ...
---
```

Keep the description trigger-oriented. It should describe when the agent should load the skill, not just what the skill is called.

Avoid agent-specific metadata in default skills. If a skill intentionally depends on Claude Code-only or Codex-only behavior, say so in the description:

```md
---
name: claude-release-helper
description: Use in Claude Code only when preparing release notes with Claude-specific command behavior.
---
```

## Skill Quality Checklist

Before committing a skill:

- The directory name is kebab-case.
- `SKILL.md` has `name` and `description` frontmatter.
- The description clearly says when to use the skill.
- The body is concise and procedural.
- Large reference material lives in `references/`, not directly in `SKILL.md`.
- Scripts are included only when they make repeated work safer or more deterministic.
- Agent-specific behavior is clearly labeled.
