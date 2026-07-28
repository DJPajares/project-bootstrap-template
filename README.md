# Project AI Bootstrap v5.3.1

A reusable bootstrap that turns a raw software idea into repository documentation and a complete execution roadmap in Linear.

The default execution workflow is:

```text
Codex app or Codex VS Code extension on your computer
  -> local GitHub repository
  -> Linear MCP for tasks and status updates
  -> GitHub branch and pull request
  -> ChatGPT mobile Remote tab for control away from the computer
```

**Codex Cloud is optional. It is not required for this workflow.**

## What is automated and what is manual?

| Step | Automated after setup? | Notes |
|---|---:|---|
| Create the GitHub repository | Usually manual once | Can be scripted with authenticated GitHub CLI, but the generic ChatGPT GitHub connection may not create repositories. |
| Create `PRD.md`, `AGENTS.md`, `README.md`, and `SKILL.md` | Yes when a write-capable GitHub action is connected | Otherwise ChatGPT generates them and local Codex commits/pushes them as the first repository task. |
| Create the Linear Project and complete issue roadmap | Yes | This is a required bootstrap output, not an optional draft. |
| Create labels, priorities, parent issues, and blocker relations | Yes | ChatGPT uses the connected Linear workspace. |
| Install/sign in to Codex | Manual once per machine | Account and device authorization cannot be safely bypassed. |
| Connect Codex to Linear MCP | Mostly automated command + manual OAuth | Run the command once, then approve the Linear login. |
| Connect GitHub to Linear and configure PR status automation | Manual once per workspace/repository | Usually requires workspace or GitHub permissions. |
| Clone/open the repository locally | Manual or semi-automated once | Codex or `gh` can clone it when authenticated, but you must grant local folder access. |
| Start and run issues | Yes | Codex reads Linear, updates status, implements, verifies, pushes, and creates a PR. |
| Control Codex from mobile | Yes after pairing | Your host computer must remain running, online, and available to Codex Remote. |
| Review and merge the PR | Manual by default | This preserves human approval. |
| Suggest the next task and model | Yes | Copied from the next ready Linear issue. |

## First-time setup — shortest correct path

Do these one-time steps in order.

### 1. Create a GitHub repository

Create an empty or README-initialized repository in GitHub.

This is the only universally manual project-creation step. It may be automated with an authenticated GitHub CLI, but the bootstrap must not assume that capability exists.

### 2. Connect ChatGPT to GitHub and Linear

In ChatGPT Apps, authorize:

- GitHub access to the new repository
- Linear access with permission to create and update projects and issues

After this, ChatGPT can publish the planning files and create the entire Linear roadmap.

### 3. Run the bootstrap in ChatGPT

Attach `PROJECT_BOOTSTRAP_V5.md` and use `PROMPT_TEMPLATE.md`.

Provide:

- project idea
- GitHub repository, such as `owner/repository`
- Linear team
- optional existing Linear Project to reuse

Approve the requested GitHub and Linear writes. When the available ChatGPT GitHub connection cannot write, have ChatGPT generate the documents and make the first local Codex run commit and push them before implementation begins.

The bootstrap must finish with:

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
  suggested Codex/OpenAI and Claude/Anthropic guidance
```

### 4. Connect GitHub to Linear

In Linear settings, connect the GitHub repository and configure issue-status automation.

Recommended review-based lifecycle:

```text
Branch or draft PR -> In Progress
PR ready           -> In Review
PR merged          -> Done
```

For your existing direct-completion workflow, use:

```text
Codex starts issue -> In Progress
Codex completes and opens PR -> Done
Manual merge does not change the already completed issue
```

This package defaults to your existing `pr-created` behavior. Store the policy in `AGENTS.md` as `completion_mode`:

```text
pr-created      # default for this package; matches your current In Progress -> Done workflow
merge-gated     # optional: Done only after merge
```

### 5. Connect local Codex to Linear

Run once on the computer where Codex works:

```bash
codex mcp add linear --url https://mcp.linear.app/mcp
```

Complete the Linear OAuth login when prompted.

If remote MCP is not enabled automatically, add this to `~/.codex/config.toml`:

```toml
[features]
rmcp_client = true

