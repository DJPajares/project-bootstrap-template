# Project Bootstrap Template

Give an AI agent your project idea or an existing project. First it generates the project documents. In a separate conversation, it helps you brainstorm an outcome and turn agreed decisions into reviewed tasks.

**The same attachments work for both new and existing projects.** No particular AI platform, technology stack, issue tracker, or hosting service is required.

## 1. Generate the project documents

1. Attach these three files unchanged: [PROJECT_BOOTSTRAP.md](PROJECT_BOOTSTRAP.md), [AGENTS.template.md](templates/AGENTS.template.md), and [PRD.template.md](templates/PRD.template.md).
2. Paste this short line into the chat:

   ```text
   Use the attached PROJECT_BOOTSTRAP.md, AGENTS.template.md, and PRD.template.md to bootstrap the project from my context below.
   ```

3. Add your idea dump, structured ideas, problem statement, or existing project context below the line and send it.

A paragraph is enough to start. Do not edit the attachments or fill in their placeholders. The agent organizes your context, gathers what it can, resolves routine gaps, and writes the documents. Missing consequential decisions are recorded with recommendations for later review, so document generation does not require a follow-up questionnaire. It stops after the documents and handoff; it does not draft or create implementation tasks.

## What the agent produces

- **`PRD.md`** — the project's purpose, audience, current scope, requirements, constraints, and decisions.
- **`AGENTS.md`** — practical rules for agents working on that project, including validation and human decision boundaries.
- **Supporting guidance when needed** — such as setup instructions, a technical decision record, or an operational runbook. Existing documents are updated instead of duplicated.
- **A short handoff** — what changed, what was checked, any decisions still needed, and a suggested outcome to discuss next.

With file access, the agent writes the documents. In a chat-only environment, it provides complete file contents ready to save. Draft decisions stay visibly distinct from approved ones.

## 2. Brainstorm and plan the tasks

Start a separate conversation when you are ready to plan work:

1. Attach [TASK_PLANNING.md](TASK_PLANNING.md) unchanged, plus the project's current `PRD.md` and `AGENTS.md` generated in stage 1. Use the actual project documents, not the reference templates.
2. Paste this short line into the chat:

   ```text
   Use the attached TASK_PLANNING.md, PRD.md, and AGENTS.md to brainstorm the next outcome with me before creating tasks.
   ```

3. Add the outcome, problem, or improvement you want to explore. If you have no starting point, the agent recommends one.

This stage is a conversation: **discuss → decide → draft tasks → approve creation**. The agent brings options, recommendations, and focused questions, then waits for your response. It explores one outcome or related task group at a time, records accepted decisions, and prepares task briefs with scope, acceptance criteria, dependencies, and verification.

You review the concrete proposal before authorizing task creation. Once authorized, the agent creates or updates the approved tasks in your selected system and verifies them. No tracker is required: reviewed briefs can remain the deliverable. Missing write access is reported honestly.

Repeat this cycle for later outcomes. Routine task breakdown stays with the agent; individual tasks need more brainstorming only when they reveal material uncertainty. Creating tasks does not start implementation automatically.

## New project

Describe the outcome you want and any decisions already made. The agent proposes the smallest useful scope, recommends a suitable structure, and writes project-specific documents. Unknowns become clearly stated assumptions or decision points.

## Existing project

Open the project workspace, share its repository, or provide the relevant documents with your chat context when available. The same attachments tell the agent to inspect the existing direction, rules, structure, and delivery conventions before updating anything. If access is unavailable, it produces complete drafts and clearly identifies what could not be verified.

It preserves accepted decisions, useful setup instructions, unrelated work, and the distinction between intended behavior and what has actually shipped. It reconciles outdated or conflicting guidance rather than appending another competing rule set. Running it again updates the same documents.

## What the agent handles

1. **Understand:** inspect the supplied idea, existing material, and available tools.
2. **Shape:** define scope and requirements, make recommendations, and surface consequential decisions.
3. **Write:** create or update the tailored documents and remove irrelevant template sections.
4. **Check:** validate document consistency, references, and scope, then hand off to the separate planning conversation.

The agent owns the legwork. You remain the decision-maker for material scope or architecture choices and any required acceptance or release approval. Existing authorization is respected; routine reversible choices do not need repeated confirmation.

Project document generation and conversational task planning are separate workflows. Daily task execution, application implementation, account setup, and deployment happen only when separately requested or already authorized by the project's rules.

## Files

| File                                                         | Purpose                                                                      |
| ------------------------------------------------------------ | ---------------------------------------------------------------------------- |
| [PROJECT_BOOTSTRAP.md](PROJECT_BOOTSTRAP.md)                 | Main instructions for the agent. Attach unchanged.                           |
| [PROMPT_TEMPLATE.md](PROMPT_TEMPLATE.md)                     | The short chat line that references the attachments.                         |
| [TASK_PLANNING.md](TASK_PLANNING.md)                         | Separate instructions for brainstorming, task review, and approved creation. |
| [TASK_PLANNING_PROMPT.md](TASK_PLANNING_PROMPT.md)           | The short chat line for the planning conversation.                           |
| [templates/AGENTS.template.md](templates/AGENTS.template.md) | Structural reference for the agent generating working rules.                 |
| [templates/PRD.template.md](templates/PRD.template.md)       | Structural reference for the agent generating direction and requirements.    |
| [CONTRIBUTING.md](CONTRIBUTING.md)                           | Guidance for improving this kit.                                             |

The agent selects relevant modules for interfaces, technical design, data, external dependencies, AI product behavior, or delivery governance. None is assumed simply because the project uses an AI development assistant.
