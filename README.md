# Project AI Bootstrap v5.4

A reusable bootstrap that turns a raw software idea into repository documentation and a complete execution roadmap in Linear.

Version 5.4 keeps the existing local workflow but makes task execution deliberately context-efficient:

```text
Codex app / Codex CLI / Codex VS Code on your computer
  -> local GitHub repository
  -> Linear MCP for issue state
  -> git + GitHub CLI for branch and PR work
  -> ChatGPT mobile Remote for control away from the computer
```

**Codex Cloud remains optional. It is not required.**

## What changed in v5.4

The agent must no longer load the entire project before every issue. The default task loop is now:

```text
Fetch target issue once with relations
  -> verify only unclear or unresolved blockers
  -> move to In Progress and verify
  -> run one concise git status
  -> read AGENTS.md once
  -> read only referenced PRD/README/SKILL sections
  -> inspect only likely affected paths
  -> implement and run narrow verification
  -> create PR and update Linear
  -> fetch one next ready issue
  -> report links and stop
```

The optimized defaults include:

- one fresh Codex thread per Linear issue
- no comment-history fetch unless the issue requires it
- no status-list fetch when the repository stores the resolved status names
- no individual blocker fetch when the relation already includes a completed status
- no full `PRD.md`, `README.md`, or `SKILL.md` read by default
- no `SKILL.md` read for non-UI tasks
- no routine `git log`, remote lookup, or unrelated dirty-file diff
- narrow tests before broad checks
- concise progress narration
- local `git` and `gh` commands instead of extra GitHub MCP context for normal work
- minimum-sufficient model and reasoning recommendations

## First-time setup — shortest correct path

These steps are unchanged from v5.3.1.

### 1. Create a GitHub repository

Create an empty or README-initialized GitHub repository. This may be semi-automated when GitHub CLI is authenticated:

```bash
gh repo create owner/repository --private --clone
```

### 2. Connect ChatGPT to GitHub and Linear

Authorize:

- GitHub access to the repository
- Linear access with permission to create and update projects and issues

### 3. Run the bootstrap in ChatGPT

Attach `PROJECT_BOOTSTRAP_V5.md` and use `PROMPT_TEMPLATE.md`.

The bootstrap creates or updates:

```text
GitHub repository
  PRD.md
  AGENTS.md
  README.md
  SKILL.md when applicable

Linear
  Project
  milestones when useful
  parent issues when useful
  executable issues
  priorities and labels
  blocker relationships
  context packs
  provider-compatible model guidance
```

Each issue receives a small **Execution Context** section containing the exact documents, sections, likely paths, comment policy, verification commands, and context budget needed for that issue. This is what lets Codex avoid rereading the whole project.

### 4. Connect GitHub to Linear

Configure the repository integration and status automation. This package defaults to:

```text
completion_mode: pr-created
```

```text
Todo/Backlog -> In Progress when Codex starts
In Progress -> Done after verified implementation and PR creation
Manual PR review and merge afterward
```

`merge-gated` remains available when Done should mean merged.

### 5. Connect local Codex to Linear

Run once:

```bash
codex mcp add linear --url https://mcp.linear.app/mcp
codex mcp login linear
```

If needed, add:

```toml
[features]
rmcp_client = true

[mcp_servers.linear]
url = "https://mcp.linear.app/mcp"
```

### 6. Open the repository

Use the Codex app, Codex CLI, or the Codex VS Code extension. They work against the same repository and Linear roadmap.

### 7. Use ChatGPT mobile Remote

Keep the host machine awake and connected, open **Remote** in ChatGPT mobile, and continue the Codex thread running on that machine.

## Lean daily workflow

### Start a specific issue

Prefer supplying the Linear issue ID. This avoids searching the roadmap:

```text
Run WDL-61 using the repository's lean Linear workflow.
```

Codex should then:

1. Fetch WDL-61 once with relations.
2. Fetch only blockers whose state is missing, unclear, or unresolved.
3. Skip comments unless WDL-61 explicitly requires them or was previously attempted/reopened.
4. Move WDL-61 to the configured In Progress status and verify the mutation.
5. Run `git status --short --branch` once.
6. Read `AGENTS.md` once and only the task's listed context.
7. Implement, verify, create the PR, update Linear, and fetch one next task.
8. Stop after the completion report.

### Select the next issue automatically

When no issue ID is supplied, Codex should list only a small page of ready candidates from the active project, choose the highest-priority unblocked candidate, then fetch that issue with relations. It must not load the entire project or every backlog issue.

## One issue per thread

Use a fresh Codex thread for each issue. Long-running threads retain prior tool output, source files, diffs, test logs, and reasoning context. Reusing one thread across many issues is convenient but can consume substantially more context.

The completion report should recommend the next task but must not start it. Start the recommended task in a new thread.

## Required completion output

Keep the final report concise:

```md
## Completed

- Linear: <current issue URL>
- GitHub PR: <PR URL>
- Changed: <2-5 concise bullets>
- Verification: <commands and results>
- Risks: <none or concise note>

## Next ready task

- Linear: <next issue URL>
- Title: <title>
- Codex/OpenAI: <issue recommendation and reasoning>
- Claude/Anthropic: <issue recommendation and reasoning>
- Why next: <one sentence>
```

Do not restate the full issue, PR diff, or project roadmap.

## Files to use

- [`PROJECT_BOOTSTRAP_V5.md`](PROJECT_BOOTSTRAP_V5.md) — full bootstrap rules
- [`PROMPT_TEMPLATE.md`](PROMPT_TEMPLATE.md) — create a project and Linear roadmap
- [`templates/AGENTS.template.md`](templates/AGENTS.template.md) — lean repository agent entry point
- [`templates/LINEAR_TASK_ISSUE.template.md`](templates/LINEAR_TASK_ISSUE.template.md) — context-efficient issue format
- [`references/CONTEXT_EFFICIENT_EXECUTION.md`](references/CONTEXT_EFFICIENT_EXECUTION.md) — detailed execution rules
- [`references/MCP_AND_CONTEXT_BUDGET.md`](references/MCP_AND_CONTEXT_BUDGET.md) — tool and output controls
- [`prompts/MOBILE_REMOTE_RUN_NEXT_ISSUE.md`](prompts/MOBILE_REMOTE_RUN_NEXT_ISSUE.md) — mobile Remote prompt
- [`prompts/CODEX_VSCODE_RUN_NEXT_ISSUE.md`](prompts/CODEX_VSCODE_RUN_NEXT_ISSUE.md) — VS Code prompt
- [`prompts/RUN_SPECIFIC_ISSUE_LEAN.md`](prompts/RUN_SPECIFIC_ISSUE_LEAN.md) — most efficient prompt when the issue ID is known
- [`prompts/UPGRADE_EXISTING_PROJECT_TO_LEAN.md`](prompts/UPGRADE_EXISTING_PROJECT_TO_LEAN.md) — retrofit an existing repository and Linear roadmap without duplication
