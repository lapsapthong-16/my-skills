## Why

This repository needs a clear structure for reusable AI-agent skills that can be shared across Claude Code and Codex without becoming tied to either tool's private installation layout. A documented workflow will make it easy to add new skills, install selected skills globally, and avoid dirtying unrelated project repositories.

## What Changes

- Add a standard `skills/<skill-name>/SKILL.md` source layout for cross-agent skill definitions.
- Add supporting folders for reusable skill assets, scripts, and references inside each skill directory.
- Add repository-level guidance for validating, adding, installing, and importing skills.
- Document safe installation patterns for global usage and project-specific usage without committing generated local agent folders.
- Add a small example skill or template so future skills can be created consistently.

## Capabilities

### New Capabilities
- `cross-agent-skill-repository`: Defines the repository layout, documentation, and workflows for storing skills compatible with Claude Code and Codex.

### Modified Capabilities

## Impact

- Affects repository structure, documentation, and helper scripts.
- No runtime application APIs or production systems are affected.
- Future users will install skills into agent-specific local directories such as Claude Code or Codex skill locations rather than copying skill folders into application source trees.
