# ChatGPT mobile Remote: run the next ready Linear issue efficiently

Work in the currently connected local Codex repository.

Use `AGENTS.md` and Linear as the source of truth. Apply the lean workflow:

1. Start one fresh thread for this issue only.
2. List only a small set of Ready issues in the active Linear Project.
3. Choose the highest-priority candidate whose returned relations show no unresolved blocker.
4. Fetch only that issue with relations.
5. Do not fetch comments unless the issue requires them or was attempted/reopened.
6. Do not list statuses unless the mapping in `AGENTS.md` is missing or invalid.
7. Move the issue to In Progress and verify once.
8. Run `git status --short --branch` once.
9. Read `AGENTS.md` once, then only the issue's required document sections, nested instructions, and likely paths.
10. Preserve unrelated dirty files without inspecting them unless they overlap the task.
11. Implement only the issue scope.
12. Run focused verification first; run broad checks only when required or justified.
13. Push the branch and create a GitHub PR containing the Linear ID.
14. Update Linear according to `completion_mode` and verify once.
15. Fetch one next ready issue and return:
    - concise changes
    - concise verification results
    - completed Linear URL
    - GitHub PR URL
    - next Linear URL
    - next Codex/OpenAI recommendation and reasoning
    - next Claude/Anthropic recommendation and reasoning
16. Stop. Do not start the next issue in this thread.

Do not narrate routine successful tool calls.
