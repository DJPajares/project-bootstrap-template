# PROJECT_BOOTSTRAP_V5.md

## Version

`v5.4`

## Purpose

Use this file as a reusable instruction document for turning any raw software-project idea into:

```text
PRD.md
AGENTS.md
README.md
SKILL.md                     # only when meaningful UI exists
```

and a complete execution plan inside one dedicated Linear Project:

```text
Linear Project
Linear milestones            # optional, phase-based
Linear parent issues          # optional workstreams
Linear executable issues
Linear labels
Linear priorities
Linear blocker relationships
Linear progress comments
```

Do not create local task files. Linear is the only task-status source of truth.

---

# 1. Default Execution Policy

Generate the repository with these defaults unless the user explicitly chooses otherwise:

```text
execution_mode: codex-local-remote
completion_mode: pr-created
context_mode: lean
session_policy: one-issue-per-thread
```

Supported execution modes:

```text
codex-local-remote    # default: Codex app/CLI on a host, optionally controlled from mobile Remote
codex-vscode          # Codex VS Code extension on the same local repository
claude-local          # Claude Code using the same Linear roadmap
codex-cloud           # optional; only when explicitly requested
```

Completion modes:

```text
pr-created            # default: verified implementation + PR means the agent task is Done
merge-gated           # PR means In Review; merge automation means Done
```

Do not add Codex Cloud to the mandatory setup unless it is explicitly selected.

## Setup automation boundary

Automate document publication, Linear roadmap creation, issue updates, branches, PR creation, completion comments, and next-task selection when connected tools permit.

Treat repository/account creation, OAuth approval, local folder access, GitHub-to-Linear configuration, and mobile Remote authorization as one-time manual or semi-automated steps. Do not claim these can always be completed without the user.

---

# 2. Core Principles

- Be project-agnostic and provider-agnostic.
- Generate project-specific documents and Linear issues, not copied boilerplate.
- Keep Linear as the only implementation-task state.
- Keep `AGENTS.md` short, operational, and context-efficient.
- Keep issues small, dependency-aware, and independently verifiable.
- Prefer vertical slices over layer-wide tasks.
- Ask only when a missing answer materially changes architecture, scope, data, UX, security, deployment, or team ownership.
- Record reasonable assumptions for small gaps.
- Avoid duplicate content across repository documents, Linear project descriptions, and issues.
- Do not create duplicate Linear projects or issues when rerun.
- Use the minimum sufficient model capability and reasoning budget for each issue.
- Optimize agent context as a first-class project requirement.

---

# 3. Project Shape

Infer one or more shapes:

```text
web-ui
mobile-ui
desktop-ui
api-service
full-stack-product
cli-tool
library-sdk
data-pipeline
ai-system
automation-integration
infrastructure-platform
```

Only generate relevant documents, milestones, workstreams, labels, and issues.

---

# 4. Repository Output Contract

Generate only these planning files unless another non-task document is clearly required:

```text
<project-root>/
  PRD.md
  AGENTS.md
  README.md
  SKILL.md                   # meaningful UI only
  <area>/AGENTS.md           # only when an area has distinct commands or boundaries
```

Do not generate:

```text
.devtool/features/
tasks/
TASKS.md
TODO.md
local kanban files
local task-state mirrors
```

## Nested AGENTS rule

Use a short root `AGENTS.md` for global workflow. Add nested `AGENTS.md` files only where a subtree has materially different commands, architecture, safety rules, or UI boundaries.

Examples:

```text
apps/web/AGENTS.md
apps/api/AGENTS.md
packages/db/AGENTS.md
```

Do not duplicate root instructions into every nested file.

---

# 5. Linear Project Construction

## 5.1 Resolve once, reuse throughout bootstrap

During one bootstrap run:

1. Resolve the Linear team once.
2. Fetch the team's workflow statuses once.
3. Resolve reusable labels once.
4. Search for the matching project once.
5. List existing project issues once and index their bootstrap keys.
6. Create or update issues from the in-memory task graph.

Do not repeat project, status, label, or full issue-list calls for every issue.

## 5.2 One project per independently planned product

A monorepo normally remains one Linear Project when its applications form one product. Use labels, milestones, and parent issues for internal areas.

Create separate projects only for independent roadmaps, owners, or release lifecycles.

## 5.3 Team resolution

Resolve the team in this order:

1. Explicit user input.
2. Existing project team.
3. Unambiguous repository/workspace context.
4. Ask exactly one focused question.

## 5.4 Project idempotency

Before creating a project, search exact and normalized names. Reuse a clear match. On rerun, update missing or materially outdated items rather than duplicating them.

## 5.5 Milestones and parent issues

Use milestones only for meaningful phases. Use parent issues only for substantial workstreams containing multiple executable issues.

## 5.6 Stable issue identity

