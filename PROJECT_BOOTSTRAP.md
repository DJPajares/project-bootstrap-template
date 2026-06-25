# PROJECT_BOOTSTRAP.md

## Purpose

Use this file as an instruction document for generating starter project documents from one raw project idea.

When attached to an AI prompt, generate:

```text
PRD.md
README.md
.devtool/features/*.md
<AI instruction file for the selected platform>
```

This bootstrap supports three project modes:

```text
frontend
backend
full-stack
```

It also supports multiple AI instruction targets:

```text
codex   -> AGENTS.md
claude  -> CLAUDE.md
copilot -> .github/copilot-instructions.md
all     -> all supported instruction files
```

If the user does not specify a project mode or AI platform target, infer it from the project idea and context.

## Prompt Template

Copy this prompt, paste your project idea below it, and attach `PROJECT_BOOTSTRAP.md`.

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

## AI Platform Target Rules

Generate the AI instruction file requested by the user.

Use this mapping:

```text
codex   -> AGENTS.md
claude  -> CLAUDE.md
copilot -> .github/copilot-instructions.md
all     -> AGENTS.md, CLAUDE.md, and .github/copilot-instructions.md
```

If the target is unclear, generate `AGENTS.md` by default unless the user clearly mentions Claude Code or GitHub Copilot.

All generated AI instruction files should contain the same core guidance:

- purpose
- project snapshot
- source of truth
- default read path
- task workflow
- task statuses
- behavioral rules
- project rules
- verification
- task report
- when unsure

Keep each AI instruction file brief. Do not duplicate the PRD or README.

When targeting multiple platforms, keep the files consistent and avoid conflicting instructions.

## Project Mode Rules

### Frontend Mode

Use when the project is mainly a UI, website, dashboard, mobile app, desktop app, design system, prototype, or user-facing experience.

Focus on:

- UX requirements
- design direction
- pages/screens
- routing/navigation
- layout and responsive behavior
- components
- design tokens/theme
- state management
- data fetching/API client needs
- forms and validation
- loading, empty, error, and success states
- accessibility
- frontend testing
- build/deployment

Only include backend/API sections if the frontend needs an API contract, mock API, or external service.

### Backend Mode

Use when the project is mainly an API, service, database system, CLI, automation, worker, integration, ingestion pipeline, or internal tool without a primary UI.

Focus on:

- backend architecture
- API/interface design
- data model and storage
- migrations
- integrations
- background jobs
- CLI commands, if applicable
- auth/security
- validation and error handling
- observability/logging, if useful
- backend tests
- local development and deployment

Only include frontend sections if a UI is explicitly requested.

### Full-Stack Mode

Use when the project has both a meaningful user-facing UI and backend/data/API responsibilities.

Focus on connecting:

- UX and screens
- frontend architecture
- backend/API architecture
- database/storage design
- auth/session flow, if applicable
- API contracts
- frontend data fetching
- error/loading states
- integration tests
- deployment of both layers

Interleave tasks based on real dependencies.

Example:

```text
t01-project-scaffold
t02-frontend-scaffold
t03-backend-health-endpoint
t04-design-tokens
t05-database-setup
t06-api-contract
t07-api-client
t08-main-screen
t09-backend-feature-endpoint
t10-connect-ui-to-api
```

## Core Generation Rules

- Avoid duplicate content across files.
- Keep `AGENTS.md` short.
- Put product, architecture, UX, data model, and technical decisions in `PRD.md`.
- Put setup, commands, endpoints, and developer workflow in `README.md`.
- Put implementation tasks in `.devtool/features/*.md`.
- Make task files the only task state.
- Make tasks small, dependency-aware, and independently verifiable.
- Include acceptance criteria for every task.
- Include suggested model and reasoning level for every task.
- Include only sections relevant to the selected project mode.

## Output Structure

```text
<project-root>/
  ├── PRD.md
  ├── AGENTS.md
  ├── README.md
  └── .devtool/
      └── features/
          ├── t01-<slug>.md
          ├── t02-<slug>.md
          └── ...
```

## PRD.md

`PRD.md` is the product and technical specification.

Recommended sections:

```text
# <Project Name> PRD

## 1. Product Summary
## 2. Problem Statement
## 3. Goals
## 4. Non-Goals
## 5. Users / Personas
## 6. Core Use Cases
## 7. UX / Frontend Requirements
## 8. Design Direction
## 9. Recommended Technical Direction
## 10. High-Level Architecture
## 11. Frontend Architecture
## 12. Backend / API Architecture
## 13. Data Model / Storage Design
## 14. External Integrations
## 15. Security / Privacy Requirements
## 16. Error Handling Requirements
## 17. Testing Requirements
## 18. MVP Scope
## 19. Future Enhancements
## 20. Open Questions
## 21. Definition Of Done
```

Adjust sections based on project mode.

Do not put AI workflow, setup commands, detailed task lists, task metadata, or commit rules in `PRD.md`.

## AI Instruction Files

The AI instruction file is the AI entry point. Keep it brief and token-efficient.

Generate the correct file for the selected platform:

```text
codex   -> AGENTS.md
claude  -> CLAUDE.md
copilot -> .github/copilot-instructions.md
all     -> all supported instruction files
```

Recommended sections:

```text
# AGENTS.md

## Purpose
## Project Snapshot
## Source Of Truth
## Default Read Path
## Task Workflow
## Task Statuses
## Behavioral Rules
## Project Rules
## Verification
## Task Report
## When Unsure
```

`AGENTS.md` should only explain:

- where the AI should start
- what files are authoritative
- when to read PRD or README
- how to choose and update tasks
- behavioral rules
- verification expectations
- final task report format

