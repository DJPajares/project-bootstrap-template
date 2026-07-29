# Context-Efficient Task Execution

## Goal

Preserve the automatic Linear workflow while reducing unnecessary tool calls, document reads, command output, narration, and accumulated thread context.

## Most efficient entry point

Supply the exact Linear issue identifier whenever it is known:

```text
Run WDL-61 using the lean workflow.
```

An issue ID removes the need to search or list the roadmap.

## Startup budget

A normal bounded issue should usually need:

1. one issue fetch with relations
2. zero comment calls by default
3. zero status-list calls when `AGENTS.md` has the mapping
4. zero individual blocker fetches when relation statuses are complete
5. one status mutation and one verification fetch
6. one concise Git status
7. one `AGENTS.md` read
8. targeted document and source reads

Extra calls are allowed only when the returned information is incomplete or contradictory.

## Blocker policy

Trust a completed status included in the issue relation response. Fetch a blocker separately only when:

- relation status is absent
- relation status is not completed
- the blocker was recently reopened or appears inconsistent
- the implementation requires the blocker's technical output

Do not fetch every completed blocker merely to repeat its title and status.

## Comment policy

Skip comments by default. Read them when:

- the issue says `Read comments: yes`
- a prior attempt or reopen is recorded
- scope changed after issue creation
- an unresolved decision is known to exist there
- the issue description is insufficient and explicitly points to discussion

When comments are required, fetch the smallest useful page or latest relevant thread rather than all historical discussion.

## Document policy

### Always

Read root `AGENTS.md` once in a fresh issue thread.

### Conditional

- Read nested `AGENTS.md` only for touched subtrees.
- Read PRD headings named by the issue. Search for the heading, then open a bounded range.
- Read README command sections only when commands are not already provided.
- Read SKILL only for UI, layout, visual, interaction, component-system, responsive, or accessibility tasks.

### Avoid

- whole-document rereads
- repeated PRD reads for separate unrelated sections when a single targeted range is enough
- reading every repository guide “just in case”

## Repository discovery

Start from the issue's `Likely paths`. Use targeted search:

```bash
rg -n "SearchTerm" apps/api/src packages/db/src
rg --files apps/api/src | head -n 80
```

Read only the files and line ranges needed to understand the execution path.

Do not dump:

- lockfiles
- generated bundles
- build output
- full snapshots
- large JSON fixtures
- full test logs
- entire migration histories

unless the issue directly requires them.

## Dirty worktree

Run:

```bash
git status --short --branch
```

For unrelated changes, preserve and ignore them. Inspect their diff only when they touch a target file, can contaminate the PR, or create a safety ambiguity.

Do not automatically run `git log`, `git remote get-url`, and `git diff` for every dirty file.

## Verification ladder

Run:

1. focused changed tests
2. affected package checks
3. affected application checks
4. full repository checks only for cross-cutting work, release tasks, or explicit policy

Capture concise pass/fail results. Do not paste full successful logs into Linear or the final response.

## Completion and next task

After PR creation and Linear update:

1. query only the ready state in the active project
2. inspect a small candidate set
3. fetch the selected candidate once if relations/model guidance are not already present
4. report its URL and stored model guidance
5. stop

The next task starts in a fresh thread.

## Narration policy

No narration for routine successes. Speak during execution only for blockers, ambiguous decisions, mutation failures, risky dirty-file overlap, or required approval.

This reduces output tokens and keeps the active context focused on implementation evidence.
