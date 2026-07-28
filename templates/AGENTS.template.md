# AGENTS.md

## Purpose

Guide coding agents working on `<Project Name>`.

## Project snapshot

- Shapes: `<project shapes>`
- Stack: `<short stack summary>`
- Linear Project: `<project name and full URL>`
- GitHub repository: `<full URL>`
- Execution mode: `codex-local-remote`
- Completion mode: `pr-created`

## Sources of truth

- Product and architecture: `PRD.md`
- Setup and commands: `README.md`
- UI/UX constraints: `SKILL.md`, when present
- Task status, dependencies, priority, assignment, model guidance, and progress: Linear

## Mandatory Linear lifecycle

1. Fetch the assigned Linear issue, status, comments, and blockers.
2. Confirm blockers are resolved.
3. Move the issue to the team's Started status and verify the mutation.
4. Stop before editing when the status update fails.
5. Implement only the issue scope.
6. Run the required verification.
7. Push a branch and create or update a GitHub PR containing the Linear issue identifier.
8. Post the required completion comment.
9. Apply `completion_mode`:
   - `merge-gated`: move to In Review; merge automation moves it to Done.
   - `pr-created`: move to Done after verified implementation and successful PR creation.
10. Verify the final Linear mutation.
11. When blocked, add the blocker relation/comment and return the issue to the appropriate blocked or unstarted status.

## Project rules

- Do not create local task files.
- Do not change unrelated Linear issues.
- Do not claim a task started or completed until the Linear mutation succeeds.
- Use the same workflow from Codex app, mobile Remote, CLI, or VS Code.
- Do not require Codex Cloud unless the project explicitly selects it.

## Verification

- Run the narrowest relevant checks first.
- Run broader typecheck, lint, tests, and build checks when appropriate.
- Record commands and results in the Linear completion comment.

## Required completion report

After implementation and verification:

1. Obtain the full GitHub PR URL.
2. Update Linear according to `completion_mode`.
3. Fetch the next ready unblocked issue from the same Linear Project.
4. Read that issue's `Suggested AI` section.
5. Return and post:
   - what changed
   - verification results
   - remaining risks
   - completed Linear issue URL
   - GitHub PR URL
   - next Linear issue URL
   - next issue title
   - next issue's Codex/OpenAI model and reasoning
   - next issue's Claude/Anthropic model and reasoning
   - why it is the recommended next issue

Do not start the next issue automatically. If none is ready, say `No ready unblocked issue`, link the Linear Project, and list the blockers.
