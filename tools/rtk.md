# RTK

Source: https://github.com/rtk-ai/rtk

## What It Is

RTK is a command proxy for AI coding agents. It filters noisy command output so agents see the useful parts instead of large logs.

Use it when a project has frequent shell commands, tests, builds, searches, or Git output.

## Install

Install with Homebrew:

```bash
brew install rtk
```

Install with the upstream script:

```bash
curl -fsSL https://raw.githubusercontent.com/rtk-ai/rtk/refs/heads/master/install.sh | sh
```

Verify:

```bash
rtk --version
rtk gain
```

## Project Init

Global init for Claude Code:

```bash
rtk init --global
```

Global init for Codex:

```bash
rtk init -g --codex
```

Project-only init:

```bash
cd /path/to/project
rtk init
```

Preview changes before writing:

```bash
rtk init --global --dry-run
```

Restart the agent after init.

## Notes

- Claude Code uses hooks for command rewriting.
- Codex setup uses AGENTS.md plus RTK instructions.
- You can still call RTK directly: `rtk git status`, `rtk rg "pattern"`, `rtk npm test`.
