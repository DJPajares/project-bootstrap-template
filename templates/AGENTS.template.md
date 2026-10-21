# AGENTS.md

> Authoring instructions: generate a structured operating guide, not a summary of this reference. Resolve every `{{placeholder}}` yourself and remove authoring guidance. Preserve the headings, numbered workflows, task schema, and completion formats that apply. Use short, separate rules rather than combining unrelated obligations into paragraphs. Do not impose a word limit or remove execution rules to shorten the file. Omit only genuinely inapplicable technical/release sections; a selected repository or tracker makes its workflow applicable. Preserve stronger existing rules and explain material conflicts rather than silently replacing them. This reference does not grant external-action permission.

## Project

{{PROJECT_NAME}} exists to {{OUTCOME_FOR_INTENDED_AUDIENCE}}.

- `PRD.md` owns approved product direction, scope, behavior, and decisions; proposals remain proposals.
- `AGENTS.md` owns agent execution and delivery rules. `CLAUDE.md` imports this file; maintain shared rules here once.
- {{TASK_SOURCE_OF_TRUTH_OR_AUTHORIZED_REQUEST}} owns work status and dependencies.
- {{TECHNICAL_DECISION_HOME}} owns accepted technical decisions; {{VALIDATION_EVIDENCE_HOME}} owns observed validation.
- Implementation and task status do not silently amend the product contract.

## Working Rules

- Follow accepted decisions; do not reopen settled scope without a material conflict or new evidence.
- Make the smallest coherent change that meets the request and acceptance criteria.
- Do not build deferred features, speculative infrastructure, or unused parallel systems.
- Inspect affected work before editing. Preserve unrelated changes and established conventions.
- Separate facts, assumptions, proposals, approved decisions, implementation status, and observed evidence.
- Keep credentials out of chat, files, logs, and commits; use supported secret-entry flows.
- Make routine reversible choices within authorization. Ask only about consequential uncertainty or a real blocker; continue independent work.
- {{PROJECT_SPECIFIC_WORKING_RULES_AND_DESIGN_CONTENT_OR_ACCESSIBILITY_CONVENTIONS_IF_APPLICABLE}}

## Tech Direction

Retain for software or technically constrained work. List the actual accepted technologies, dependency/package tooling, supported environments, and setup-command home. Label proposals. Preserve the existing stack; never substitute the source project's technologies.

{{ACCEPTED_TECHNICAL_CONSTRAINTS_AND_SETUP_REFERENCE}}

## Architecture Principles

Retain meaningful project boundaries as explicit bullets, not a generic “follow best practices” sentence.

{{AUTHORITATIVE_IDENTITY_STATE_DATA_OWNERSHIP_RELATIONSHIPS_PERMISSION_FAILURE_RECOVERY_AND_RESOURCE_BOUNDARIES_OR_PRD_REFERENCES}}

Where applicable: preserve independent relationships; enforce authorization at the authoritative boundary; define concurrency/retry integrity; distinguish owned data from external evidence; respect provider permissions, provenance, freshness, and aggregate cost. Do not introduce a second identity/state system or treat optional dependency failure as permission to fabricate results. Include only the actual project's applicable contracts.

## Task Workflow

### Requests made directly in chat

- Implement a direct implementation request within its authorized scope. Do not require issue creation or a brainstorming ceremony first.
- Create external tasks only when explicitly requested or when the user authorizes the concrete reviewed batch, regardless of task size.
- If the request references an existing task, use that task. Do not create a duplicate.
- For planning requests, use discuss → decide → draft tasks → approve creation. Reuse settled decisions and handle routine decomposition yourself. Task creation does not start implementation automatically.

### Task-backed execution

Task destination and scope: {{SELECTED_TRACKER_TEAM_PROJECT_OR_NO_TRACKER_SELECTED}}. Use only the confirmed destination. If none is selected, keep briefs in the conversation; do not force setup.

