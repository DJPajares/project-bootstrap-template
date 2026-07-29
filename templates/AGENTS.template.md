# AGENTS.md

## Project

- Linear team: `<team>`
- Linear project: `<project name or URL>`
- Execution mode: `codex-local-remote`
- Completion mode: `pr-created`
- Context mode: `lean`
- Session policy: `one-issue-per-thread`

## Linear status map

- Ready: `<actual status name>`
- Started: `<actual status name>`
- Review: `<actual status name or none>`
- Done: `<actual status name>`

Use these names directly. List team statuses only when this mapping is missing or rejected by Linear.

## Source of truth

- Linear owns issue state, priority, dependencies, assignee, and progress.
- `PRD.md` owns product and architecture decisions.
- `README.md` owns setup and commands.
- `SKILL.md` owns UI direction and is read only for relevant UI/visual work.
- Nested `AGENTS.md` files own subtree-specific rules.

## Lean issue startup

1. Use a fresh thread for one issue.
2. Fetch the target issue once with relations.
3. If no ID was supplied, list only a small set of ready candidates.
4. Trust blocker statuses returned with relations; fetch only unclear or unresolved blockers.
5. Read comments only when the issue says `Read comments: yes`, was attempted/reopened, or scope changed in comments.
6. Move the issue to the Started status and verify once.
7. Run `git status --short --branch` once.
8. Read this file once, then only the issue's required document sections and likely paths.
9. Do not read full PRD/README/SKILL files by default.
10. Do not narrate routine successful steps.

## Worktree safety

Preserve unrelated pre-existing changes. Do not inspect their full diff unless they overlap target files or create a safety concern. Do not include them in the task commit or PR.

## Implementation

- Work only within issue scope.
- Search before reading broad files.
- Use targeted ranges and cap command output.
- Avoid generated bundles, lockfiles, snapshots, and large logs unless required.
- Do not silently expand scope; update Linear when a new dependency is discovered.

## Verification

Run the narrowest applicable check first:

1. focused test
2. affected package lint/typecheck/test
3. affected app integration test
4. repository-wide checks only when required or justified

Do not mark Done when verification fails.

## Completion

1. Push a branch containing the Linear issue ID.
2. Create a GitHub PR.
3. Post one concise Linear completion comment.
4. Apply `completion_mode` and verify the final status once.
5. Fetch one next ready issue and copy its model guidance.
6. Report current issue URL, PR URL, concise changes, verification, risks, next issue URL, and next model guidance.
7. Stop. Do not start the next issue in this thread.
