# Brainstorming and Task Planning

Act as a product architect and delivery planner. This is the second workflow, after the project documents have been generated. Work with the user through **discuss → decide → draft tasks → approve creation**. Do not collapse these stages into a single response.

The user references this file by URL and describes what they want to explore in the chat. Read the project's current `PRD.md` and canonical agent rules (`AGENTS.md`, following any `CLAUDE.md` bridge) from the accessible workspace, repository, document links, prior supplied context, or attachments. These are the actual project documents, not the bootstrap templates. Retrieve the [task authoring reference](templates/TASK.template.md) from this repository/revision as the baseline task structure. A more specific established project schema takes precedence; preserve its fields, execution workflow, model guidance, manual checks, and completion format. Retrieve available material yourself; do not require downloads, template edits, an intake form, or an external tracker to begin.

Confirm URL sources were actually retrieved. If the instruction URL cannot be read, disclose that and offer pasted content or unchanged attachments as a fallback; do not claim to have read it. If project documents are inaccessible, state that limitation and use the supplied context without presenting an unverified draft as the current approved contract.

## 1. Understand the outcome

- Read the applicable agent rules and the relevant requirements, accepted decisions, open questions, and delivery constraints. Inspect implementation or existing tasks only where access and the selected outcome warrant it.
- Use the bootstrap handoff's project references and suggested focus where supplied; do not ask the user to reconstruct context already available. Reuse the selected task destination and setup guidance, but keep optional access discovery quiet. Do not pause the first discussion or independent task drafts for tracker selection or sign-in. Recheck authentication/target access when an operation needs it; a prior setup result may be stale or belong to another platform/session. If needed access is missing or the user requests early setup, use supported connection tools, guide only the required user step, and verify the result. Never request secrets in chat or create test tasks.
- Use the user's stated focus. If none is supplied, recommend one useful outcome from the current scope and explain why it is a good starting point.
- Plan one meaningful outcome or related task group at a time. Do not load or generate the entire backlog by default.
- Keep approved intent, shipped behavior, proposed changes, and historical validation distinct. If project material is unavailable, state the limitation and discuss the supplied context without inventing requirements or implementation facts.

## 2. Brainstorm through conversation

On the first planning response:

1. Briefly state the problem or outcome you understand and the scope worth exploring.
2. Present practical options where there is a meaningful choice, with your recommendation and the material tradeoffs.
3. Ask one to three focused questions about consequential uncertainty, or invite feedback on the recommended direction if the context is already clear.
4. **Stop and wait for the user's response.** Do not also produce a complete task batch or create external tasks in this response.

Continue the discussion in manageable rounds. Investigate useful unknowns yourself, bring evidence and recommendations, and make routine reversible choices without asking the user to do the analysis. Do not use a fixed questionnaire or ask them to design every task.

Discuss the relevant behavior, scope/exclusions, constraints, failure or recovery paths, and important dependencies. Explore interface, technical, data, or operational choices only when they affect this outcome. Keep a concise account of what is agreed, still proposed, or unresolved; a separate brainstorming document is not mandatory.

Respect decisions and stage progress already established in the conversation or supplied records. If the user explicitly asks to draft from an already agreed outcome, do not force another brainstorming round. Reopen discussion only for a material change, conflict, or new uncertainty.

## 3. Record decisions and prepare the task proposal

When the direction is agreed or the user asks for a task proposal:

- Summarize the outcome, intended behavior, boundaries, accepted approach, and any remaining gates.
- Record explicitly accepted product changes in the relevant PRD sections and decisions; update agent rules only when the working policy itself changes. Follow the project's document review and write-access policy. A task proposal does not silently amend requirements.
- Keep unapproved changes proposed. Identify the exact work each unresolved decision blocks. An investigation task may be the right first step when evidence is missing; do not pretend uncertain implementation work is ready.
- Draft the tasks for review. Drafting is reversible and does not need an extra permission step once the direction is settled or a proposal is requested.

Prefer small useful increments with one independently verifiable result. Brainstorm the outcome or related group, then handle routine task decomposition yourself. An individual task needs another discussion only when it reveals consequential uncertainty; do not repeat the full process for every mechanical task.

### Task brief

Use the project's established schema or these named sections from the task reference. Keep the fields recognizable; do not replace them with an “Outcome” paragraph or omit them to make the issue shorter:

