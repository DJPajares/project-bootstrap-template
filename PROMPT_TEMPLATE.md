# Project AI Bootstrap v5 Prompt

I want to build the project described below.

Using the attached `PROJECT_BOOTSTRAP_V5.md` (v5.3.1 Linear + local Codex/mobile Remote workflow):

1. Generate the project-specific repository documents:
   - `PRD.md`
   - `AGENTS.md`
   - `README.md`
   - `SKILL.md` only when the project has meaningful UI
2. Create or reuse one dedicated Linear Project for this software project.
3. Create the Linear milestones, parent issues, executable issues, labels, priorities, and blocker relationships required to implement it.
4. Do not generate `.devtool/features/*.md` or any other local task files.

## Linear target

- Workspace/team: `<team name, or infer when unambiguous>`
- Project name: `<optional; infer from the idea when omitted>`
- Existing Linear project to reuse: `<optional name or URL>`

## Project shape

Infer one or more when omitted:

```text
web-ui
mobile-ui
desktop-ui
api-service
full-stack-product
cli-tool
library-sdk
data-pipeline
ai-system
automation-integration
infrastructure-platform
```

## Requirements

- Make reasonable assumptions for small gaps and record them.
- Ask only one focused question when a missing answer materially changes architecture, scope, data model, UX, security, or the required Linear team.
- Keep `AGENTS.md` brief and token-efficient.
- Keep Linear as the only implementation-task state.
- Require agents to move issues to In Progress before editing code and verify the mutation.
- Set `execution_mode: codex-local-remote` unless the user explicitly selects another mode.
- Set `completion_mode` to `merge-gated` or `pr-created`; do not assume one silently.
- Require agents to update status according to the selected completion mode.
- A failed Linear status mutation must stop implementation rather than allowing status drift.
- Use small, dependency-aware, independently verifiable Linear issues.
- Use capability-based agent recommendations rather than assuming one LLM provider.
- Prefer latest stable dependencies where practical.
- Use the repository's existing package manager and tooling; otherwise prefer pnpm, TypeScript, Vitest, Prettier, and lint-staged where they fit.
- For meaningful UI, apply the contextual TasteSkill workflow and generate a project-specific `SKILL.md`.
- Do not default to a component library unless the user, repository, domain, or design read justifies it.
- Do not create duplicate Linear projects or duplicate issues when rerun.

## Execution workflow

- Primary execution mode: `codex-local-remote`
- Completion mode: `pr-created` (use `merge-gated` only when explicitly selected)
- Codex Cloud: optional and disabled unless explicitly requested

## Project idea

---
<Paste the project idea here>
---

## Model and completion requirements

- For every Linear issue, include provider-compatible model guidance for both Codex/OpenAI and Claude/Anthropic.
- Resolve current model names from the connected environments at generation time; do not permanently rely on model names listed in this prompt.
- Keep capability profile and reasoning requirement canonical.
- After every completed task, require the agent to include the GitHub PR URL, current Linear issue URL, next Linear issue URL, and the next issue's suggested models and reasoning for both providers.
