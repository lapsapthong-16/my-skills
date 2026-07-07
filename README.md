# My Skills

Personal agent setup repo for Claude Code, Codex, and related coding tools.

This repo has two kinds of things:

- **Owned skills**: skills I create or customize. These live in `skills/`.
- **Tools I use**: third-party tools with their own docs, installers, or source links. These live in `tools/` or are linked below.

The point is simple: keep one place that explains what I use, how to install it, and when it belongs in a project.

## Repo Layout

```text
.
├── skills/
│   └── <skill-name>/
│       ├── SKILL.md
│       ├── references/
│       ├── scripts/
│       └── assets/
├── tools/
│   ├── caveman.md
│   ├── openspec.md
│   ├── ponytail.md
│   └── rtk.md
└── templates/
    └── skill/
        ├── SKILL.md
        ├── references/
        ├── scripts/
        └── assets/
```

## Owned Skills


- `parallel-goals`: turns a task into a concrete build brief and goal, delegates independent work to parallel agents, and synthesizes verified results.
- `validator`: validates or generates project problem statements, niches, opponent maps, and solution directions for repos, hackathon ideas, and rough product tracks.
- `repo-illustrations`: generates English README illustrations for repository overview, architecture, workflow, feature, setup, or shot-list visuals based on a repo `README.md`.
- `repo-readme-writer`: creates or improves a repo-aware `README.md` with product story, flow diagrams, architecture diagrams, stack, setup, and Web3 contract details when relevant.
- `refactor-codebase`: reviews architecture, generates deepening candidates when useful, safely refactors an entire repository, removes proven dead code, files, assets, and dependencies, verifies behavior, and reports per-file and aggregate changes.

Install every owned skill from this repo:

```bash
npx skills add lapsapthong-16/my-skills \
  --skill parallel-goals \
  --skill validator \
  --skill repo-illustrations \
  --skill repo-readme-writer \
  --skill refactor-codebase \
  --agent claude-code \
  --agent codex \
  --global
```

Restart Claude Code or Codex after installing new skills.

## Tools I Use

Tools are third-party projects that are not owned by this repo. Each entry explains what it is, where it comes from, and how it belongs in a project when that applies.

- [Caveman](./tools/caveman.md): token-saving skill/plugin pack.
- [Frontend Slides](./tools/frontend-slides.md): Claude Code plugin and portable agent skill for creating HTML presentations or converting PowerPoint decks.
- [OpenSpec](./tools/openspec.md): spec-driven change workflow.
- [Ponytail](./tools/ponytail.md): minimal-code skill/plugin pack for avoiding over-engineering.
- [RTK](./tools/rtk.md): token-saving command proxy.
- [prototype](https://github.com/mattpocock/skills/blob/main/skills/engineering/prototype/SKILL.md): Matt Pocock tool for quickly building throwaway implementations to learn before committing.
- [diagnosing-bugs](https://github.com/mattpocock/skills/blob/main/skills/engineering/diagnosing-bugs/SKILL.md): Matt Pocock tool for reproducing, isolating, fixing, and regression-testing bugs.
- [handoff](https://github.com/mattpocock/skills/blob/main/skills/productivity/handoff/SKILL.md): Matt Pocock tool for writing a continuation handoff so another session can pick up work.
- [writing-great-skills](https://github.com/mattpocock/skills/blob/main/skills/productivity/writing-great-skills/SKILL.md): Matt Pocock tool for creating, assessing, and editing skills well.

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
