# PROJECT_BOOTSTRAP_V5.md

## Version

`v5.3.1`

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


# Execution Mode and Setup Policy

Default to:

```text
execution_mode: codex-local-remote
```

This means Codex runs on the user's laptop, devbox, remote SSH host, or VS Code environment, while ChatGPT mobile Remote can control supported Codex threads.

Supported modes:

```text
codex-local-remote    # default: Codex app/CLI on a host, controlled from desktop or mobile Remote
codex-vscode          # Codex VS Code extension on the same local repository
claude-local          # Claude Code using the same Linear roadmap
codex-cloud           # optional; only when explicitly selected
```

Do not add Codex Cloud to the mandatory setup when `codex-local-remote` or `codex-vscode` is selected.

## Completion mode

Store one project-level policy in `AGENTS.md`:

```text
completion_mode: merge-gated
```

or:

```text
completion_mode: pr-created
```

- `merge-gated`: agent moves the issue to In Review after opening the PR; Git integration moves it to Done after manual merge.
- `pr-created`: agent moves the issue to Done after implementation, verification, and PR creation; the user reviews and merges later.

Use `pr-created` when applying this package for the current user. For other users or projects, ask one focused question only when the preferred completion meaning is unclear.

## Setup automation rule

Automate document publication, Linear roadmap creation, issue updates, branches, PR creation, completion comments, and next-task selection when connected tools permit them.

Treat repository creation, account authorization, OAuth consent, local folder access, GitHub-to-Linear workspace configuration, and mobile Remote device authorization as one-time manual or semi-automated setup. Do not claim those steps can always be completed without user action.

---

# 1. Core Principles

- Be project-agnostic. Never assume a new project resembles the project that informed this bootstrap.
- Be agent-agnostic. Route work by capabilities and reasoning needs, not by one model provider.
- Generate project-specific documents and issues rather than copying generic boilerplate blindly.
- Ask only when a missing answer materially changes architecture, scope, data model, UX direction, security, deployment, or the required Linear team.
- Make reasonable assumptions for small gaps and record them clearly.
- Avoid duplicate information across `PRD.md`, `README.md`, `AGENTS.md`, `SKILL.md`, Linear project descriptions, and issue descriptions.
- Keep `AGENTS.md` short and token-efficient.
- Keep implementation status, priority, assignee, dependencies, and progress only in Linear.
- Keep issues small enough to complete and verify independently.
- Prefer vertical slices over broad layer-only tasks.
- Do not create duplicate projects or issues when the bootstrap is rerun.

---

# 2. Project Shape

Infer one or more project shapes from the idea:

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

A project may combine shapes. Example:

```text
full-stack-product + mobile-ui + ai-system
```

Only generate sections, milestones, workstreams, and issues relevant to the inferred shape.

## Shape emphasis

### Web, mobile, or desktop UI

Focus on users, flows, navigation, component strategy, responsive/adaptive behavior, accessibility, states, design system, data access, testing, and distribution.

### API service or full-stack product

Focus on contracts, data model, authorization, validation, error behavior, integrations, observability, frontend/backend boundaries, and end-to-end flows.

### CLI or library/SDK

Focus on public interfaces, commands, configuration, compatibility, versioning, errors, documentation, packaging, test matrices, and release automation.

### Data pipeline or AI system

Focus on inputs, provenance, validation, normalization, evaluation, idempotency, privacy, cost controls, observability, retries, human review, and reproducibility.

### Automation or integration

Focus on triggers, credentials, external contracts, rate limits, retries, idempotency, reconciliation, failure recovery, auditability, and operational ownership.

### Infrastructure or platform

Focus on environments, isolation, configuration, secrets, deployment, rollback, observability, reliability targets, access controls, and runbooks.

---

# 3. Repository Output Contract

Generate only these local planning files unless the project clearly requires another non-task document:

```text
<project-root>/
  PRD.md
  AGENTS.md
  README.md
  SKILL.md                   # meaningful UI only
```

Do not generate:

```text
.devtool/features/
tasks/
TASKS.md
TODO.md
local kanban files
local issue mirrors
```

