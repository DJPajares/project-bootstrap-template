# Project Bootstrap Prompt Template

Copy this prompt, paste your idea dump below it, then attach `PROJECT_BOOTSTRAP.md`.

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
