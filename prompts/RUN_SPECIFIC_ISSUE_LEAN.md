# Run a specific Linear issue — lean workflow

Run `<ISSUE-ID>` in the current local repository.

- Use a fresh thread for this issue only.
- Fetch the issue once with relations.
- Trust completed blocker statuses returned by Linear; fetch only unclear or unresolved blockers.
- Skip comments unless the issue requires them or was attempted/reopened.
- Use the Linear status mapping in `AGENTS.md`; do not list statuses unless the mapping fails.
- Move the issue to In Progress and verify once before edits.
- Run only `git status --short --branch` for initial repository state.
- Read root `AGENTS.md` once, relevant nested instructions, and only the issue's required document sections and likely paths.
- Preserve unrelated dirty changes without diffing them unless they overlap target files.
- Implement only the issue scope.
- Run focused verification first and broad checks only when required.
- Push a branch containing the issue ID and create a GitHub PR.
- Update Linear according to `completion_mode` and verify once.
- Fetch one next ready issue and report its URL and stored Codex/Claude model guidance.
- Stop after the concise completion report.
- Do not narrate routine successful actions.
