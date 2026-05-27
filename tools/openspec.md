# OpenSpec

Source: https://github.com/Fission-AI/OpenSpec

## What It Is

OpenSpec is a spec-driven workflow tool for AI coding assistants. It creates change folders with proposal, design, specs, and task artifacts before implementation.

Use it when a project needs clearer planning than chat history alone.

## Install

OpenSpec requires Node.js 20.19.0 or higher.

Install globally with npm:

```bash
npm install -g @fission-ai/openspec@latest
```

Verify:

```bash
openspec --version
```

## Project Init

Initialize inside a project:

```bash
cd /path/to/project
openspec init
```

OpenSpec creates an `openspec/` directory and can configure supported AI tools with slash commands or skills.

## Notes

- Use OpenSpec before larger changes where requirements and implementation steps should be explicit.
- It is a project tool, not a portable `SKILL.md` skill.
- Do not copy OpenSpec-generated project folders into this repository unless documenting this repository itself.
