# Linear Workflow — Local Codex and Mobile Remote Primary

# Linear Automatic Workflow Reference

## Bootstrap phase

1. Resolve the team.
2. Search for an existing project.
3. Create or update the project.
4. Fetch team statuses and labels.
5. Create only missing labels.
6. Create milestones when phases are useful.
7. Create parent issues for large workstreams.
8. Create executable issues with stable bootstrap keys.
9. Add parent-child and blocker relations.
10. Verify project membership, status, priority, and duplicate keys.

## Required implementation lifecycle

### Start

1. Open an unblocked Todo/Ready issue.
2. Fetch its current state, blocker relations, and the team's actual Started status.
3. Move it to Started/In Progress through Linear MCP/API.
4. Re-fetch or otherwise verify the mutation succeeded.
5. If the mutation fails, stop before modifying the repository.
6. Read relevant docs and code.
7. Implement the stated outcome.

### Finish without review

1. Run all required verification.
2. Add a completion comment containing evidence.
3. Move the issue to the team's Completed/Done status.
4. Verify the status mutation succeeded.
5. Recommend the next unblocked issue.

### Finish with pull-request review

1. Run all required verification.
2. Open/link a PR containing the Linear issue identifier.
3. Add a completion comment containing evidence and the PR.
4. Move the issue to In Review.
5. Let configured GitHub/GitLab workflow automation move the issue to Done when the PR merges.
6. Verify the issue reached Done after merge.

### Failed verification

- Keep the issue In Progress.
- Comment with the exact failed command, error, and next action.
- Never move to Done.

### Blocked work

1. Add or verify the blocker relation.
2. Add a comment describing the exact missing decision or dependency.
3. Move to the team's blocked/backlog/unstarted state.
4. Do not expand scope to work around the blocker without approval.

## Recommended Linear settings

In Linear account/team settings, enable where available:

- On open in coding tool, move issue to started status.
- On git branch copy, move issue to started status.
- GitHub/GitLab workflow rules to move linked issues across PR states and to Done on merge.
- Parent auto-close when all required sub-issues are Done.

These native automations complement the explicit agent status calls. They do not replace the requirement that the agent verifies issue state.

## Branches and pull requests

- Prefer the branch name suggested by Linear.
- Otherwise include the issue identifier in the branch name.
- Include the issue identifier in the PR title or description.
- Link the PR to the issue.
- Use the team's review workflow rather than prematurely marking Done.

## Mobile workflow

Issue descriptions should include enough context to:

- inspect and prioritize work from the Linear mobile app
- ask ChatGPT, Codex, or another connected agent to start a specific issue
- see the issue move to In Progress immediately when execution begins
- review progress comments and verification evidence
- see PR-based tasks reach Done after merge without opening the repository

Long technical specifications remain in the repository and are linked from issues.

## Completion links and next-task handoff

After verification and PR creation:

1. Capture the full GitHub PR URL.
2. Fetch the current Linear issue URL.
3. Query the same project for ready, unblocked issues.
4. Select the next issue using dependencies first, then priority, then project ordering.
5. Fetch the selected next issue and read its `Suggested AI` section.
6. Add a completion comment using `templates/LINEAR_COMPLETION_COMMENT.template.md`.
7. Include the same links and model guidance in the user-facing final response.

Required fields:

- GitHub PR URL
- completed Linear issue URL
- next Linear issue URL
- next issue title
- next Codex/OpenAI model and reasoning
- next Claude/Anthropic model and reasoning
- recommendation rationale

Do not provide a guessed next model. Copy the recommendation from Linear.


## Execution-mode rule

Default to local Codex/mobile Remote. Codex Cloud is optional and must not be required unless selected explicitly.