Add this metadata to every generated issue:

```text
---
Bootstrap key: `feature.search-api`
Bootstrap version: `v5.4`
```

Use stable semantic keys. Match by bootstrap key first and exact title/project second.

---

# 6. Context-Efficient Linear Issue Contract

Every executable issue must contain enough context to run without loading the whole project, but must not duplicate the PRD.

Use this structure:

```md
# Outcome

<One independently verifiable result.>

## Scope

- <Required work>

## Out of scope

- <Nearby work intentionally excluded>

## Acceptance criteria

- [ ] <Specific result>
- [ ] <Specific result>

## Execution context

- Context budget: `lean | standard | deep`
- Required documents:
  - `AGENTS.md`
  - `PRD.md#<specific heading>` only when needed
  - `SKILL.md#<specific heading>` only for relevant UI/visual work
- Likely paths:
  - `<path or package>`
- Read comments: `no` by default
- Prior attempt/reopened: `no` by default

## Dependencies

Use Linear blocker relations. Do not duplicate full blocker descriptions here.

## Suggested AI

- Capability profile: `<profile>`
- Reasoning requirement: `<low | medium | high | xhigh>`
- Codex/OpenAI recommendation: `<current compatible model or resolve at execution time>`
- Claude/Anthropic recommendation: `<current compatible model or resolve at execution time>`
- Selection rationale: `<task-specific reason>`

## Verification

```bash
<narrow task-specific commands>
```

