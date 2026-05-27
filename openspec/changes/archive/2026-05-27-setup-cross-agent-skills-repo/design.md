## Context

The repository is an empty GitHub clone intended to become the source of truth for reusable agent skills. The skills need to work across Claude Code and Codex, so the repository should avoid tool-specific assumptions where possible and keep tool-specific behavior in documentation or install commands rather than in the skill source format.

Claude Code and Codex both use folder-based skills with a required `SKILL.md`. The stable shared contract is therefore a `skills/<skill-name>/SKILL.md` layout, with optional `references/`, `scripts/`, and `assets/` folders inside each skill when a skill needs more than instructions.

## Goals / Non-Goals

**Goals:**
- Establish a clear repository layout for reusable cross-agent skills.
- Provide a README that explains how to use the repo, add a new skill, install skills globally, and import skills for a project without dirtying project Git state.
- Include a reusable skill template so new skills start from a consistent structure.
- Keep the repository compatible with installer workflows such as `npx skills add ...`.

**Non-Goals:**
- Build a custom package manager or publish an npm package for this repo.
- Mirror installed skills into every application repository.
- Depend on Claude-only or Codex-only metadata as the default skill format.
- Implement project-specific skills for a particular application.

## Decisions

1. Use `skills/<skill-name>/SKILL.md` as the canonical source layout.

   This is the lowest-common-denominator format across Claude Code and Codex. Alternatives considered were separate `claude/` and `codex/` trees, or storing skills directly at the repository root. Separate trees would duplicate content and drift over time; root-level skills would make repository docs and tooling harder to distinguish from skill directories.

2. Prefer global installation for day-to-day use.

   Global installation keeps application repositories clean because installed skills live in agent-specific user directories, not inside the app checkout. Project-local installation remains documented for cases where a repo must pin its own skills, but the README will recommend local Git excludes for generated `.claude/skills/` or `.codex/skills/` folders.

3. Keep skills cross-agent by default and document tool-specific extensions as opt-in.

   Skill frontmatter should include only portable fields such as `name` and `description` by default. Claude-specific or Codex-specific fields can be added only when a skill intentionally targets one agent, and that limitation should be named in the skill description.

4. Add a template rather than a generator.

   A template is enough for an empty personal skills repository and keeps maintenance low. A script can be added later if skill creation becomes repetitive or validation needs become stricter.

## Risks / Trade-offs

- Installer CLI behavior may change over time -> The README will frame `npx skills add` as the preferred current workflow and keep the underlying repo layout simple enough for manual copy or other installers.
- Cross-agent portability can limit advanced agent-specific features -> The default template will stay portable, while specialized skills can explicitly document when they require Claude Code or Codex.
- Project-local installation may still create untracked files -> The README will provide `.git/info/exclude` guidance so generated local skill folders do not affect committed Git state.
- Empty template skills can become vague -> The template will include concise guidance for frontmatter, triggers, workflow, resources, and validation.