A repository may contain links to the Linear Project and key issues, but it must not duplicate task status.

---

# 4. Linear Is The Task System

## 4.1 One project per product

Create one Linear Project for each independently planned and releasable software project.

A monorepo with multiple applications normally remains one Linear Project when the applications form one product. Use labels, milestones, or parent issues to separate applications.

Create separate Linear Projects only when products have independent roadmaps, owners, or release lifecycles.

## 4.2 Team resolution

A Linear team is required to create issues and normally a project.

Resolve the team in this order:

1. Team explicitly provided by the user.
2. Team associated with an existing project the user asked to reuse.
3. Unambiguous team inferred from the connected workspace and repository context.
4. Ask exactly one focused question: `Which Linear team should own this project?`

Do not guess when multiple plausible teams exist.

## 4.3 Project idempotency

Before creating a project:

1. Search Linear for the exact or normalized project name.
2. Reuse the existing project when it clearly represents the same software project.
3. Fetch its details before adding milestones or issues.
4. Create a new project only when no matching project exists.

When rerunning the bootstrap, update missing or outdated planning items rather than recreating everything.

## 4.4 Project description

Keep the Linear Project description concise. Include:

- one-paragraph product summary
- project shapes
- MVP outcome
- repository link when available
- links to `PRD.md`, `README.md`, and `SKILL.md` when available
- major constraints
- bootstrap version

Do not paste the full PRD into the project description.

## 4.5 Milestones

Use milestones only when the project has meaningful phases. Common examples:

```text
Foundation
MVP Core
Integration
Hardening
Launch
```

Do not force five milestones onto a small library or script. A small project may need no milestones.

## 4.6 Parent issues

Use parent issues for substantial workstreams that contain multiple executable child issues. Examples:

```text
Authentication and access
Primary user workflow
Data ingestion
Dashboard experience
Release hardening
```

Do not use a parent issue as a task that an agent should implement directly unless it has a clear standalone outcome.

## 4.7 Executable issues

Each executable issue must:

- have one clear outcome
- belong to the dedicated Linear Project
- use the correct team
- be independently verifiable
- have explicit acceptance criteria
- declare real blockers through Linear issue relations
- contain enough context for execution from desktop or mobile
- include a capability-based agent recommendation
- avoid duplicating the entire PRD

---

# 5. Linear Structure Mapping

Use this mapping:

| Planning concept | Linear representation |
|---|---|
| Software project | Project |
| Delivery phase | Milestone, when useful |
| Epic/workstream | Parent issue |
| Executable task | Issue |
| Dependency | `blocked by` / `blocks` relation |
| Work category | Label |
| Importance | Priority field |
| Current state | Team issue status |
| Progress evidence | Issue comments |
| Weekly/checkpoint summary | Project status update |
| Detailed supplementary brief | Project or issue document, only when needed |

Do not emulate dependencies using text alone when Linear relations are available.

---

# 6. Automatic Status Workflow

Fetch the target team's statuses and map them semantically rather than assuming exact names. Resolve the actual status IDs/names before implementation.

Expected semantic flow:

```text
Backlog -> Todo/Ready -> In Progress -> In Review -> Done
```

For work without a review or merge gate:

```text
Backlog/Todo -> In Progress -> Done
```

Optional terminal states:

```text
Canceled
Duplicate
```

## Mandatory agent mutations

The coding agent must update Linear itself through MCP/API calls. These are execution steps, not optional reporting guidance.

### Start transition

Before changing repository files:

1. Fetch the issue, status, project, and blocker relations.
2. Confirm all blockers are resolved.
3. Move the issue to the team's first Started-category status, normally `In Progress`.
4. Re-fetch or verify the mutation succeeded.
5. Only then begin implementation.

If the status mutation fails, stop and report the failure. Do not implement code while Linear still shows the issue as Backlog or Todo.

### Completion transition

After implementation:

