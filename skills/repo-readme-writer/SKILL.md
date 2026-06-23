---
name: repo-readme-writer
description: Write or improve repository README.md files from the actual working repo. Use when asked to create, rewrite, update, or polish README files for product, hackathon, Web3, full-stack, or demo repositories.
---

# Repo README Writer

## Core Rule

Inspect the current repository before writing. Do not produce a generic README from memory when local files can reveal the actual product, stack, commands, contracts, or architecture.

## Workflow

1. Inspect project files with fast targeted reads:
   - Existing `README.md`
   - `package.json`, lockfiles, workspace configs
   - `src/`, `app/`, `pages/`, `components/`, `backend/`, `server/`
   - `contracts/`, `script/`, `ignition/`, `deployments/`, `foundry.toml`, `hardhat.config.*`
   - `.env.example`, config files, Docker/deployment files
   - `assets/`, `public/`, or docs only when needed for screenshots/demo links
2. Decide the README mode:
   - **Update mode**: if the existing README has useful product, setup, architecture, or contract information, preserve and improve it.
   - **New mode**: if no README exists or the existing README is mostly empty, placeholder, stale, or irrelevant, create a full replacement.
3. Infer the product from code and docs:
   - What the app does
   - Who it is for
   - Why it exists
   - Main user journey
   - Frontend/backend/on-chain/data flow
   - Run commands and required environment
4. Decide diagram flow:
   - In **New mode**, create fresh User Flow and System Architecture Flow diagrams.
   - In **Update mode**, inspect the existing README for Mermaid diagrams, ASCII diagrams, image links, or external diagram links before creating anything new.
   - Prefer Mermaid diagrams directly in the README because GitHub renders them without generated image files or paid services.
   - Use ASCII only when Mermaid would be too complex or the target Markdown renderer does not support Mermaid.
5. Ask only when important facts cannot be inferred safely:
   - Target user or story scenario is unclear
   - Smart contract network/address is missing or ambiguous
   - Setup commands cannot be inferred
   - Product name conflicts across files
6. Read `references/readme-sections.md` only when you need section templates, diagram examples, Web3 contract tables, or README style guidance.
7. Write or update `README.md`.
8. Re-read the final README for broken structure, false claims, missing important sections, and commands that do not match the repo.

## Clarifying Q&A

Prefer inference from the repository, but ask the user concise questions when missing information would make the README misleading or weak. Do not ask about details already visible in files.

Ask at most 3-5 questions at once. Prioritize questions that affect the story, setup, deployment, or contract sections.

Good questions:
- What is the intended user or judge-facing story for this project?
- What problem should the README emphasize?
- Which network are the smart contracts deployed on?
- Are these contract addresses final or placeholders?
- Is there a live demo, video, or screenshot link to include?
- Are there required environment variables not shown in `.env.example`?

If the user does not answer, proceed with `TBD` for unknown values and state what was inferred from the repo.

## Required README Sections

Use only the sections the repo can support. Keep small repos short.

Core sections:

- Project name
- Problem and solution
- Product concept or core workflow
- Tech stack
- Getting started / running locally
- Environment variables, when present
- Notes, when unknowns remain

Add only when supported by the repo:

- Story scenario for demo, pitch, or hackathon repos
- User flow or system architecture diagram for multi-part apps
- Smart contracts for Web3 repos
- Project structure for larger repos
- Demo / screenshots when links or assets exist
- Roadmap when the repo already implies planned work

If a section does not apply, omit it rather than adding filler. For examples and tables, read `references/readme-sections.md`.

## Style

Write concrete, repo-specific README copy. Prefer short paragraphs, tables, and Mermaid diagrams where they clarify the project. Preserve useful existing content in update mode and remove stale boilerplate in new mode.

## Safety

- Do not invent smart contract addresses, deployed URLs, API keys, metrics, sponsors, prizes, or production status.
- Mark unknown values as `TBD`.
- If the repo is private or incomplete, say what was inferred from available files.
- If the README is for judging/demo use, prioritize clarity of product story and local run instructions.
