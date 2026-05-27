## 1. Repository Structure

- [x] 1.1 Create the canonical `skills/` directory for reusable skill folders.
- [x] 1.2 Create a template skill directory at `templates/skill/` with a portable `SKILL.md` starter.
- [x] 1.3 Add placeholder structure or documentation for optional per-skill `references/`, `scripts/`, and `assets/` directories.

## 2. Documentation

- [x] 2.1 Create `README.md` explaining the repository purpose and cross-agent compatibility model.
- [x] 2.2 Document how to add a new skill under `skills/<skill-name>/SKILL.md`.
- [x] 2.3 Document global installation with `npx skills add` for Claude Code and Codex.
- [x] 2.4 Document project-specific import options and Git-safe excludes for `.claude/skills/` and `.codex/skills/`.
- [x] 2.5 Document when agent-specific skill metadata is allowed and how to label those skills clearly.

## 3. Validation

- [x] 3.1 Verify every example skill path uses kebab-case directory names.
- [x] 3.2 Verify every `SKILL.md` example contains portable `name` and `description` frontmatter.
- [x] 3.3 Run `git status --short` and confirm the created files are limited to the intended repository setup and OpenSpec change artifacts.