1. Run the required verification.
2. Add the completion comment with commands, results, risks, and next issue.
3. Read `completion_mode` from `AGENTS.md`.
4. For `pr-created`, move the issue to the Completed-category status after verification and successful PR creation.
5. For `merge-gated`, move the issue to `In Review`; configure GitHub/GitLab automation to move it to `Done` after merge.
6. Verify the final status mutation succeeded.

Do not mark Done when verification fails. Leave the issue In Progress and comment with the failure.

### Blocked transition

When blocked unexpectedly:

1. Add or verify the blocker relation.
2. Comment with the exact missing dependency or decision.
3. Move the issue to the team's appropriate blocked, backlog, or unstarted status.
4. Do not silently work around the blocker or mark the issue Done.

## Linear-native automation

Where available, also configure:

- `On open in coding tool, move issue to started status` for Codex/IDE launches.
- GitHub/GitLab issue-status automation so branch/PR activity advances the issue and merge moves it to Done.
- Parent auto-close so a parent issue completes when all required sub-issues are Done.

The explicit agent mutations remain the fallback and verification layer even when native automations are enabled.

---

# 7. Priority Rules

Map priority to the target Linear workspace's standard priority values:

```text
Urgent
High
Medium
Low
No priority
```

Guidance:

- Urgent: production incident, security exposure, release-blocking failure.
- High: critical path, foundational blocker, auth/security, data integrity, primary workflow.
- Medium: normal MVP feature or important quality improvement.
- Low: optional polish, convenience, deferred optimization.

Do not mark every issue High.

---

# 8. Label Strategy

Reuse existing labels before creating new ones.

Keep the label set small and useful.

## Recommended groups

### Type

```text
type:feature
type:bug
type:chore
type:spike
type:qa
type:docs
```

### Area

Create only areas relevant to the project:

```text
area:frontend
area:mobile
area:backend
area:api
area:database
area:auth
area:design
area:data
area:ai
area:integration
area:infrastructure
area:testing
area:release
```

### Optional capability

Only when filtering agent work is useful:

```text
agent:deep
agent:balanced
agent:fast
agent:visual
agent:review
```

Do not use model-provider names as required labels. Models change; capabilities remain useful.

---

# 9. Stable Issue Identity And Reruns

Linear generates issue identifiers. The bootstrap still needs a stable logical key to avoid duplicates.

Add this unobtrusive metadata at the bottom of every generated issue description:

```text
---
Bootstrap key: `foundation.project-scaffold`
Bootstrap version: `v5.3.1`
```

Before creating an issue:

1. Search or list issues in the target project.
2. Match the bootstrap key when available.
3. Fall back to exact title plus project when needed.
4. Update the existing issue if scope or acceptance criteria changed materially.
5. Never create a duplicate solely because the title changed slightly.

Bootstrap keys must be semantic, stable, and project-local:

```text
foundation.project-scaffold
quality.tooling-baseline
auth.session-flow
feature.search-api
feature.search-ui
release.production-readiness
```

---

# 10. Issue Decomposition

Generate small vertical slices.

Good:

```text
Project scaffold and workspace commands
Database connection and migration baseline
Health endpoint with API test
Search contract and validation
Search endpoint and provider adapter
Search screen states and API integration
End-to-end search smoke test
```

Avoid:

```text
Build backend
Build frontend
Add database
Do testing
Finish app
```

## Dependency discipline

Create a blocker relation only when one issue cannot reasonably be completed before another.

Examples:

```text
Database migration baseline blocks persistence service.
API contract blocks client integration.
Auth middleware blocks protected endpoints.
Theme contract blocks theme implementations.
```

Do not create a fully serial chain when work can proceed in parallel.

## Acceptance criteria

Each issue normally has 3-8 acceptance criteria. Criteria must be specific, observable, and limited to the issue.

Include verification commands or expected evidence when practical.

---

# 11. Capability-Based Agent Routing

Every issue includes a suggested capability profile and reasoning level.

## Profiles

### `deep-architecture`

Use for:

- architecture and major boundaries
- auth and security
- migrations and data integrity
- complex concurrency or idempotency
- cross-package refactors
- ambiguous product/technical tradeoffs

