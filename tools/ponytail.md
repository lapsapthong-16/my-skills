# Ponytail

Source: https://github.com/DietrichGebert/ponytail

## What It Is

Ponytail is a third-party skill/plugin pack that pushes AI coding agents toward the smallest solution that works: skip speculative work, prefer standard-library and native features, reuse installed dependencies, and only then write minimal custom code.

## Install

### Claude Code

```text
/plugin marketplace add DietrichGebert/ponytail
/plugin install ponytail@ponytail
```

### Codex

```bash
codex plugin marketplace add DietrichGebert/ponytail
```

Open `/plugins`, select the Ponytail marketplace, and install Ponytail. Review and trust its lifecycle hooks under `/hooks`, then restart Codex or start a new thread.

Node.js must be available on the non-interactive shell's `PATH` for the lifecycle hooks. The skills still work without the hooks.

## Notes

- This repository does not vendor Ponytail.
- Keep using upstream unless you need a customized or pinned copy.
- Ponytail includes modes plus review, audit, debt, and help skills.