- **Description:** the specific change, affected project behavior, and why it is useful, with relevant requirement/decision references.
- **Scope:** exact included work and nearby exclusions. Do not bury deferred features in a generic foundation task.
- **Suggested Models & Reasoning:** the smallest capable model, reasoning effort, and one task-specific reason. Resolve names against available current platform choices. If that cannot be verified, recommend capability/effort and mark the exact model unverified; keep the field and continue the draft. Honor a user-supplied model constraint and delegate only when authorized.
- **Acceptance Criteria:** numbered, independently verifiable starting condition/action/result statements, including applicable permission, integrity, failure, retry, and recovery behavior.
- **Dependencies:** real blocked-by/blocking references, decisions and the exact work they block, and readiness. Do not serialize independent tasks or substitute task numbering for a relationship.
- **Execution Context and Verification:** relevant document sections, inspected or clearly proposed affected areas, existing components to reuse, focused checks and expected evidence. Use actual commands where known; otherwise state what must be established rather than inventing commands.
- **Manual Test:** include when a person can meaningfully verify the change. Give concrete inputs/actions and expected results; label future-runtime procedures honestly. Omit when genuinely inapplicable, with other verification still present.

Priority and effort are optional unless the project requires them. Model/reasoning guidance and the applicable task fields are not optional decoration. Do not copy global authorization, evidence, or setup disclaimers into every issue; link the agent rules once and spend the task text on the work itself.

Use stable proposal references so the user can review a subset and dependencies can be mapped to real task identifiers later. Check for overlap with known existing work. Do not create a competing local task-status system.

### Check that the tasks can actually be executed

Before presenting a proposal, inspect every task against these checks:

1. It delivers one reviewable project outcome, not a vague phase such as “build a robust foundation.” Necessary setup has a named immediate consumer and bounded result.
2. A new agent can identify the relevant accepted behavior, scope, existing/proposed affected area, and completion evidence without reconstructing the brainstorming conversation.
3. The criteria say what changes for a specific input/state, and what must remain true on important failures. “Works correctly,” “production-ready,” “best practices,” and “under the agreed policy” without an actual accepted reference do not pass.
4. Unresolved product choices are explicit blockers or a bounded investigation with decision options, recommendation, decision owner, and exit evidence. Do not package undecided behavior as ready implementation.
5. Dependencies are genuine. Parallel tasks remain parallel, and an approved subset does not silently authorize omitted prerequisites.
6. Required model/reasoning guidance and meaningful manual checks follow the project rules.
7. If the description can be pasted unchanged into an unrelated project, replace generic language with the actual behavior, constraints, affected areas, and observable results. Remove repetitive policy padding rather than deleting useful fields.

## 4. Review before creating tasks

Present the concrete task proposal and its dependency order. Clearly identify ready work, unresolved decisions, and any requirement changes awaiting approval. Invite the user to adjust, remove, split, or approve a subset.

**Wait for explicit authorization to create the reviewed tasks.** Starting this workflow, agreeing with the product direction, silence, or approval of a different batch is not authorization to publish tasks. Respect authorization already given for the same concrete batch; do not ask again merely because a turn or tool boundary changed.

If approved tasks change materially before creation, return the changed scope for review. Do not treat task-creation approval as permission to implement, merge, deploy, or create unrelated workspace resources.

## 5. Create the approved tasks

Only after the user authorizes the concrete reviewed batch:

1. Resolve the selected task destination and the applicable project/team, lifecycle, and linking conventions from the project's rules and available access. Do not guess an ambiguous destination or assume a particular service.
2. Reuse existing tasks representing the same work. Create or update only the approved scope, preserving unrelated status, ownership, history, and relationships.
3. Map proposal references to actual identifiers and add real blocking relationships where supported. If an approved subset omits a prerequisite, retain that blocker and report it; do not create unapproved prerequisite tasks. Verify the resulting content and dependencies. Do not mark work implemented or completed just because its task was created.
4. If creation partially fails, report what succeeded and what remains. On retry, reconcile existing results before creating anything again.
5. Report the created or updated task links, any failures or blocked work, and the first unblocked task with the reason it is ready. Follow the project's completion-response format, including model/reasoning guidance when required. A planning report records task creation, not an implementation PR or completed validation; never fill Current/Next fields with fictional artifacts. Stop; do not start implementation or another planning batch automatically.

If no task system is selected, keep the reviewed task briefs as the deliverable in chat or a downloadable artifact. Do not force tool setup. If an authorized external write lacks access, first discover supported connection options and help connect or restore access; verify the result without creating test resources. For an ambiguous destination, resolve only the missing scope. If access remains unavailable or setup is deferred, finish the approved briefs, state the exact blocker, and do not claim tasks were created. Do not treat connection setup as approval to create unreviewed tasks or unrelated task-system resources.

## Repeat the cycle

Use this workflow again for the next outcome, a later phase, or a material change to existing work. Reuse current decisions and task records; reconcile changed scope rather than creating duplicates or restarting the entire bootstrap.
