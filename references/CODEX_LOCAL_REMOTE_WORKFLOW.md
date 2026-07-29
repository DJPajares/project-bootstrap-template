# Codex Local + Mobile Remote Workflow — Lean Mode

## Architecture

```text
Mac, devbox, or approved remote machine
  Codex app / CLI / VS Code extension
  local Git repository
  Linear MCP
  git + GitHub CLI
        ^
        | ChatGPT mobile Remote
        v
Phone or tablet
```

Execution remains on the host machine.

## Run a known issue

1. Start a fresh Codex thread in the repository.
2. Supply the Linear issue identifier.
3. Codex fetches the issue once with relations.
4. Codex verifies only unclear/unresolved blockers.
5. Codex skips comments unless required by the issue.
6. Codex moves the issue to the configured Started status and verifies once.
7. Codex runs one concise Git status.
8. Codex reads root `AGENTS.md`, relevant nested instructions, exact referenced document sections, and likely paths only.
9. Codex implements and runs focused verification.
10. Codex pushes and creates the PR.
11. Codex updates Linear according to `completion_mode`.
12. Codex fetches one next ready issue, reports links/model guidance, and stops.

## Run the next issue when no ID is known

1. List a small page of issues in the active project's Ready status.
2. Choose the highest-priority candidate whose returned relations show no unresolved blocker.
3. Fetch only the chosen issue when more detail is needed.
4. Continue with the known-issue workflow.

Do not load the entire roadmap.

## Completion modes

### `pr-created`

```text
Ready -> In Progress -> Done after verification and PR creation
```

The user reviews and merges manually.

### `merge-gated`

```text
Ready -> In Progress -> In Review after PR creation -> Done after merge
```

## Mobile Remote

From ChatGPT mobile Remote, open the host Codex thread and use the prompt in `prompts/RUN_SPECIFIC_ISSUE_LEAN.md` or `prompts/MOBILE_REMOTE_RUN_NEXT_ISSUE.md`.

Use a new thread for the recommended next task rather than continuing the completed issue thread.
