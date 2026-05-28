---
name: repo-readme-writer
description: Generate or improve a repository README by inspecting the current working repo. Use when asked to create, rewrite, update, or polish README.md files, especially hackathon/product repos, Web3 apps, full-stack apps, or projects that need story scenario, problem statement, solution, product concept, user flow diagram, system architecture diagram, tech stack, setup, and smart contract address sections.
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
   - In **Update mode**, inspect the existing README for Excalidraw links, image links, Mermaid diagrams, or ASCII diagrams before creating anything new.
   - If an Excalidraw MCP is available, prefer Excalidraw scenes for the two diagrams.
   - If no Excalidraw MCP is available, or if scene linking is not available, use Mermaid or ASCII diagrams in the README.
   - Do not block README generation only because diagram tooling is unavailable.
5. Ask only when important facts cannot be inferred safely:
   - Target user or story scenario is unclear
   - Smart contract network/address is missing or ambiguous
   - Setup commands cannot be inferred
   - Product name conflicts across files
6. Write or update `README.md`.
7. Re-read the final README for broken structure, false claims, missing required sections, and commands that do not match the repo.

## Required README Sections

Use these sections unless the user asks for a different order. Keep headings clear and readable.

```md
# Project Name

## Story Scenario

## Problem Statement

## Solution

## Product Concept

## User Flow

## System Architecture Flow

## Tech Stack

## Smart Contracts

## Getting Started

## Environment Variables

## Running Locally

## Project Structure

## Demo / Screenshots

## Roadmap

## Notes
```

If a section truly does not apply, keep it brief rather than inventing content. For example, a non-Web3 repo can say under Smart Contracts: "This project does not use smart contracts."

## Section Guidance

### Story Scenario

Write a short scenario that makes the project feel real. Use a concrete user, context, and pain point. Avoid vague marketing copy.

### Problem Statement

State the problem in practical terms. Explain what is broken, inefficient, risky, confusing, or missing.

### Solution

Explain how the project solves the problem. Tie the solution to actual implemented features, not imagined future features.

### Product Concept

Describe the product as a buildable system:
- Core experience
- Key features
- Primary user
- What makes the approach distinct

### User Flow

Always include a user flow diagram. Prefer an Excalidraw scene link when available; otherwise include Mermaid or ASCII that is simple enough to read on GitHub.

ASCII fallback example:

```text
User
  |
  v
Landing / Dashboard
  |
  v
Connect Wallet / Sign In
  |
  v
Create or Select Action
  |
  v
Review Result
  |
  v
Confirm / Share / Track
```

### System Architecture Flow

Always include a system architecture diagram based on the actual repo. Prefer an Excalidraw scene link when available; otherwise include Mermaid or ASCII.

ASCII fallback example:

```text
Browser UI
  |
  v
Frontend App
  |
  +--> API / Server Actions
  |       |
  |       v
  |     Database / External APIs
  |
  +--> Wallet Provider
          |
          v
       Smart Contracts
          |
          v
       Blockchain Network
```

### Excalidraw Diagram Mode

Use this mode only when an Excalidraw MCP server is available in the active client. Treat Excalidraw as a diagram capability bundled into this README workflow, not as a standalone repo tool.

For a new README:
- Create two separate scenes: User Flow and System Architecture Flow.
- Add the scene links under the matching README sections.
- If the user will manually export PNGs later, include a short note such as "Excalidraw scene: <url>" rather than inventing a local image path.
- Include Mermaid or ASCII fallback only when helpful for immediate GitHub readability.

For an existing README:
- First check whether the README already has Excalidraw scene links, image links, Mermaid diagrams, or ASCII diagrams.
- If existing Excalidraw links are present and the MCP can access them, update those scenes instead of creating duplicates.
- If existing Excalidraw links are present but inaccessible, keep the links unless clearly stale, then create new scenes and label them as updated.
- If existing image diagrams are present, preserve them when still accurate. Add Excalidraw scene links only if the current diagrams are missing, stale, or requested for editing.
- If existing Mermaid or ASCII diagrams are present, replace or supplement them with Excalidraw scene links when the MCP can produce better diagrams.
- Do not delete old diagrams unless they are clearly obsolete or replaced by better current diagrams.
- Do not create duplicate diagrams on repeated README updates.

Recommended scene style:
- Use simple boxes for actors, screens, services, APIs, contracts, and storage.
- Use arrows with labels for important actions or data movement.
- Keep labels short so the diagram works in a README.
- Prefer left-to-right flow for user journeys.
- Prefer layered top-to-bottom or left-to-right flow for architecture.
- Use the project name and diagram type in the scene title.

When the MCP can provide a shareable scene URL, link it in the README:

```md
## User Flow

Excalidraw scene: <user-flow-scene-url>

## System Architecture Flow

Excalidraw scene: <system-architecture-scene-url>
```

If the user manually exports PNGs later, update the README to reference the real committed files:

```md
## User Flow

![User Flow](./docs/images/user-flow.png)

## System Architecture Flow

![System Architecture Flow](./docs/images/system-architecture.png)
```

If the scene link exists but GitHub readability needs a fallback, include Mermaid or ASCII under it:

````md
## User Flow

Excalidraw scene: <scene-url>

```text
ASCII fallback here
```
````

Do not invent image paths. Only reference files or URLs that actually exist or were created during the task.

### Tech Stack

Use a grouped list or table. Include only technologies actually present or clearly required.

Suggested groups:
- Frontend
- Backend
- Database / Storage
- Blockchain / Web3
- AI / APIs
- Tooling
- Deployment

### Smart Contracts

For Web3 projects, include a table:

```md
| Contract | Network | Address | Purpose |
| --- | --- | --- | --- |
| ExampleContract | Monad Testnet | `0x...` | Handles ... |
```

Find addresses in deployment files, config files, `.env.example`, frontend constants, docs, or scripts. Do not hallucinate addresses.

If addresses are missing:

```md
| Contract | Network | Address | Purpose |
| --- | --- | --- | --- |
| ExampleContract | TBD | TBD | Handles ... |
```

### Getting Started / Running Locally

Use commands from the repo. Prefer exact package scripts over generic commands.

If scripts are available, show the shortest reliable setup:

```bash
npm install
npm run dev
```

Do not claim a command works unless it is present or strongly implied by the repo.

### Environment Variables

Read `.env.example` if present. Use a table:

```md
| Variable | Purpose |
| --- | --- |
| NEXT_PUBLIC_CONTRACT_ADDRESS | Frontend contract address |
```

If no env example exists, include a short note and only list variables discovered in code.

### Demo / Screenshots

If assets exist, reference them. If not, use a placeholder sentence:

```md
Add screenshots or a demo link here after deployment.
```

## Style

- Write like a polished hackathon/product README.
- Be concrete and repo-specific.
- Prefer short paragraphs and tables.
- Avoid hype that the code does not support.
- Avoid long architecture essays.
- Preserve useful existing README content in update mode.
- Remove stale boilerplate when replacing a weak README.

## Safety

- Do not invent smart contract addresses, deployed URLs, API keys, metrics, sponsors, prizes, or production status.
- Mark unknown values as `TBD`.
- If the repo is private or incomplete, say what was inferred from available files.
- If the README is for judging/demo use, prioritize clarity of product story and local run instructions.
