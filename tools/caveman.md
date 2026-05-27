# Caveman

Source: https://github.com/JuliusBrussee/caveman

## What It Is

Caveman is a third-party skill/plugin pack for making AI coding agents answer with fewer tokens while keeping the technical meaning.

Use it when you want lower-noise agent responses across Claude Code, Codex, Cursor, and other supported tools.

## Install

The upstream install guide recommends this one-liner for macOS, Linux, WSL, and Git Bash:

```bash
curl -fsSL https://raw.githubusercontent.com/JuliusBrussee/caveman/main/install.sh | bash
```

Preview before installing:

```bash
curl -fsSL https://raw.githubusercontent.com/JuliusBrussee/caveman/main/install.sh | bash -s -- --dry-run
```

Install only for Codex:

```bash
npx skills add JuliusBrussee/caveman -a codex
```

## Project Init

Caveman is usually installed globally or per-agent. It does not need project init for normal use.

If you want always-on repo rule files for supported agents, run the upstream installer with init behavior from inside the project:

```bash
curl -fsSL https://raw.githubusercontent.com/JuliusBrussee/caveman/main/install.sh | bash -s -- --with-init
```

Use this carefully because it can write agent rule files into the current repo.

## Notes

- This repository does not vendor Caveman.
- Keep using upstream unless you want to customize or pin your own copy.
- If you customize it, copy the relevant skill folder into `skills/<skill-name>/`.
