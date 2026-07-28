# Codex local prompt: run the next ready issue

Read `AGENTS.md` and the linked Linear Project.

1. Find the highest-priority executable issue that is ready, unblocked, and not already in progress.
2. Fetch the full issue, blocker relations, comments, and Suggested AI section.
3. Move the issue to the team's Started status and verify the update before editing code.
4. Use a branch containing the Linear issue identifier.
5. Implement only the issue scope.
6. Run all required verification.
7. Push the branch and create a GitHub PR containing the Linear issue identifier.
8. Update the issue according to `completion_mode` in `AGENTS.md`.
9. Add the required Linear completion comment.
10. Fetch the next ready issue and return:
    - what changed
    - verification results
    - completed issue URL
    - GitHub PR URL
    - next issue URL
    - next issue's Codex/OpenAI model and reasoning
    - next issue's Claude/Anthropic model and reasoning

Do not start a second issue automatically.