1. Read the existing task, accepted requirements, and actual blocking relationships. Create a new task first only if explicitly authorized.
2. Check the workspace and branch before editing. Resolve real blockers; do not guess readiness from issue order.
3. Move the task to the project's active-work state when this workflow and access permit it.
4. Read only the relevant requirement sections, decisions, implementation, and tests.
5. Implement only the task scope.
6. Run focused validation and the required project checks.
7. Self-review the complete change for scope, correctness, safety, and unsupported claims.
8. Commit and push through the repository's review workflow when applicable. Use the task's supplied branch name when available; otherwise use established project conventions.
9. Create or update the review artifact and its verified task-linking metadata. An attachment alone may not trigger lifecycle automation.
10. Move the task to the appropriate review state, not completion merely because a review was opened.
11. Identify the next approved, genuinely unblocked task when the selected workflow calls for a recommendation. Do not create a follow-up or change its status without authorization.
12. Stop for human review. Final task completion follows the actual integration/acceptance event below.

Status mapping, linking mechanism, and completion event: {{VERIFIED_LIFECYCLE_LINKING_AND_COMPLETION_CONVENTIONS_OR_RESOLVE_BEFORE_FIRST_TASK_WRITE}}.

For chat requests without a task, skip tracker reads/writes and next-task advancement. Still follow scope, branch, validation, self-review, and review rules. Verify needed access just in time; help restore it through supported sign-in/consent without requesting secrets or creating test resources. Reconcile partial writes before retrying.

## Task Structure

Every executable task uses these recognizable sections; keep entries specific rather than adding boilerplate:

### Description

The concrete change, affected behavior, and why it matters. Link the relevant approved requirements; do not copy the full PRD.

### Scope

Exact included work and nearby exclusions. Distinguish inspected implementation from proposed paths. Do not hide deferred features inside “foundation” work.

### Suggested Models & Reasoning

Recommend the smallest capable model and suitable reasoning effort for the target platform, with one brief reason. Resolve available names when drafting the task; do not hard-code a roster into standing rules. If availability cannot be verified, give a capability/reasoning recommendation and mark the exact model unverified. Delegate only when authorized.

### Acceptance Criteria

Numbered, independently verifiable conditions tied to the task's behavior, including material permission, failure, retry, and data-integrity boundaries. Avoid “works correctly,” “robust,” or “best practices” as criteria.

### Dependencies

Actual blocked-by/blocking task references or an explicit absence of blockers. Identify unresolved decisions, exactly what they block, and readiness. Use real tracker relationships where supported; do not serialize independent tasks or treat adjacent numbering as a dependency.

### Execution Context and Verification

Relevant requirement/decision references, known affected areas, existing components to reuse, and focused checks. Include actual commands only when grounded in the project; otherwise state what must be inspected or established. Do not repeat global governance text in every issue.

### Manual Test

Include when a person can meaningfully verify the change. Give concrete steps, inputs, and expected results; for interactive work include important empty, denied, or recovery behavior. Omit for tasks without a meaningful manual check rather than inventing one.

The [task authoring reference](TASK.template.md) supplies the full shape. In the generated project, embed the structure above or link an actual delivered local reference; do not leave this template-relative link unresolved.

## Repository Rules

Retain when version control/review applies; resolve the actual platform, destination, integration branch, naming, and review conventions.

- Repository and integration branch: {{REPOSITORY_AND_INTEGRATION_BRANCH}}.
- Never commit or push directly to the protected integration branch. Check the current branch before the first edit and immediately before every commit and every push; an earlier session check is not proof of the current branch.
- Use an isolated change branch. Preserve unrelated local work; do not reset or move it without authorization.
- Deliver changes through {{REVIEW_ARTIFACT_AND_TASK_LINKING_POLICY}} with the concrete problem, resulting behavior, validation, material gaps, and meaningful manual checks.
- Use the selected platform's verified issue/branch/linking conventions. Do not assume a keyword or attachment automatically updates status.
- Never enable automatic merge. A human reviews and merges, or explicitly authorizes the applicable integration action.
- Mark an implementation task complete only at {{TASK_COMPLETION_EVENT}}. Review readiness is not integration, release, or final acceptance.