[mcp_servers.linear]
url = "https://mcp.linear.app/mcp"
```

Then run:

```bash
codex mcp login linear
```

The Codex CLI and Codex VS Code extension share this configuration.

### 6. Open or clone the repository in Codex

Use either path:

```text
Codex app
  -> open the local repository folder

VS Code
  -> open the repository
  -> use the Codex extension
```

Cloning can be semi-automated when GitHub CLI is already authenticated:

```bash
gh repo clone owner/repository
```

You still need to grant Codex or VS Code access to the local folder.

### 7. Enable mobile Remote access

On the same ChatGPT account:

1. Update the ChatGPT mobile app and Codex desktop app.
2. Keep Codex running on the Mac or development machine.
3. Open **Remote** in the ChatGPT mobile app.
4. Select the supported Codex machine/thread.
5. Start a new task or continue an active task.

The files, credentials, terminal, and repository remain on the host machine. Mobile receives the live thread, approvals, diffs, terminal output, screenshots, and test results.

## Daily workflow from mobile

```text
1. Keep the Codex host machine awake, online, and signed in.
2. Open ChatGPT mobile -> Remote.
3. Open the project thread or start a new thread for the repository.
4. Ask Codex to run the next ready Linear issue.
5. Codex reads the issue and blockers.
6. Codex moves it to In Progress and verifies the update.
7. Codex implements locally, runs checks, pushes a branch, and creates a PR.
8. Codex posts the completion summary and next-task recommendation.
9. Review the PR from GitHub, Linear, or your computer.
10. Merge manually.
```

Use [`prompts/MOBILE_REMOTE_RUN_NEXT_ISSUE.md`](prompts/MOBILE_REMOTE_RUN_NEXT_ISSUE.md).

## Required completion output

After each issue, Codex must show:

- what changed
- verification performed
- remaining risks
- completed Linear issue URL
- GitHub PR URL
- next ready Linear issue URL
- next issue title
- next issue's suggested Codex/OpenAI model and reasoning
- next issue's suggested Claude/Anthropic model and reasoning
- why the next issue is ready

The next task and model guidance must be read from Linear rather than invented during the completion report.

## VS Code remains fully supported

The roadmap does not change when switching tools.

```text
Codex app + mobile Remote
Codex VS Code extension
Codex CLI
Claude Code
```

All use:

- the same GitHub repository
- the same repository documents
- the same Linear Project and issues
- the same branch/PR conventions

## Optional Codex Cloud

Codex Cloud exists as a separate execution path, but it is not needed for the local/mobile Remote workflow. See [`references/OPTIONAL_CODEX_CLOUD.md`](references/OPTIONAL_CODEX_CLOUD.md).

## Package contents

```text
PROJECT_BOOTSTRAP_V5.md
PROMPT_TEMPLATE.md
README.md
VERSION.md
references/
  CODEX_LOCAL_REMOTE_WORKFLOW.md
  SETUP_AUTOMATION_BOUNDARIES.md
  OPTIONAL_CODEX_CLOUD.md
  LINEAR_WORKFLOW.md
  AUTOMATIC_STATUS_CONFIGURATION.md
  MODEL_ROUTING.md
prompts/
  CHATGPT_BOOTSTRAP_AND_PUBLISH.md
  CODEX_LOCAL_RUN_NEXT_ISSUE.md
  MOBILE_REMOTE_RUN_NEXT_ISSUE.md
  CODEX_VSCODE_RUN_NEXT_ISSUE.md
templates/
  AGENTS.template.md
  LINEAR_COMPLETION_COMMENT.template.md
```

## Source-of-truth policy

- Product and architecture: `PRD.md`
- Agent execution rules: `AGENTS.md`
- Setup and commands: repository `README.md`
- UI/UX constraints: `SKILL.md`
- Task scope, state, dependencies, priority, model guidance, and progress: Linear

Do not create `.devtool/features/*.md`, `TASKS.md`, or another local task mirror.