---
Bootstrap key: `<stable-key>`
Bootstrap version: `v5.4`
```

## Context budget meanings

### `lean`

Default for bounded issues. Read the issue, `AGENTS.md`, exact referenced sections, and likely paths only.

### `standard`

Use for moderate cross-file implementation. Read a few related modules and one or two relevant design/architecture sections.

### `deep`

Reserve for architecture, security, migrations, cross-package refactors, and ambiguous systems work. Deep does not mean read every file; it means broader targeted investigation is justified.

## Comment policy

Set `Read comments: yes` only when:

- newer comments modify scope or acceptance criteria
- the issue was attempted or reopened
- a decision exists only in comments
- an unresolved discussion materially affects implementation

Do not fetch comment history by default.

## Document policy

- `AGENTS.md`: always read once per fresh issue thread.
- `PRD.md`: read only named headings or searched ranges needed by the issue.
- `README.md`: read only setup/command sections when the required commands are not already in `AGENTS.md` or the issue.
- `SKILL.md`: read only for UI, visual, interaction, design-system, responsive, or accessibility work.
- Nested `AGENTS.md`: read only for directories the task will touch.

---

# 7. Lean Automatic Status Workflow

The bootstrap must store the resolved Linear status names in generated `AGENTS.md`:

```text
linear_team: <team>
linear_project: <project name or URL>
status_ready: <actual status name>
status_started: <actual status name>
status_review: <actual status name or none>
status_done: <actual status name>
```

This prevents listing issue statuses at the beginning of every task.

## Start transition

Before editing repository files:

1. Fetch the target issue once with relations.
2. If no issue ID was supplied, list only a small page of ready candidates and choose one.
3. Trust blocker statuses included in the relation payload.
4. Fetch an individual blocker only when its state is missing, unclear, not completed, or its implementation details are required.
5. Fetch comments only when the issue's `Read comments` or `Prior attempt/reopened` flag requires it.
6. Move the issue to `status_started`.
7. Verify the mutation with one lightweight re-fetch.
8. Run one concise worktree check: `git status --short --branch`.
9. Read `AGENTS.md` once and then only the issue's required context.
10. Begin implementation.

Do not list workflow statuses unless the stored mapping is missing or a mutation fails because the status no longer exists.

Do not run `git log`, inspect remotes, or diff unrelated dirty files unless a branch/remote problem or file collision requires it.

If the status mutation fails, stop and report the failure.

## Completion transition

1. Run narrow issue-specific verification first.
2. Run broader checks only when the change is cross-cutting, `AGENTS.md` requires them, or the narrow checks indicate risk.
3. Create and push a branch containing the Linear issue identifier.
4. Create the GitHub PR using local `git` and `gh` where available.
5. Add one concise Linear completion comment.
6. Update status according to `completion_mode`.
7. Verify the final mutation once.
8. Fetch one next ready issue and copy its model guidance.
9. Report links and stop. Do not begin the next issue in the same thread.

## Blocked transition

When blocked unexpectedly:

1. Add or verify the blocker relation.
2. Add one concise comment with the exact missing dependency or decision.
3. Move the issue to the configured unstarted/blocked state.
4. Stop. Do not silently broaden scope or work around the blocker.

---

# 8. Context and Tool Budget Rules

## 8.1 One issue per thread

Start each Linear issue in a fresh Codex thread. The completion report recommends the next issue but must not start it.

## 8.2 Minimal narration

Narrate only:

- an unresolved blocker
- an unexpected dirty-file collision
- an authorization/status mutation failure
- a materially ambiguous requirement
- a risky change requiring user choice
- final completion results

Do not narrate routine successful fetches, reads, commands, or status transitions.

## 8.3 Targeted repository discovery

Prefer:

```bash
rg -n "symbol|route|table" likely/path
rg --files likely/path | head -n 80
sed -n '<start>,<end>p' file
```

Avoid reading entire directories, generated bundles, lockfiles, snapshots, logs, or large documents unless directly required.

Cap command output. Use filters, path scopes, line ranges, and test selectors.

## 8.4 Dirty worktree policy

Run `git status --short --branch` once at startup.

For unrelated pre-existing changes:

- preserve them
- exclude them from the task branch/commit when possible
- do not inspect their full diff unless they overlap a target file or create safety ambiguity
- mention them only when they affect implementation or PR cleanliness

## 8.5 Verification ladder

Use this order:

1. changed unit or focused test
2. affected package/typecheck/lint
3. affected app integration test
4. repository-wide checks only when required or justified

Do not run every suite after every small task.

## 8.6 MCP minimalism

For ordinary local execution:

- Keep Linear MCP available for issue reads/writes.
- Use local filesystem, `git`, and `gh` for repository and PR work.
- Use design-system, browser, database, deployment, or other MCP servers only for tasks that require them.
- Avoid invoking overlapping tools for the same information.

## 8.7 Re-read prevention

Do not reread a document or source file in the same thread unless:

- it changed
- the earlier read omitted the required range
- a failing check points back to it
- the current implementation creates a new ambiguity

---

# 9. Model and Reasoning Efficiency

Capability profiles remain canonical because provider model names change.

```text
deep-architecture
implementation-general
fast-bounded
visual-design
research-analysis
verification-review
```

Use the minimum sufficient capability:

- `fast-bounded`: clear, isolated, mechanical, or documentation/config work
- `implementation-general`: ordinary non-trivial implementation
- `deep-architecture`: architecture, auth/security, migrations, concurrency, idempotency, broad refactors
- `visual-design`: material visual judgment or multimodal UI work
- `research-analysis`: unfamiliar provider/standard/integration investigation
- `verification-review`: independent security, accessibility, architecture, or release review

Reasoning guidance:

- `low`: mechanical work with explicit steps
- `medium`: normal bounded implementation
- `high`: non-trivial integration, data, state, testing, or design judgment
- `xhigh`: rare; ambiguous high-risk architecture, security, migration, or cross-system work

Do not assign the strongest model or `xhigh` by default. Exact model names are optional snapshots; capability profile and reasoning requirement remain the long-lived source of truth.

---

# 10. Issue Decomposition and Dependencies

Generate small vertical slices with one clear outcome, 3-8 testable acceptance criteria, explicit out-of-scope notes, and real blocker relations.

Create a blocker only when one issue cannot reasonably be completed first. Do not serialize independent work.

Use priorities honestly:

```text
Urgent  production/security/release emergency
High    critical path, security, data integrity, primary workflow blocker
Medium  normal MVP work
Low     optional polish or deferred optimization
```

Do not mark every issue High.

---

# 11. UI and TasteSkill Policy

For meaningful UI, generate a project-specific `SKILL.md` after a contextual design read. Do not load `SKILL.md` during backend, database, infrastructure, or documentation tasks unless the issue explicitly requires UI impact review.

Keep component-system boundaries explicit. Use one system per UI tree unless the architecture intentionally isolates separate surfaces.

---

# 12. Required Completion Comment and Final Report

The Linear completion comment and user-facing final report must be concise.

```md
## Completed

- Linear: <current issue URL>
- GitHub PR: <PR URL>
- Changed:
  - <concise outcome>
- Verification:
  - `<command>` — <result>
- Risks: <none or concise note>

## Next ready task

- Linear: <next issue URL>
- Title: <next issue title>
- Codex/OpenAI: <copied recommendation and reasoning>
- Claude/Anthropic: <copied recommendation and reasoning>
- Why next: <one sentence based on priority and blockers>
```

Do not include the full diff, full issue description, complete test logs, or a roadmap dump.

When no ready issue exists, link the Linear Project and state the unresolved blocker(s) concisely.

---

# 13. Final Bootstrap Output

After running this bootstrap, report:

- project shape(s)
- repository documents created or updated
- Linear Project URL
- milestone count
- parent issue count
- executable issue count
- first ready issue URL
- first issue capability/model guidance
- assumptions
- open questions
- status-name mapping stored in `AGENTS.md`
- confirmation that issue context packs were generated

The Linear issues are the core implementation output. Do not stop after generating documents.
