## ADDED Requirements

### Requirement: Canonical skill source layout
The repository SHALL store reusable skills under `skills/<skill-name>/` with a required `SKILL.md` file in each skill directory.

#### Scenario: New skill is added
- **WHEN** a contributor adds a skill named `api-review`
- **THEN** the repository contains `skills/api-review/SKILL.md`

#### Scenario: Skill includes supporting resources
- **WHEN** a skill needs reusable scripts, references, or assets
- **THEN** those resources are stored inside that skill's directory under `scripts/`, `references/`, or `assets/`

### Requirement: Portable skill metadata
Each default skill SHALL use portable frontmatter with at least `name` and `description` so the skill can be consumed by both Claude Code and Codex.

#### Scenario: Skill is read by an agent
- **WHEN** Claude Code or Codex loads a skill from the repository
- **THEN** the skill exposes a clear `name` and trigger-oriented `description`

#### Scenario: Skill requires a specific agent
- **WHEN** a skill relies on Claude Code-only or Codex-only behavior
- **THEN** the skill description identifies the agent-specific requirement

### Requirement: Repository usage documentation
The repository SHALL include a README that explains how to use the repository, add new skills, install skills globally, and import skills for a project.

#### Scenario: User wants to install skills globally
- **WHEN** a user reads the README
- **THEN** they can find commands for installing selected skills for Claude Code and Codex without modifying an application repository

#### Scenario: User wants to add a new skill
- **WHEN** a user reads the README
- **THEN** they can follow documented steps to create a new `skills/<skill-name>/SKILL.md` directory and commit it to the skills repository

### Requirement: Git-safe project import workflow
The repository SHALL document a project import workflow that avoids committing downloaded or generated agent skill folders unless the user explicitly chooses to vendor them.

#### Scenario: Project uses global skills
- **WHEN** a project relies on globally installed skills
- **THEN** the application repository does not gain new tracked skill files

#### Scenario: Project uses local skill folders
- **WHEN** a user installs or copies skills into a project-local `.claude/skills/` or `.codex/skills/` folder
- **THEN** the README explains how to exclude those folders from Git using local excludes or a committed ignore rule

### Requirement: New skill template
The repository SHALL include a reusable template for creating a new portable skill.

#### Scenario: User creates a skill from the template
- **WHEN** a user copies the template to `skills/<skill-name>/SKILL.md`
- **THEN** the resulting file contains the required frontmatter and concise sections for trigger guidance, workflow, resources, and validation
