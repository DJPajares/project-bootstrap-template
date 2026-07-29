# Upgrade an existing Linear project to the v5.4 lean workflow

Update the current repository and its existing Linear Project to the v5.4 context-efficient workflow.

Do not recreate the Linear Project or duplicate issues.

1. Update root `AGENTS.md` with:
   - `execution_mode`
   - `completion_mode`
   - `context_mode: lean`
   - `session_policy: one-issue-per-thread`
   - actual Linear Ready, Started, Review, and Done status names
   - lean startup, verification, worktree, and completion rules
2. Add nested `AGENTS.md` files only where a subtree has materially different commands or boundaries.
3. List existing project issues once and index them by bootstrap key or identifier.
4. For each open executable issue, add or update an `Execution context` section containing:
   - context budget
   - exact required document headings
   - likely paths/packages
   - `Read comments: no` unless history is materially required
   - prior-attempt/reopened flag
   - focused verification commands
5. Preserve issue titles, identifiers, statuses, priorities, assignees, comments, and blocker relations.
6. Do not rewrite completed issues unless their guidance is still used as a dependency reference.
7. Replace overpowered model guidance with the minimum sufficient capability and reasoning level, while keeping provider-specific names optional and current.
8. Do not create local task files.
9. Report:
   - repository files changed
   - number of Linear issues updated
   - number skipped and why
   - stored status mapping
   - first ready issue URL

Use batched discovery: resolve team, statuses, project, labels, and existing issues once rather than refetching them per issue.
