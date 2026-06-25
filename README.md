# Project Bootstrap

Reusable instruction file for generating project starter documents from a single idea dump.

Attach `PROJECT_BOOTSTRAP.md` to an AI prompt and ask it to generate a complete project documentation and task starter pack.

## What This Generates

Depending on the selected AI platform, the bootstrap generates:

```text
PRD.md
README.md
.devtool/features/*.md
<AI instruction file for your platform>
```

Supported project modes:

```text
frontend
backend
full-stack
```

Supported AI instruction targets:

```text
codex   -> AGENTS.md
claude  -> CLAUDE.md
copilot -> .github/copilot-instructions.md
all     -> all supported instruction files
```

If no project mode is provided, the AI should infer the best mode from the idea dump.

## Recommended VS Code Extension

For viewing and managing the generated Markdown Kanban/task files in VS Code, install:

```text
lachyfs.kanban-markdown
```

A workspace recommendation is included in:

```text
.vscode/extensions.json
```

## Files In This Repository

```text
PROJECT_BOOTSTRAP.md
PROMPT_TEMPLATE.md
README.md
CONTRIBUTING.md
LICENSE
.vscode/extensions.json
.gitignore
```

## Generated File Responsibilities

### `PRD.md`

Product and technical specification.

Use it for:

- product summary
- goals and non-goals
- users/personas
- UX and design direction, when relevant
- frontend architecture, when relevant
- backend/API architecture, when relevant
- data model and storage design
- integrations
- MVP scope
- open questions
- definition of done

### AI instruction file

The generated AI instruction file depends on your platform:

| Platform | Generated file |
|---|---|
| Codex | `AGENTS.md` |
| Claude Code | `CLAUDE.md` |
| GitHub Copilot | `.github/copilot-instructions.md` |
| All / unsure | generate all of the above |

Use it for:

- source-of-truth rules
- default read path
- task workflow
- behavioral rules
- verification rules
- final task report format

Keep these files brief. They should not duplicate the PRD or README.

### `README.md`

Developer guide for the generated project.

Use it for:

- setup instructions
- environment variables
- run commands
- frontend/backend commands
- CLI commands
- API endpoints
- testing
- build/deployment
- project limitations

### `.devtool/features/*.md`

Feature task files.

Each task includes:

- YAML frontmatter
- status
- priority
- epic
- dependencies
- order
- suggested GPT model
- reasoning level
- scope
- acceptance criteria
- notes
- progress log

These files are intended to be the task source of truth and can be visualized with a Markdown Kanban-style extension.

## Step-By-Step Usage

### 1. Install the VS Code Kanban extension

Install this extension in VS Code:

```text
lachyfs.kanban-markdown
```

This is optional for generation, but useful after the AI creates `.devtool/features/*.md` task files.

### 2. Choose your project mode

Use one of:

```text
frontend
backend
full-stack
```

Use `Infer from my idea dump` if you are not sure.

### 3. Choose your AI platform target

Use one of:

```text
codex
claude
copilot
all
```

Recommended:

- Use `codex` if you mainly work with OpenAI Codex.
- Use `claude` if you mainly work with Claude Code.
- Use `copilot` if you mainly work with GitHub Copilot.
- Use `all` if you want the generated project to support multiple AI coding tools.

### 4. Copy the prompt template

Open `PROMPT_TEMPLATE.md` and copy the prompt.

### 5. Paste your idea dump

Paste your raw project idea under:

```text
Project idea dump:
---
<paste my raw idea here>
---
```

### 6. Attach the bootstrap file

Attach:

```text
PROJECT_BOOTSTRAP.md
```

### 7. Ask the AI to generate the files directly

The AI should create the project starter files, not just describe them.

### 8. Open the generated project in VS Code

Use the Markdown Kanban extension to inspect the generated task files under:

```text
.devtool/features/
```

Then start with the first `todo` task by lowest `order`.

## Prompt To Use

Copy this, paste your idea dump at the bottom, and attach `PROJECT_BOOTSTRAP.md`.

```text
I want to build the project described below.

Using the attached PROJECT_BOOTSTRAP.md, generate:

- PRD.md
- README.md
- .devtool/features/*.md
- the correct AI instruction file(s) for my selected AI platform

Project mode:
- Infer from my idea dump
- Or use one of: frontend, backend, full-stack

AI platform target:
- Infer from my context
- Or use one of: codex, claude, copilot, all

Requirements:
- Create the files directly.
- Keep AI instruction files brief and token-efficient.
- Avoid duplicate content across files.
- If frontend: focus on UX, design direction, routing, components, state, API client needs, accessibility, responsive behavior, and frontend tests.
- If backend: focus on architecture, APIs, data model, storage, integrations, jobs, security, and backend tests.
- If full-stack: include both frontend and backend planning, and make task dependencies connect the UI, API, and data layers.
- Break the work into small feature task files with dependencies.
- Add suggested GPT model and reasoning level for every task.
- Make reasonable assumptions for small missing details.
- Ask questions only if missing information materially affects architecture, scope, data model, UX direction, AI platform target, or implementation strategy.

Project idea dump:
---
<paste my raw idea here>
---
```

## Platform Notes

- Codex reads `AGENTS.md` files as repository instructions.
- Claude Code uses `CLAUDE.md` for project memory/instructions.
- GitHub Copilot supports repository custom instructions through `.github/copilot-instructions.md`.

When targeting `all`, generate equivalent short instructions for each platform. The content should be consistent, but the file name and heading may be adapted for the platform.

## Project Mode Guide

### Frontend

Choose this for UI-heavy projects, dashboards, websites, mobile screens, prototypes, or design systems.

Focus on UX, design direction, routing, components, state, data fetching, accessibility, responsive behavior, and frontend testing.

### Backend

Choose this for APIs, services, data pipelines, CLI tools, workers, integrations, databases, and automation projects.

Focus on architecture, APIs, data model, storage, integrations, jobs, security, error handling, and backend testing.

### Full-stack

Choose this when the project has both a meaningful UI and backend/data/API responsibilities.

Connect UI, API, and data layers through dependency-aware tasks.

## Recommended Repository Structure

```text
project-bootstrap/
  ├── README.md
  ├── PROJECT_BOOTSTRAP.md
  ├── PROMPT_TEMPLATE.md
  ├── CONTRIBUTING.md
  ├── LICENSE
  ├── .vscode/
  │   └── extensions.json
  └── .gitignore
```

## Notes

This repository does not generate code by itself. It is an instruction template for AI-assisted project bootstrapping.
