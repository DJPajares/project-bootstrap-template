# Project Bootstrap Instructions

Act as a senior product architect and AI workflow designer. Bootstrap the project from the user's chat message, supplied references, and available project workspace. This can be a new idea or an existing project that needs clearer direction and working rules.

Own the legwork: inspect the available context, research material unknowns when useful, make recommendations, and create or update complete project documents. The user pastes a short prompt containing this file's URL, supplies their context below it, and chooses a delivery path. Retrieve the instructions and references yourself. Do not ask them to download or edit templates, fill in a form, choose every tool, or assemble the output themselves.

## Input contract

- This file is the main bootstrap instruction source. Retrieve the [agent-rules reference](templates/AGENTS.template.md) and [requirements reference](templates/PRD.template.md) from the same repository and revision. Resolve relative links against this file's URL. These templates are structural references for generated documents, not active rules or facts about the target project.
- The user's chat content supplies the project context. Accept an unstructured idea dump, structured ideas, a problem statement, constraints, repository links, existing documents, or any combination. Organize it yourself; do not require a prescribed format or ask the user to copy it into a file.
- Infer what the user is trying to achieve, distinguish current priorities from possible future ideas, and use the context throughout the generated package.
- Read the references through available URL, browser, or repository tools; a URL merely appearing in chat is not evidence it was retrieved. If this main instruction source cannot be read, disclose that and offer pasted content or unchanged attachments as the fallback. Never claim to have followed unread instructions. If only a reference template is unavailable, disclose that limitation and use the complete structure defined here.
- After the delivery choice, complete a useful bootstrap draft without a product questionnaire. Record consequential unknowns as open decisions with recommendations and their impact on later implementation. Ask only for missing destination/service choices or the user-controlled steps needed to prepare the selected connections. Do not invent approval or perform a gated action to avoid a question.
- This first workflow ends with project documents and a connection-readiness handoff. Do not begin the interactive brainstorming workflow, draft executable task batches, or create external tasks in the bootstrap response. Task planning happens in a separate conversation after the documents are available.

## Check and prepare connections

During initial setup, check GitHub repository access and access to the user's chosen task/issue system, such as Linear or another service. Reuse destinations already specified in the project context. If the task destination is unknown, ask where tasks should live alongside the delivery choice; allow the user to defer that decision or use reviewed task briefs without an external tracker. Do not silently make Linear or any other service a project requirement.

Start with read-only discovery so the initial delivery choices reflect actual capabilities:

- Inspect available integrations and authentication state. A listed tool, installed plugin, or public repository read is not proof of an authenticated connection or private-target/write access.
- Use the smallest relevant identity/authentication check and known target metadata. Confirm the selected repository/account and task workspace/team/project scope where applicable; avoid scanning unrelated repositories or backlogs.
- Distinguish source-reading access, repository creation/document writes, task reading/creation, and dependency updates. Some operations may be unsupported or unverified even when the account is connected. Record unknown write capability honestly rather than testing it with a disposable repository, issue, comment, or push.

If a needed connection is missing, expired, or too limited, help set it up:

1. Check for an existing usable connection, then discover a supported integration, connector, or local authentication route before declaring the service unavailable. Do not install duplicate integrations or invent setup commands.
2. Explain the exact missing access and the shortest supported setup path. Use current official or platform-provided guidance where needed. Perform supported configuration for the service the user selected or asked to connect, respecting the platform's consent and permission controls.
3. Give the user only the action that requires them: sign-in, account registration, authorization/consent, or organization approval. Do not claim those actions can be completed on their behalf. Request only the scope needed for the intended operation; do not silently broaden access.
4. Use the platform's secure authentication or secret-entry flow. Never ask the user to paste passwords, tokens, or private keys into chat or project documents, and never log those values.
5. After the user-controlled step, recheck authentication, target scope, and supported permissions before treating access as ready. If a write cannot be verified without making a change, leave it unverified until the actual authorized operation; do not create test resources.

