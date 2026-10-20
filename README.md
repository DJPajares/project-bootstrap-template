# Project Bootstrap Template

Give an AI agent your project idea or an existing project. It does the discovery, makes recommendations, and creates the documents needed to start useful work.

**The same attachments work for both new and existing projects.** No particular AI platform, technology stack, issue tracker, or hosting service is required.

## Get started

1. Attach these three files unchanged: [PROJECT_BOOTSTRAP.md](PROJECT_BOOTSTRAP.md), [AGENTS.template.md](templates/AGENTS.template.md), and [PRD.template.md](templates/PRD.template.md).
2. Paste this short line into the chat:

   ```text
   Use the attached PROJECT_BOOTSTRAP.md, AGENTS.template.md, and PRD.template.md to bootstrap the project from my context below.
   ```

3. Add your idea dump, structured ideas, problem statement, or existing project context below the line and send it.

A paragraph is enough to start. Do not edit the attachments or fill in their placeholders. The agent organizes your context, gathers what it can, resolves routine gaps, and writes the documents. Missing consequential decisions are recorded with recommendations for later review, so document generation does not require a follow-up questionnaire.

## What the agent produces

- **`PRD.md`** — the project's purpose, audience, current scope, requirements, constraints, and decisions.
- **`AGENTS.md`** — practical rules for agents working on that project, including validation and human decision boundaries.
- **Supporting guidance when needed** — such as setup instructions, a technical decision record, or an operational runbook. Existing documents are updated instead of duplicated.
- **A short handoff** — what changed, what was checked, any decisions still needed, and the first useful implementation step.

With file access, the agent writes the documents. In a chat-only environment, it provides complete file contents ready to save. Draft decisions stay visibly distinct from approved ones.

## New project

Describe the outcome you want and any decisions already made. The agent proposes the smallest useful scope, recommends a suitable structure, and writes project-specific documents. Unknowns become clearly stated assumptions or decision points.

## Existing project

Open the project workspace, share its repository, or provide the relevant documents with your chat context when available. The same attachments tell the agent to inspect the existing direction, rules, structure, and delivery conventions before updating anything. If access is unavailable, it produces complete drafts and clearly identifies what could not be verified.

It preserves accepted decisions, useful setup instructions, unrelated work, and the distinction between intended behavior and what has actually shipped. It reconciles outdated or conflicting guidance rather than appending another competing rule set. Running it again updates the same documents.

## How the process works

1. **Understand:** inspect the supplied idea, existing material, and available tools.
2. **Shape:** define scope and requirements, make recommendations, and surface consequential decisions.
3. **Write:** create or update the tailored documents and remove irrelevant template sections.
4. **Check:** validate consistency, references, scope, and readiness for the first implementation step.

The agent owns the legwork. You remain the decision-maker for material scope or architecture choices and any required acceptance or release approval. Existing authorization is respected; routine reversible choices do not need repeated confirmation.

The bootstrap ends with usable project documents and an implementation starting point. Daily task execution, application implementation, external backlog creation, account setup, and deployment happen only when separately requested or already authorized by the project's rules.

## Files

| File                                                         | Purpose                                                                   |
| ------------------------------------------------------------ | ------------------------------------------------------------------------- |
| [PROJECT_BOOTSTRAP.md](PROJECT_BOOTSTRAP.md)                 | Main instructions for the agent. Attach unchanged.                        |
| [PROMPT_TEMPLATE.md](PROMPT_TEMPLATE.md)                     | The short chat line that references the attachments.                      |
| [templates/AGENTS.template.md](templates/AGENTS.template.md) | Structural reference for the agent generating working rules.              |
| [templates/PRD.template.md](templates/PRD.template.md)       | Structural reference for the agent generating direction and requirements. |
| [CONTRIBUTING.md](CONTRIBUTING.md)                           | Guidance for improving this kit.                                          |

The agent selects relevant modules for interfaces, technical design, data, external dependencies, AI product behavior, or delivery governance. None is assumed simply because the project uses an AI development assistant.