## Change Notes and Versioning

Retain for versioned or user-facing software/products; preserve established formats and commands. Do not invent catalogs, manifests, version numbers, or release tooling that do not exist.

- Decide before final validation whether the change gives users a meaningful accessible improvement or fix. Include its note with the same change when applicable; internal-only work normally needs no user-facing note.
- Keep notes in {{CHANGE_NOTE_HOME_OR_SELECTED_SETUP_GUIDANCE}}. Describe user benefits in plain language. Preserve shipped history and stable identifiers when used.
- State in the review whether notes were added or unnecessary and why. Follow existing declaration/check formats exactly when present; validate the live review metadata separately from a local catalog when policy requires it.
- Version policy and released units: {{ACTUAL_VERSION_POLICY_OR_CLEARLY_PROPOSED_DEFAULT}}. Bump only affected units under that policy and recheck against the integration baseline after rebasing.
- Publication/deployment requires its own authorization and evidence, including applicable configuration, monitoring, resource, rollout, and recovery checks.

## Completion Response

Keep responses short and structured. Use actual links and observed results; never fill missing fields with invented progress.

For chat-originated work without a tracker task: briefly state the change and validation, include the review link if created, and disclose material gaps. Omit Current/Next task links and do not suggest or advance backlog work unless requested.

For task-backed execution, use:

### Current

- Review: {{ACTUAL_REVIEW_LINK_OR_PRECISE_BLOCKER}}
- Task: {{ACTUAL_CURRENT_TASK_LINK}}
- Validation: {{SHORT_OBSERVED_RESULT_AND_MATERIAL_GAPS}}

### Next

- Task: {{ACTUAL_NEXT_APPROVED_UNBLOCKED_TASK_LINK_OR_NONE_IDENTIFIED}}
- Model: {{CURRENTLY_VERIFIED_MODEL_REASONING_PLATFORM_OR_UNVERIFIED_CAPABILITY_RECOMMENDATION}}
- Reason: {{ONE_SHORT_SENTENCE_OR_ACTUAL_BLOCKER}}

These are output field descriptions, not unresolved placeholders to leave in generated rules. Write the final project's response pattern with descriptive field labels or code-formatted examples that require actual values at execution time. Recommend only from accessible approved work; missing access or no ready work must be stated, not filled with a fictional “next task.”

## Context Efficiency

- Read relevant requirement sections and affected code; avoid repeated broad scans.
- Prefer focused checks before required broader suites.
- Keep one authoritative home per fact. Do not mirror the backlog locally or copy the PRD into issues.
- Keep chat updates concise. Remove repetition from instructions without deleting operational rules, numbered workflows, task fields, or response formats.

## Testing

- Validate observable behavior and important business rules, permissions, integrity, concurrency, and recovery contracts.
- Exercise changed screens/workflows in the available browser or relevant runtime, including applicable accessibility and failure states. State when the runtime is unavailable.
- Add focused tests for meaningful behavior, not incidental implementation details. Do not introduce an end-to-end suite unless requested or required by an accepted project testing policy.
- Run the project's actual adopted linting, type, build, and focused test commands from {{VERIFIED_COMMAND_HOME}} as applicable. Do not invent a toolchain or claim a documented command ran.
- For documentation, check consistency, links, placeholders, and representative scenarios. Document review is not runtime validation.
- Record passed, failed, blocked, and untested checks with artifact/version, environment, date, and coverage. Historical checks do not validate a changed artifact.
- Missing required evidence prevents a completion claim; report a draft or blocker with its exact gap.

## Human Control

{{DECISION_OWNER}} is the final decision-maker for consequential product gates, architecture changes, scope changes, spending, review approval, integration, and release/deployment. Respect authorization already given. Prepare concrete work and evidence before final approval; do not ask again for routine work already authorized.