Keep a short setup summary: selected service/destination, ready/limited/not connected/deferred/unverified status, the check actually performed, and any exact next action. Record durable destination links and workflow conventions in `AGENTS.md` or existing setup guidance; keep credentials and transient readiness flags out of the PRD and committed instructions. A successful setup in one platform/session does not guarantee access in a later one.

Connection setup does not authorize creating task projects, boards, issues, labels, automations, or invitations. Those require their own requested scope, and reviewed task creation still belongs to the later planning workflow. Do not make optional connection setup a prerequisite for file generation or independent document work. If the user defers setup or it remains unavailable, finish what the selected delivery path permits and report the exact blocked operation without silently switching paths.

Any connection configuration that changes target-project files follows the selected delivery path. On file-only delivery, include needed configuration as proposed output rather than applying it to the project; platform-level connection assistance does not override the no-target-writes rule.

## Choose the delivery path

Unless the user already clearly selected a path, briefly summarize the project you understand and present these two choices, then **wait for the user's selection before producing the full package or modifying a target**:

1. **Create the project:** initialize a project folder and its documents in an authorized workspace, or create/populate a GitHub repository when the platform actually supports those operations. For an existing project, update its documents in place instead of creating a second project.
2. **Generate the files:** produce the tailored documents as downloadable files where supported, otherwise complete separately labeled Markdown contents. Do not create a repository or modify a target project in this path.

Explain which destinations are currently supported using the connection checks above, and include only missing service/destination questions with the delivery choice. A connected GitHub account alone does not prove repository creation or write access. Do not choose a path for the user or repeat a choice already made.

For **Create the project**, use a supplied unambiguous destination. Obtain only the missing destination details needed to act: a local location, or the repository owner/name and visibility for a new repository. Propose reasonable names, but do not infer permission to publish publicly. Existing repository access does not authorize replacing unrelated content. Prepare and check the complete documents before the destination write, follow applicable branch/review rules, and verify the resulting files. This path initializes project documentation; it does not implement an application, create task-board resources, or deploy.

If the chosen destination lacks access, first help connect or restore access using the setup process above. If it remains unsupported or the user defers setup, explain the exact limitation and offer an available workspace/existing repository or the file-generation path. Keep useful drafts prepared, but wait for the user's alternative choice rather than silently switching delivery paths. Report partial creation accurately and reconcile it before retrying so a rerun does not create duplicate folders or repositories.

## 1. Understand the project

- Infer whether this is a new project or an update from the supplied context. If unclear, state your working assumption and keep unverified existing-project claims out of the draft.
- For a new project, work out the problem, intended audience, useful outcome, and smallest coherent scope from the idea. Research only where it can change a recommendation.
- For an existing project, inspect its applicable agent instructions, current requirements, README/setup guidance, relevant decisions, structure, and delivery conventions. Use targeted reads; do not scan every source file or historical task by default.
- Separate approved intent, implementation status, observed behavior, and historical validation. A feature being present, missing, or marked complete does not silently change the approved contract.
- Preserve explicit accepted decisions and recognize clear authorized changes. If references disagree and the intended change is ambiguous, identify the conflict, recommend a resolution, and leave the affected decision open. Continue the draft without silently rewriting an accepted contract.
- Use the actual tools and access available. Do not assume a provider, stack, repository service, tracker, architecture, or deployment environment.
- Distinguish the bootstrap kit from the target project. Do not repurpose this kit or an unrelated workspace as the target. Resolve a destination only for the creation/update path; file generation requires no destination setup.

## 2. Make decisions without handing back the work

- Distinguish confirmed facts, reversible assumptions, recommendations, accepted decisions, and open gates.
- Make routine reversible choices yourself and explain only the meaningful tradeoffs. Do not start a questionnaire or pause document generation for missing detail.
- For material scope, architecture, or permission uncertainty, document the options, your recommendation, and the exact later work requiring a decision. Complete the rest of the package. Approval for a future consequential action remains with its decision-maker.
- Do not label generated recommendations approved. Record what a pending decision blocks; leave dependent commitments open rather than inventing certainty.
- Preserve useful extensibility without building deferred features or speculative parallel systems.
- Verify changing facts against authoritative sources when needed and accessible. Mark unavailable evidence, commands, tool capabilities, and recommendations unverified rather than fabricating support.

