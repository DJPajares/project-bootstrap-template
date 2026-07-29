# Project AI Bootstrap v5.4 Prompt

I want to build the project described below.

Using the attached `PROJECT_BOOTSTRAP_V5.md`:

1. Generate or update:
   - `PRD.md`
   - `AGENTS.md`
   - `README.md`
   - `SKILL.md` only when meaningful UI exists
2. Create or reuse one dedicated Linear Project.
3. Create the milestones, parent issues, executable issues, labels, priorities, and blocker relationships needed to implement the project.
4. Do not create `.devtool/features/*.md` or any local task-state file.
5. Treat the Linear issue roadmap as the core output. Do not finish after writing repository documents.

## Linear target

- Team: `<team name, or infer only when unambiguous>`
- Project: `<optional project name or URL>`

## Execution policy

```text
execution_mode: codex-local-remote
completion_mode: pr-created
context_mode: lean
session_policy: one-issue-per-thread
```

## Context-efficiency requirements

- Resolve Linear team statuses once and store their actual names in `AGENTS.md`.
- List existing project issues once during bootstrap and index stable bootstrap keys.
- Give every executable issue an `Execution context` section containing:
  - context budget
  - exact required document headings
  - likely paths/packages
  - whether comments must be read
  - whether the issue was previously attempted/reopened
  - narrow verification commands
- Default `Read comments` to `no`.
- Reference `SKILL.md` only for relevant UI/visual tasks.
- Keep issue descriptions independently executable without copying the whole PRD.
- Keep root `AGENTS.md` brief. Add nested `AGENTS.md` only for materially different subtrees.
- Require one fresh Codex thread per issue.
- Require minimal narration and targeted reads during execution.
- Require narrow verification before broad repository checks.
- Prefer local `git` and `gh` for branch/PR work; use Linear MCP for task state.

## Model guidance

- Use capability profiles as the canonical recommendation.
- Recommend the minimum sufficient capability and reasoning level.
- Provide compatible recommendations for both Codex/OpenAI and Claude/Anthropic when current models can be resolved.
- Otherwise write `resolve at execution time`; do not invent model names.
- Do not assign the strongest model or `xhigh` to routine work.

## Project idea

---
<Paste the project idea here>
---

## Completion requirements

After bootstrap creation, report the Linear Project URL, issue counts, first ready issue URL, its model guidance, assumptions, open questions, and the stored Linear status mapping.
