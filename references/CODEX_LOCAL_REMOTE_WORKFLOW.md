# Codex Local + Mobile Remote Workflow

## Target architecture

```text
Mac, devbox, or approved remote machine
  Codex app / CLI / VS Code extension
  local Git repository
  local credentials and tools
  Linear MCP
        ^
        | secure Remote connection
        v
ChatGPT mobile app
  start or continue Codex threads
  approve commands
  change direction or model
  inspect terminal output, tests, diffs, and screenshots
```

This is not Codex Cloud. Codex executes on the connected host machine.

## Requirements

- Codex is installed and signed in on the host.
- The repository exists locally and has a working GitHub remote.
- Linear MCP is authenticated in Codex.
- The host remains powered on, connected, and available.
- ChatGPT mobile and Codex desktop use the same authorized account/workspace.

## Run one Linear issue

1. Open the repository in Codex or VS Code.
2. From desktop or mobile Remote, give Codex the Linear Project or issue identifier.
3. Codex fetches the issue, comments, blockers, and status.
4. Codex confirms that blockers are resolved.
5. Codex updates the issue to the Started status and verifies it.
6. Codex reads `AGENTS.md` and only the relevant project documents.
7. Codex creates or uses a branch containing the Linear issue identifier.
8. Codex implements and verifies the issue.
9. Codex pushes the branch and opens a GitHub PR.
10. Codex updates Linear according to `completion_mode`.
11. Codex fetches the next ready issue and copies its model guidance.
12. Codex returns the PR URL and next issue URL.

## Completion modes

### `merge-gated`

```text
Started -> In Progress
PR opened and verified -> In Review
PR merged manually -> Done through Linear/GitHub automation
```

Use this when Done means code is merged.

### `pr-created`

```text
Started -> In Progress
Implementation verified and PR opened -> Done
PR remains available for manual review and merge
```

Use this when Done means the coding agent finished its assigned implementation. This matches the user's existing workflow.

## Mobile operating prompt

Use the prompt in `prompts/MOBILE_REMOTE_RUN_NEXT_ISSUE.md`.

## Switching to VS Code

Open the same repository in VS Code and use the Codex extension. Linear's Codex MCP setup is shared by the CLI and IDE extension, so the task roadmap and status workflow remain unchanged.
