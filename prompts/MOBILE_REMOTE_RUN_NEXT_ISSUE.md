# ChatGPT mobile Remote prompt: run the next Linear issue

Work in the currently connected Codex repository on this machine.

Read `AGENTS.md`, then use Linear as the task source of truth.

Run the highest-priority ready and unblocked issue from the active Linear Project:

1. Fetch the issue and blockers.
2. Move it to In Progress and verify the update.
3. Implement only its scope in the local repository.
4. Run verification.
5. Push a branch and create a GitHub PR with the Linear issue identifier.
6. Update Linear according to the repository's `completion_mode`.
7. Post the completion comment.
8. Show:
   - what changed
   - test and verification results
   - completed Linear issue URL
   - GitHub PR URL
   - next ready Linear issue URL
   - next issue's suggested Codex/OpenAI model and reasoning
   - next issue's suggested Claude/Anthropic model and reasoning

Stop after recommending the next issue. I will review and merge the PR manually.