Typical reasoning: `high` or `xhigh`.

### `implementation-general`

Use for:

- ordinary features
- forms and endpoints
- state management
- integration work
- non-trivial tests
- moderate refactors

Typical reasoning: `medium` or `high`.

### `fast-bounded`

Use for:

- straightforward configuration
- small documentation changes
- mechanical migrations
- simple static UI
- isolated test additions

Typical reasoning: `low` or `medium`.

### `visual-design`

Use for:

- design reads
- interaction and layout direction
- theme systems
- visual QA
- branded/editorial UI

Typical reasoning: `high`; use multimodal capability when screenshots or visual references exist.

### `research-analysis`

Use for:

- unfamiliar integrations
- provider comparison
- standards or dependency research
- evaluation design
- investigation/spikes

Typical reasoning: `high`.

### `verification-review`

Use for:

- code review
- security review
- accessibility audit
- test-gap analysis
- release readiness

Typical reasoning: `high` or `xhigh` for high-risk work.

## Provider mapping

Do not hardcode one model family in generated issues unless the user requests it.

Hosts may map profiles to current models, for example:

```text
deep-architecture      -> strongest available reasoning/coding model
implementation-general -> balanced coding model
fast-bounded           -> fast low-cost model
visual-design          -> strong multimodal design/coding model
research-analysis      -> strong research/reasoning model
verification-review    -> independent strong reviewer model
```

If the user provides a model-routing policy, add the current model recommendation beneath the capability profile.

---

# 12. Issue Description Contract

Use this structure for executable issues:

```md
## Outcome

One clear result.

## Context

Only the context required to execute this issue.

## Scope

What is included.

## Non-goals

What is intentionally excluded, when useful.

## Acceptance criteria

- [ ] Testable outcome
- [ ] Testable outcome

## Verification

- Command, test, manual flow, screenshot, or observable evidence.

## Suggested agent

- Capability profile: `implementation-general`
- Reasoning: `high`
- Optional current model: `<only when a mapping is configured>`

## Implementation notes

Constraints, references, file paths, API contracts, or migration notes.

---
Bootstrap key: `feature.example`
Bootstrap version: `v5.3.1`
```

Keep issue descriptions self-contained enough to run from mobile, but link to `PRD.md`, `SKILL.md`, repository files, or another issue instead of duplicating long specifications.

---

# 13. Agent Execution Workflow

When an implementation agent is asked to work on the project:

1. Read `AGENTS.md`.
2. Resolve the Linear Project from the URL/name in `AGENTS.md` or repository context.
3. Fetch the issue, current status, team workflow statuses, and blocker relations.
4. Confirm all blocking issues are Done or otherwise resolved.
5. Read only the relevant sections of `PRD.md`, `README.md`, and `SKILL.md`.
6. Move the issue to the team's Started status and verify the mutation succeeded.
7. If the mutation fails, stop before editing code.
8. Use the issue identifier in the branch and PR where supported.
9. Implement only the issue scope.
10. Run the narrowest relevant verification first, then broader checks.
11. Create or update the GitHub PR and capture its full URL.
12. Fetch the next ready unblocked Linear issue and its full URL.
13. Read the next issue's Suggested AI fields.
14. Add a completion comment containing what changed, verification, risks, the GitHub PR URL, the completed issue URL, the next issue URL, and the next issue's Codex/OpenAI and Claude/Anthropic model recommendations with reasoning.
15. Read `completion_mode` from `AGENTS.md`.
16. For `pr-created`, move the issue to Done after verification and PR creation, then verify the mutation.
17. For `merge-gated`, move the issue to In Review and let configured Git automation move it to Done after manual merge.
18. If verification fails, leave it In Progress and comment with the failed checks.
19. Recommend the next unblocked issue instead of inventing new work silently.

Do not change unrelated issue states. Do not claim completion unless the Linear mutation succeeds.

---

# 14. Completion Comment

After implementation, comment on the Linear issue:

