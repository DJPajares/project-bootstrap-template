# Automatic Status Configuration

## Select a completion policy

Default for this package: `pr-created`.

### `merge-gated` — recommended when Done means merged

```text
Codex starts -> In Progress
PR opened/ready -> In Review
PR merged manually -> Done
```

### `pr-created` — matches the user's current workflow

```text
Codex starts -> In Progress
Implementation verified and PR created -> Done
User reviews and merges the PR manually later
```

Store the choice in `AGENTS.md` and use it consistently.

## Layer 1: agent-enforced Linear lifecycle

Codex must use Linear MCP to:

- fetch the issue and blockers
- move it to In Progress before editing
- verify the mutation
- post verification evidence and links
- apply the selected completion mode
- stop when Linear cannot be updated

This is the primary status layer for local Codex, Codex CLI, and the Codex VS Code extension.

## Layer 2: Linear coding-tool start automation

In Linear account Code & Reviews settings, optionally enable automatic movement to a Started status when opening or branching from an issue.

This is a convenience and fallback. Codex must still verify the status before implementation.

## Layer 3: GitHub integration

Connect the repository to Linear and include the Linear issue identifier in the branch name, PR title, or PR description.

For `merge-gated`, configure PR activity to move issues through In Progress, In Review, and Done.

For `pr-created`, disable or adapt merge-based Done transitions so they do not conflict with the agent's earlier completion mutation.

## Failure behavior

- Failed verification: remain In Progress and comment with the failed checks.
- Unexpected blocker: add blocker relation and return to a blocked/unstarted status.
- Failed Linear mutation: stop; do not claim progress or completion.
- Failed PR creation: do not mark Done in either completion mode.