Do not include full specs, schemas, endpoints, env docs, setup instructions, long examples, or duplicated README content.

Required task report:

```text
After completing a task, report:

- What changed
- How it was verified
- What to test next, if anything
- Recommended next task
- Suggested commit message
```

Commit message format:

```text
type(scope): summary
```

## README.md

`README.md` is the developer-facing project guide.

Recommended sections:

```text
# <Project Name>

## Overview
## Tech Stack
## Project Structure
## Requirements
## Environment Variables
## Local Setup
## Common Development Commands
## Frontend Development
## Backend/API Development
## CLI Commands
## API Endpoints
## Database / Storage Notes
## Testing
## Build / Deployment
## Task Workflow
## Notes / Limitations
```

Adjust sections based on project mode.

Do not include detailed PRD discussion, AI behavioral rules, full task lists, or task frontmatter.

## Feature Tasks

Task files live in:

```text
.devtool/features/
```

Each task file must be independently useful.

### Task File Naming

```text
tNN-short-slug.md
```

Examples:

```text
t01-project-scaffold.md
t02-frontend-scaffold.md
t03-database-setup.md
t04-health-endpoint.md
```

### Task Frontmatter

Each task must start with YAML frontmatter:

```yaml
---
id: "t01-project-scaffold"
status: "todo"
priority: "high"
assignee: null
epic: "foundation"
dueDate: null
created: "2026-01-01T00:00:00Z"
modified: "2026-01-01T00:00:00Z"
completedAt: null
labels: ["foundation", "setup"]
depends_on: []
order: "a01"
---
```

### Task Body

```md
# t01-project-scaffold - Project scaffold

## Hierarchy

- Epic: `foundation`
- Dependencies: None

## Scope

Describe what this task builds.

## Suggested Agent

- Suggested model: `GPT-5.4-mini`
- Reasoning level: `medium`

## Acceptance

- [ ] Acceptance criterion
- [ ] Acceptance criterion
- [ ] Acceptance criterion

## Notes

Implementation notes, constraints, or references.

## Progress Log

- <timestamp>: Task created.
```

## Task Generation Rules

Generate tasks as small vertical slices.

Good:

```text
t01-project-scaffold
t02-frontend-scaffold
t03-design-tokens
t04-health-endpoint
t05-database-models
t06-api-client
t07-dashboard-shell
```

Avoid:

```text
t01-build-backend
t02-build-frontend
t03-create-api
t04-add-ui
```

Each task should:

- have one clear outcome
- be independently verifiable
- have explicit dependencies
- have 3-7 acceptance criteria
- include suggested model and reasoning level
- include labels and an epic
- include a stable order value

Initial statuses:

- first task is usually `todo`
- dependency-blocked tasks are `backlog`
- no task starts as `in-progress`
- no task starts as `done`

## Dependency Rules

Use `depends_on` for real implementation blockers.

Examples:

```yaml
depends_on: []
```

```yaml
depends_on: ["t01-project-scaffold"]
```

```yaml
depends_on: ["t03-health-endpoint", "t04-config-management"]
```

## Model And Reasoning Rules

Every task must include:

```md
## Suggested Agent

- Suggested model: `<model>`
- Reasoning level: `<level>`
```

Use:

```text
GPT-5.4-mini - low
```

For simple documentation, static UI, minor styling, config, and straightforward file updates.

```text
GPT-5.4-mini - medium
```

For ordinary implementation, basic screens, simple endpoints, simple CLI commands, forms, and moderate tests.

```text
GPT-5.5 - high
```

For schema work, migrations, integrations, state management, complex forms, error handling, accessibility passes, and non-trivial tests.

```text
GPT-5.5 - extra high
```

For architecture, complex data flows, ingestion, normalization, sync systems, idempotency, auth flows, cross-cutting frontend architecture, and large refactors.

## Suggested Epic Categories

Use project-appropriate epics.

Common examples:

```text
foundation
design-system
frontend
backend
database
api
auth
integration
ingestion
jobs
state-management
testing
quality
docs
release
```

## Acceptance Criteria Guidelines

Acceptance criteria should be:

- specific
- testable
- scoped to the task
- written as checkboxes
- focused on outcomes

Backend/API example:

```md
## Acceptance

- [ ] `GET /health` returns HTTP 200.
- [ ] Response body is `{ "status": "ok" }`.
- [ ] Endpoint is registered from the main app.
- [ ] README documents how to call the endpoint.
```

Frontend/UI example:

```md
## Acceptance

- [ ] Dashboard route renders successfully.
- [ ] Page uses the shared app layout.
- [ ] Loading, empty, and error states are represented.
- [ ] Layout is usable on mobile and desktop widths.
- [ ] Primary actions are keyboard accessible.
```

## Final Output Requirements

When generating project bootstrap files, the AI should provide:

1. `PRD.md`
2. `README.md`
3. `.devtool/features/*.md`
4. the selected AI instruction file(s)

The AI should also summarize:

- project mode used
- AI platform target used
- files created
- number of feature tasks created
- first task to start
- assumptions made
- open questions

## Quality Checklist

Before finishing, verify that:

- project mode is identified as `frontend`, `backend`, or `full-stack`
- generated AI instruction files are brief and not duplicate PRDs
- `README.md` contains setup and run instructions
- `PRD.md` contains product and architecture details
- frontend/full-stack projects include UX, design, and frontend architecture planning
- backend/full-stack projects include API, storage, integration, and backend architecture planning
- every task has frontmatter
- every task has acceptance criteria
- every task has dependencies
- every task has suggested model and reasoning level
- task dependencies form a sensible implementation flow
- the first task is `todo`
- blocked tasks are `backlog`
- no task starts as `in-progress`