```md
## Completed

### What changed
- ...

### Verification
- `command` — result
- Manual flow — result

### Notes / risks
- None, or describe remaining risk.

### Follow-up
- Recommended next issue: `<identifier/title>`

### Suggested commit
`type(scope): summary`
```

Use a separate blocker comment when work cannot continue.

---

# 15. Project Status Updates

For projects lasting more than a short implementation session, create concise Linear Project status updates at meaningful checkpoints.

Include:

- health: on track, at risk, or off track
- completed outcomes
- current focus
- blockers/risks
- next milestone

Do not publish noisy updates after every issue.

---

# 16. Tooling Defaults

Apply these only when the idea or existing repository does not specify alternatives:

- Use the existing package manager; otherwise prefer `pnpm` for JavaScript/TypeScript.
- Prefer latest stable dependencies where practical.
- Use TypeScript when the selected stack supports it.
- Use Vitest for JavaScript/TypeScript unit, package, service, and API tests where practical.
- Use Prettier for formatting where appropriate.
- Use lint-staged for lightweight pre-commit checks when Git hooks are appropriate.
- Keep configuration minimal and maintainable.
- Verify a dependency is installed before importing it, or include installation in the issue.
- Never expose secrets in frontend or mobile clients.
- Respect the existing repository architecture before introducing new frameworks.

These are defaults, not mandatory technology choices for non-JavaScript projects.

---

# 17. Design-System Policy

For projects with meaningful UI, select the component/styling strategy in this order:

1. User-specified system.
2. Existing repository system.
3. Official domain/platform system.
4. A system justified by the design read and project needs.
5. Tailwind or native styling plus semantic tokens when no full system is appropriate.

Do not default to HeroUI, shadcn/ui, Material, Radix, or another component library automatically.

Use one coherent system per UI tree. A multi-app project may intentionally use different systems when app boundaries and ownership are explicit.

Keep global styles simple:

- framework imports
- selected library imports
- semantic variables/tokens
- minimal base styles

Do not use global CSS as a dumping ground for component overrides.

---

# 18. TasteSkill UI/UX Workflow

For UI-bearing projects, perform a contextual design read before creating UI issues.

## Design read

Record one line in `PRD.md` and `SKILL.md`:

```text
Reading this as: <product/page kind> for <audience>, with a <vibe> language, leaning toward <system, component strategy, or aesthetic family>.
```

Ask one clarifying question only when credible design directions materially diverge.

## Design dials

Set and use:

```text
DESIGN_VARIANCE: 1-10
MOTION_INTENSITY: 1-10
VISUAL_DENSITY: 1-10
```

## UI issue requirements

Relevant UI issues should cover:

- loading, empty, error, success, and disabled states
- responsive/adaptive behavior
- keyboard and screen-reader operation
- focus behavior
- real copy and content strategy
- design-system boundaries
- typography, color, shape, and theme consistency
- meaningful motion with reduced-motion fallback
- visual QA against references or screenshots

## Anti-default discipline

Avoid generic AI styling such as unmotivated purple gradients, repetitive equal cards, excessive glass, placeholder screenshots, repeated page sections, decorative badges without value, and animations without purpose.

Apply the philosophy contextually. Do not force landing-page composition rules onto dashboards, CRUD tools, or dense workflows.

---

# 17. Completion Link Contract

After every executable issue, the agent must return and post to Linear:

- completed Linear issue URL
- GitHub PR URL
- next ready Linear issue URL
- next issue title
- next issue's Codex/OpenAI recommendation and reasoning
- next issue's Claude/Anthropic recommendation and reasoning
- why the next issue is ready and recommended

The agent must fetch the next issue and copy its suggestions. It must not infer a replacement without updating Linear first. When no issue is ready, link the Linear Project and report the blockers.

Use `templates/LINEAR_COMPLETION_COMMENT.template.md`.

# 19. PRD.md

`PRD.md` is the product and technical source of truth.

Recommended sections, adjusted to the project shape:

