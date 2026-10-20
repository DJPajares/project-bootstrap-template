# Project Bootstrap Template

Paste a short prompt with a URL, add your project context, and choose how the agent should deliver the result: create the project in a workspace/repository, or generate the files for you. In a separate conversation, brainstorm outcomes and turn agreed decisions into reviewed tasks.

**No template downloads or edits are needed when the AI platform can read URLs.** The same flow works for new and existing projects. A GitHub connection is optional and usable only for operations its tools and permissions actually support.

## 1. Generate the project documents

1. Copy this prompt into your AI platform:

   ```text
   Read and follow [PROJECT_BOOTSTRAP.md](https://raw.githubusercontent.com/DJPajares/project-bootstrap-template/main/PROJECT_BOOTSTRAP.md) using my project context below. If you cannot retrieve that file, say so.
   ```

2. Add your idea dump, structured ideas, problem statement, or existing project context below it and send.
3. Choose the delivery path the agent presents:
   - **Create the project:** initialize a project folder or create/populate a GitHub repository when supported. For an existing project, update its documents in place.
   - **Generate the files:** receive downloadable documents where supported, otherwise complete Markdown contents. No target-project or repository changes are made.

A paragraph is enough to start. The agent reads the URL and retrieves the reference templates itself. It checks repository and task-system access, then asks for your delivery choice and only missing service/destination details. A connected account alone does not guarantee the required operations or target permissions.

## Initial access setup

The agent checks GitHub and your chosen task/issue destination, such as Linear or another service. It reuses known choices and existing connections. If you have not chosen a task system, it asks where tasks should live; you can decide later or keep task briefs without an external tracker.

When access is missing, the agent looks for a supported connection method, handles the configuration it can, and guides you through only the necessary sign-in, consent, or organization-approval step. It then verifies the connection and target scope. It never asks you to paste credentials into chat or creates test issues/repositories to prove access.

You receive a short readiness summary with any exact next action. Setup does not create task projects, issues, or automations, and does not authorize later task creation. Missing or deferred connections do not block file generation. File-only delivery still leaves target-project files untouched, including connection configuration.

No product questionnaire or template editing is required. The agent organizes your context, handles routine gaps, and records consequential unknowns with recommendations. Creating the project initializes its documents; it does not build an application. This workflow stops after the documents and handoff, without drafting or creating implementation tasks.

If the platform cannot read the URL, use pasted instructions or attach [PROJECT_BOOTSTRAP.md](PROJECT_BOOTSTRAP.md) and its [agent-rules](templates/AGENTS.template.md) and [requirements](templates/PRD.template.md) references unchanged. The agent must disclose unread sources instead of claiming it followed them.

## What the agent produces

- **`PRD.md`** — the project's purpose, audience, current scope, requirements, constraints, and decisions.
- **`AGENTS.md`** — practical rules for agents working on that project, including validation and human decision boundaries.
- **Supporting guidance when needed** — such as setup instructions, a technical decision record, or an operational runbook. Existing documents are updated instead of duplicated.
- **A short handoff** — what changed, what was checked, repository/task-system readiness, any exact setup step or decision still needed, and a suggested outcome to discuss next.

On the creation/update path, the agent writes and verifies the documents in the agreed destination. On the file-generation path, it returns the files without modifying a target project. Draft decisions stay visibly distinct from approved ones.

## 2. Brainstorm and plan the tasks

Start a separate conversation when you are ready to plan work:

1. Copy this prompt into the chat:

   ```text
   Read and follow [TASK_PLANNING.md](https://raw.githubusercontent.com/DJPajares/project-bootstrap-template/main/TASK_PLANNING.md) to brainstorm the next outcome with me using my current project documents. If you cannot retrieve that file, say so.
   ```

2. Add the outcome, problem, or improvement you want to explore, and the project location or document links if they are not already available. The agent reads the current project `PRD.md` and `AGENTS.md`; these are not the bootstrap templates. If you have no starting point, it recommends one.

Attachments or pasted project documents remain available when URL or repository access is unavailable.

This stage is a conversation: **discuss → decide → draft tasks → approve creation**. The agent brings options, recommendations, and focused questions, then waits for your response. It explores one outcome or related task group at a time, records accepted decisions, and prepares task briefs with scope, acceptance criteria, dependencies, and verification.

You review the concrete proposal before authorizing task creation. Once authorized, the agent rechecks access, helps restore a missing connection if needed, and creates or updates only the approved tasks. No tracker is required: reviewed briefs can remain the deliverable. Missing or deferred access is reported honestly, without blocking discussion or drafts.

Repeat this cycle for later outcomes. Routine task breakdown stays with the agent; individual tasks need more brainstorming only when they reveal material uncertainty. Creating tasks does not start implementation automatically.

## New project

Describe the outcome you want and any decisions already made. The agent proposes the smallest useful scope, recommends a suitable structure, and writes project-specific documents. Unknowns become clearly stated assumptions or decision points.

## Existing project

Open the project workspace, share its repository, or provide the relevant documents with your chat context when available. The agent inspects existing direction, rules, structure, and delivery conventions. Choose project creation/update to apply the document changes, or file generation to receive the revised documents without changing the project.

It preserves accepted decisions, useful setup instructions, unrelated work, and the distinction between intended behavior and what has actually shipped. It reconciles outdated or conflicting guidance rather than appending another competing rule set. Repeated runs reuse existing destinations and documents rather than creating duplicates.

## What the agent handles

1. **Understand:** inspect the supplied idea, existing material, and available tools.
2. **Shape:** define scope and requirements, make recommendations, and surface consequential decisions.
3. **Write:** create or update the tailored documents and remove irrelevant template sections.
4. **Check:** validate document consistency, references, and scope, then hand off to the separate planning conversation.

The agent owns the legwork. You remain the decision-maker for material scope or architecture choices and any required acceptance or release approval. Existing authorization is respected; routine reversible choices do not need repeated confirmation.

Project document generation with connection assistance and conversational task planning are separate workflows. Daily task execution, application implementation, unrelated account/infrastructure changes, and deployment happen only when separately requested or already authorized by the project's rules.

## Files

| File                                                         | Purpose                                                                      |
| ------------------------------------------------------------ | ---------------------------------------------------------------------------- |
| [PROJECT_BOOTSTRAP.md](PROJECT_BOOTSTRAP.md)                 | Main instructions, linked from the URL-based prompt.                         |
| [PROMPT_TEMPLATE.md](PROMPT_TEMPLATE.md)                     | Copy-ready prompt containing the bootstrap URL.                              |
| [TASK_PLANNING.md](TASK_PLANNING.md)                         | Separate instructions for brainstorming, task review, and approved creation. |
| [TASK_PLANNING_PROMPT.md](TASK_PLANNING_PROMPT.md)           | Copy-ready prompt containing the planning URL.                               |
| [templates/AGENTS.template.md](templates/AGENTS.template.md) | Structural reference for the agent generating working rules.                 |
| [templates/PRD.template.md](templates/PRD.template.md)       | Structural reference for the agent generating direction and requirements.    |
| [CONTRIBUTING.md](CONTRIBUTING.md)                           | Guidance for improving this kit.                                             |

The agent selects relevant modules for interfaces, technical design, data, external dependencies, AI product behavior, or delivery governance. None is assumed simply because the project uses an AI development assistant.