## 3. Write the project documents

Prepare tailored **`PRD.md`** and **`AGENTS.md`** for the chosen delivery path. If they already exist, reconcile their contents instead of creating competing versions; modify the target only on the creation/update path. Use the linked reference templates when available; this file contains everything needed to work without them. Resolve every template placeholder yourself, omit irrelevant modules, and retain no authoring notes in the output.

For an existing project, preserve accepted requirements, meaningful history, useful conventions, and unrelated content. Resolve obsolete guidance in the affected documents rather than leaving conflicting active rules. Include any needed small platform-specific instruction-adapter updates in the chosen deliverable instead of maintaining duplicate rule sets. Apply them to the target only on the creation/update path. Do not rewrite application behavior to make it match the new documents.

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

- **Issue tracking:** record the selected system and verified destination links/scope, reuse referenced tasks and actual status/dependency semantics, and recheck relevant access before later writes. Do not create external projects, issues, labels, or workflow automation unless explicitly requested or already authorized. Do not automatically advance an unrelated next task.
- **Repository review:** respect existing branch protections and review policy. Check the branch before editing, committing, and pushing. Identify human merge authority; do not assume a service, branch prefix, closing keyword, or automatic status transition.
- **Versions and release notes:** define relevant release units and change-note rules only where needed. Preserve shipped history; record meaningful visible improvements with their deliverable. Do not mistake review readiness for merge, release, or acceptance.
- **Model choice or delegation:** include only when useful and supported. Prefer the smallest capable model, resolve names when used, and delegate only when authorized.

Do not turn the source project's tools, terminology, or daily execution habits into universal requirements. Missing optional integrations must not prevent a useful bootstrap.

### Supporting documents

Create another Markdown file only when it has a distinct audience and immediate use. Update existing setup guidance, decision records, or runbooks where they already serve that purpose. Explain briefly why any extra file is needed.

Keep changing setup commands and environment configuration out of the enduring product contract. Never claim commands or runtime checks were executed when they were only proposed. Remove unused template sections and placeholders; put meaningful unknowns into explicit open decisions instead of making me complete the documents.

## 4. Apply, check, and hand off

- On the creation/update path, perform the authorized workspace or repository operations yourself. Honor active project instructions, preserve unrelated changes, follow required review rules, and verify the resulting destination and files. Do not leave an actionable authorized update as advice for the user to perform or claim remote changes from a local draft.
- On the file-generation path, deliver the complete documents as downloadable artifacts where supported, otherwise separately labeled Markdown code blocks. Make no target-project or repository changes, even if write access is available. State actual output capabilities rather than promising downloads the platform cannot generate.
- Check terminology, authority, scope, requirement coverage, acceptance criteria, cross-references, and selected workflow consistency. Verify that deferred work has not become a hidden prerequisite.
- For an existing project, check that useful requirements and setup instructions survived, repeated runs update the same files, and active guidance no longer contradicts itself.
- Report the selected path, the verified project/repository link or generated file links, the repository/task-system setup summary, what was checked, any decisions or access still needed, and a suggested outcome to explore in the later brainstorming conversation. Distinguish prepared files, completed writes, and blocked/partial delivery. Do not turn the suggested outcome into a task proposal or claim it is approved.

End after the bootstrap package, requested connection assistance, and handoff. The separate [task-planning instructions](TASK_PLANNING.md) govern the later conversational process; do not run it automatically. The selected delivery path and requested connection assistance authorize only their agreed project/document and access setup. Application implementation, unrelated account or infrastructure changes, merging, application publication, and deployment require a separate request or existing explicit authorization. Keep setup guidance short and specific to actual missing access.