```text
# <Project Name> PRD

## Product summary
## Problem statement
## Project shapes
## Goals
## Non-goals
## Users and jobs to be done
## Core use cases
## Functional requirements
## UX / interface requirements
## Design read and design direction
## Technical direction
## High-level architecture
## Client architecture
## Service/API architecture
## Data/storage design
## AI/data pipeline design
## External integrations
## Security and privacy
## Reliability and observability
## Error handling and recovery
## Testing strategy
## MVP scope
## Future enhancements
## Assumptions
## Open questions
## Definition of done
```

Do not place task lists, Linear issue identifiers, agent status rules, or setup command catalogs in the PRD.

---

# 20. AGENTS.md

`AGENTS.md` is the short AI entry point.

It must include:

- project snapshot
- authoritative documents
- Linear Project name and URL/slug
- issue selection workflow
- status-transition rules
- project-specific constraints
- verification expectations
- completion-comment format
- what to do when blocked or unsure

Do not duplicate the PRD, issue descriptions, schemas, or README.

---

# 21. README.md

`README.md` is the developer guide.

Include only relevant sections:

```text
Overview
Tech stack
Project structure
Requirements
Environment variables
Local setup
Commands
Frontend/mobile development
Backend/API development
Database/data notes
Testing
Build and deployment
Linear workflow
Notes and limitations
```

The Linear section should link to the project and explain how developers select and complete issues. Do not list every issue.

---

# 22. SKILL.md

Generate only when the project has meaningful UI.

It must be project-specific and concise, containing:

- frontmatter
- design read
- design dials
- system/component strategy
- app-boundary rules
- typography and layout
- color, shape, and theme locks
- responsive/adaptive rules
- motion rules
- state rules
- accessibility
- anti-slop bans
- pre-flight review

Do not paste the entire generic TasteSkill source into each project.

---

# 23. Linear Creation Algorithm

Follow this order:

1. Parse the idea and infer project shapes.
2. Identify material open questions; ask at most one before proceeding.
3. Generate `PRD.md`.
4. Generate `SKILL.md` when UI is meaningful.
5. Generate `README.md` and concise `AGENTS.md`.
6. Resolve the Linear team.
7. Search for and reuse the project, or create it.
8. Fetch team statuses and existing labels.
9. Create only missing labels.
10. Create milestones when useful.
11. Define workstreams and executable issues in a dependency graph.
12. Create or update parent issues.
13. Create or update executable issues in topological batches.
14. Add parent/child and blocking relations.
15. Set priorities and initial statuses.
16. Verify every issue belongs to the correct project and team.
17. Verify there are no duplicate bootstrap keys.
18. Return a summary with links, counts, first issue, assumptions, and open questions.

---

# 24. Linear Unavailable Policy

If the connected agent cannot access Linear:

- state that Linear access is required for v5 task creation
- do not silently create local task files
- ask the user to connect Linear or authorize a documentation-only fallback

A documentation-only fallback may generate `PRD.md`, `AGENTS.md`, `README.md`, and `SKILL.md`, but `AGENTS.md` must mark task planning as pending and must not invent a local task system.

---

# 25. Final Response Requirements

After generating a project with v5, summarize:

- project shapes used
- Linear team and project
- project link
- milestones created
- parent issues created
- executable issues created
- first unblocked issue
- design read and selected UI system, when applicable
- repository files created
- assumptions
- unresolved questions

Do not paste the full issue list unless the user asks.

---

# 26. Quality Checklist

Before finishing, verify:

- Linear is the only task-status source of truth.
- No local task files were generated.
- The correct team and one dedicated project were used.
- Existing projects/issues were reused instead of duplicated.
- Every executable issue belongs to the project.
- Every issue has one clear outcome and testable acceptance criteria.
- Real dependencies use Linear relations.
- Priorities are differentiated.
- Initial statuses reflect blockers.
- Capability profiles are provider-neutral.
- `AGENTS.md` points agents to Linear.
- `PRD.md`, `README.md`, and `SKILL.md` do not duplicate issue state.
- UI work follows the project-specific design read and system boundary.
- Security, accessibility, testing, and release work are included when relevant.
- The first unblocked issue is obvious and ready to start.
