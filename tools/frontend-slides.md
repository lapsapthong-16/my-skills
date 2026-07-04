# Frontend Slides

Source: https://github.com/zarazhangrui/frontend-slides

## What It Is

Frontend Slides is a third-party Claude Code plugin and portable agent skill for creating HTML slide decks from scratch or by converting PowerPoint files.

It creates single-file, dependency-free web presentations, offers visual style discovery, supports PPT extraction, and includes curated presentation style presets plus a bold template pack.

## Install

### Claude Code Plugin

Run these as two separate Claude Code messages:

```text
/plugin marketplace add https://github.com/zarazhangrui/frontend-slides
```

Then:

```text
/plugin install frontend-slides@frontend-slides
```

Use it in Claude Code with:

```text
/frontend-slides:frontend-slides
```

### Manual Claude Code Skill

Clone the repository into the Claude Code skills directory:

```bash
git clone https://github.com/zarazhangrui/frontend-slides.git ~/.claude/skills/frontend-slides
```

Use it as:

```text
/frontend-slides
```

### Codex And Other Agents

Frontend Slides is not packaged as a Codex plugin. For Codex, point the agent at the upstream repository and ask it to use the Frontend Slides skill:

```text
https://github.com/zarazhangrui/frontend-slides
```

The agent should start from `SKILL.md` and load only the referenced support files needed for the current deck.

## Requirements

- Local coding agent with filesystem and shell access.
- Python with `python-pptx` for PowerPoint conversion.
- Node.js for Vercel deployment or Playwright PDF export.
- Claude Code is only required for the plugin command surface.

## Notes

- This repository does not vendor Frontend Slides.
- Keep using upstream unless you need a customized or pinned copy.
- Generated decks are HTML presentations, usually with inline CSS and JavaScript.
