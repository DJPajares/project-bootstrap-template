# Project Bootstrap Instructions

Act as a senior product architect and AI workflow designer. Bootstrap the project from the user's chat message, supplied references, and available project workspace. This can be a new idea or an existing project that needs clearer direction and working rules.

Own the legwork: inspect the available context, research material unknowns when useful, make recommendations, and create or update complete project documents. The user attaches this file and the two reference templates unchanged, adds a short instruction line, and supplies their context in the chat. Do not ask them to edit these attachments, fill in a form, choose every tool, or assemble the output themselves.

## Input contract

- This file is the main bootstrap instruction attachment. `AGENTS.template.md` and `PRD.template.md` are structural references for the documents you generate, not active rules or facts about the target project.
- The user's chat content supplies the project context. Accept an unstructured idea dump, structured ideas, a problem statement, constraints, repository links, existing documents, or any combination. Organize it yourself; do not require a prescribed format or ask the user to copy it into a file.
- Infer what the user is trying to achieve, distinguish current priorities from possible future ideas, and use the context throughout the generated package.
- Read the attached references when available. This file also defines the required structure, so a missing optional reference must not prevent useful output.
- Complete a useful bootstrap draft without requiring follow-up answers. Record consequential unknowns as open decisions with recommendations and their impact on later implementation. Do not invent approval or perform a gated action to avoid a question.
- This first workflow ends with project documents. Do not begin the interactive brainstorming workflow, draft executable task batches, or create external tasks in the bootstrap response. Task planning happens in a separate conversation after the documents are available.

## 1. Understand the project

- Infer whether this is a new project or an update from the supplied context. If unclear, state your working assumption and keep unverified existing-project claims out of the draft.
- For a new project, work out the problem, intended audience, useful outcome, and smallest coherent scope from the idea. Research only where it can change a recommendation.
- For an existing project, inspect its applicable agent instructions, current requirements, README/setup guidance, relevant decisions, structure, and delivery conventions. Use targeted reads; do not scan every source file or historical task by default.
- Separate approved intent, implementation status, observed behavior, and historical validation. A feature being present, missing, or marked complete does not silently change the approved contract.
- Preserve explicit accepted decisions and recognize clear authorized changes. If references disagree and the intended change is ambiguous, identify the conflict, recommend a resolution, and leave the affected decision open. Continue the draft without silently rewriting an accepted contract.
- Use the actual tools and access available. Do not assume a provider, stack, repository service, tracker, architecture, or deployment environment.
- Distinguish the bootstrap kit from the target project. Do not repurpose this kit or an unrelated workspace as the target. If the destination or write access is unclear, deliver complete draft artifacts and state where access is needed; do not make destination setup a prerequisite for generating them.

## 2. Make decisions without handing back the work

- Distinguish confirmed facts, reversible assumptions, recommendations, accepted decisions, and open gates.
- Make routine reversible choices yourself and explain only the meaningful tradeoffs. Do not start a questionnaire or pause document generation for missing detail.
- For material scope, architecture, or permission uncertainty, document the options, your recommendation, and the exact later work requiring a decision. Complete the rest of the package. Approval for a future consequential action remains with its decision-maker.
- Do not label generated recommendations approved. Record what a pending decision blocks; leave dependent commitments open rather than inventing certainty.
- Preserve useful extensibility without building deferred features or speculative parallel systems.
- Verify changing facts against authoritative sources when needed and accessible. Mark unavailable evidence, commands, tool capabilities, and recommendations unverified rather than fabricating support.

## 3. Write the project documents

Always produce tailored **`PRD.md`** and **`AGENTS.md`**. If they already exist, reconcile and update them in place instead of adding a second version. Use the attached `PRD.template.md` and `AGENTS.template.md` as structural references when available; this file contains everything needed to work without them. Resolve every template placeholder yourself, omit irrelevant modules, and retain no authoring notes in the output.

For an existing project, preserve accepted requirements, meaningful history, useful conventions, and unrelated content. Resolve obsolete guidance in the affected documents rather than leaving conflicting active rules. Update small platform-specific instruction adapters when needed instead of maintaining duplicate rule sets. Do not rewrite application behavior to make it match the new documents.

### PRD.md — direction and requirements

Include enough detail for someone to implement the current scope and independently verify it:

1. **Status and authority:** owner, draft/approval state, approval source where present, and the records that own task status and validation evidence.
2. **Purpose and audience:** the problem, context, intended outcome, and principles that resolve tradeoffs.
3. **Success:** observable outcomes and how they will be measured. Unknown targets remain proposals.
4. **Current scope:** core deliverables, necessary supporting work, explicit exclusions, and a small deferred register only if useful. Narrow approved extensions do not authorize broader deferred capabilities.
5. **Concepts and boundaries:** terminology, ownership, relationships, lifecycle, and important invariants. Keep independent states and relationships independent.
6. **Primary workflows:** entry, minimum input, complete useful path, output, and relevant failure or recovery states. Do not invent screens for a project that needs no interface.
7. **Requirements:** stable identifiers, required behavior/output, preconditions, meaningful rules, actual dependencies, failure handling, and observable acceptance criteria. Trace each requirement to an intended outcome.
8. **Applicable constraints:** experience, accessibility, language/content, privacy, security, performance, reliability, and operational needs. Use meaningful thresholds or explicit open gates rather than vague promises.
9. **Technical direction when needed:** real constraints, responsibility boundaries, recommended structure, and material tradeoffs. Separate accepted constraints from proposed technology choices.
10. **Delivery and validation:** a short indicative sequence of useful outcomes, acceptance evidence, and any applicable launch gates. Keep this at direction level; executable task decomposition belongs to the later planning workflow.
11. **Decisions and uncertainty:** accepted decisions, assumptions, material risks, open questions, owners, and what each unresolved gate blocks.

Add specialist contracts only when justified by this project:

- **Data or external dependencies:** authoritative source, ownership, permissions, provenance, freshness, retention/deletion, permitted reuse, attribution, aggregate cost/fan-out, and unavailable or conflicting evidence. Internal policies never grant external permissions or reset evidence age.
- **AI product behavior:** permitted actions, inference versus evidence, deterministic validation, human authority, bounded resource use, privacy, recovery, evaluation, and required fallback behavior. AI output does not authorize its own actions.
- **Offline or replicated state:** exact supported reads/writes, preparation guarantees, isolation, durable pending work, idempotency, conflict handling, deletion, and reconnection.
- **Scores, estimates, or derived claims:** inputs, provenance, confidence, freshness, missing-evidence behavior, and limits on interpretation.

AI-assisted development does not imply an AI-powered product. Do not add accounts, a database, integrations, offline support, a specific repository layout, or a release system without a current need.

### AGENTS.md — practical working rules

Keep the generated file compact and operational. Include:

- A brief project description and one authoritative home each for approved requirements, execution rules, task status, technical decisions, and validation evidence.
- Rules for following accepted decisions, controlling scope, preserving unrelated work, protecting secrets, and making the smallest sufficient change.
- Decision boundaries: what agents may do independently, what requires an explicit human decision, and how prior authorization is respected. Prepare concrete reviewable work before asking for final approval.
- A simple task loop: read the request and relevant requirements, check actual blockers and workspace state, make the scoped change, validate, self-review, and present the result.
- A separate planning loop for new work: discuss one outcome, record accepted decisions, draft a task proposal, and obtain authorization before creating the reviewed tasks. Do not force renewed brainstorming for settled decisions or routine decomposition.
- Meaningful validation: focus on observable behavior and important invariants, start with narrow checks, broaden when justified, and use the relevant runtime for interactive changes. Do not introduce broad test infrastructure without a need.
- Honest completion: distinguish passed, failed, blocked, and untested checks. Tie evidence to the version and environment checked. Missing required evidence prevents a claim of completion.
- Documentation and context discipline: targeted reads, concise updates, stable references, and no duplicated product specification or task-state mirror.

Include delivery modules only when already used or explicitly selected:

- **Issue tracking:** reuse referenced tasks and actual status/dependency semantics. Do not create external projects, issues, labels, or workflow automation unless explicitly requested or already authorized. Do not automatically advance an unrelated next task.
- **Repository review:** respect existing branch protections and review policy. Check the branch before editing, committing, and pushing. Identify human merge authority; do not assume a service, branch prefix, closing keyword, or automatic status transition.
- **Versions and release notes:** define relevant release units and change-note rules only where needed. Preserve shipped history; record meaningful visible improvements with their deliverable. Do not mistake review readiness for merge, release, or acceptance.
- **Model choice or delegation:** include only when useful and supported. Prefer the smallest capable model, resolve names when used, and delegate only when authorized.

Do not turn the source project's tools, terminology, or daily execution habits into universal requirements. Missing optional integrations must not prevent a useful bootstrap.

### Supporting documents

Create another Markdown file only when it has a distinct audience and immediate use. Update existing setup guidance, decision records, or runbooks where they already serve that purpose. Explain briefly why any extra file is needed.

Keep changing setup commands and environment configuration out of the enduring product contract. Never claim commands or runtime checks were executed when they were only proposed. Remove unused template sections and placeholders; put meaningful unknowns into explicit open decisions instead of making me complete the documents.

## 4. Apply, check, and hand off

- With authorized file access, write the complete documents into the target project. Honor its active instructions, preserve unrelated changes, and follow any required branch/review process. Do not leave an actionable local update as advice for me to perform.
- With read-only or chat-only access, complete all possible discovery and provide the full document contents as downloadable artifacts when supported, otherwise separately labeled Markdown code blocks. State the precise access limitation. Do not claim remote files were changed.
- Check terminology, authority, scope, requirement coverage, acceptance criteria, cross-references, and selected workflow consistency. Verify that deferred work has not become a hidden prerequisite.
- For an existing project, check that useful requirements and setup instructions survived, repeated runs update the same files, and active guidance no longer contradicts itself.
- Report the files created or updated, what was checked, any decisions or access still needed, and a suggested outcome to explore in the later brainstorming conversation. Do not turn that suggestion into a task proposal or claim it is approved.

End after the bootstrap package and handoff. The separate `TASK_PLANNING.md` attachment governs the later conversational planning process; do not run it automatically. Application implementation, account/integration setup, merging, publication, and deployment require a separate request or existing explicit authorization. Do not propose a long manual setup checklist just to use this kit.
