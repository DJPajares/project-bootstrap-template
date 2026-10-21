# Project Bootstrap Template

**Bring the idea. Get a clear direction, a well-structured project foundation, and an easy next step.**

You do not need to know the technology, write requirements, or choose development tools first. The agent does the discovery, makes recommendations, and creates the appropriate documents. Existing projects and engineering constraints are supported too.

## Start with your idea

Copy this prompt into an AI platform that can read URLs:

```text
Read and follow [PROJECT_BOOTSTRAP.md](https://raw.githubusercontent.com/DJPajares/project-bootstrap-template/main/PROJECT_BOOTSTRAP.md) using my project context below. If you cannot retrieve that file, say so.
```

Add your idea dump, problem statement, structured requirements, or existing project context beneath it and send. A paragraph is enough. No template downloads or edits are needed.

## What happens first

The agent gives you a short, useful project brief before asking about setup: who the project serves, what it should achieve, a recommended first version, what can wait, and important assumptions. It recommends a direction instead of handing every decision back to you.

Then you choose how to receive the result:

- **Set up my project:** write the documents into an authorized project folder or supported repository, or update an existing project in place.
- **Give me the files:** receive downloadable documents where supported, otherwise complete Markdown contents. Your project and repositories remain untouched.

If you already supplied the choice and destination, the agent continues without asking again. It makes no target writes before your choice. Project setup creates the documentation foundation; building the application comes later.

## What you receive

- **A project plan (`PRD.md`):** purpose, users, current scope, requirements, important boundaries, and decisions.
- **Agent working rules (`AGENTS.md`):** structured working rules, numbered execution workflows, task fields, testing/review policy, and a completion-response format. The agent preserves useful existing rules rather than summarizing them away.
- **A Claude entry file (`CLAUDE.md`):** imports `AGENTS.md` so shared rules have one authoritative home.
- **An appropriate structure:** a minimal proposed layout and setup approach where useful, preserving existing structure and constraints. A small utility gets concise documents; complex work gets the detail its risks need.
- **Supporting guidance only when useful:** such as a README explaining the project and how its actual setup works. Proposed commands are distinguished from verified ones.
- **A personalized handoff:** file/project links, material open decisions, and a ready-to-copy prompt for the next planning conversation, with your actual project references filled in.

You do not need to select a document mode or identify as a beginner or expert. The agent adjusts its explanations and preserves the necessary rigor. It does not introduce accounts, databases, multiple services, or elaborate infrastructure without a current need.

## Connections when you need them

The agent quietly checks existing capabilities. It helps connect repository access when the selected delivery or inspection needs it, and your chosen task system when you want to configure task delivery or publish reviewed tasks. You can request setup earlier, or defer it. GitHub, Linear, and other services are optional.

The agent handles supported configuration, guides only necessary sign-in/consent steps, and verifies relevant access. A listed connector does not guarantee write permissions or repository creation capability. Missing optional access does not block the brief, independent drafts, or file generation. File-only delivery also leaves target configuration untouched.

If the AI cannot read the instruction URL, paste the instructions or attach [PROJECT_BOOTSTRAP.md](PROJECT_BOOTSTRAP.md) unchanged; its [agent-rules](templates/AGENTS.template.md) and [requirements](templates/PRD.template.md) references are optional fallbacks. The agent must disclose unread sources and actual capability limits.

## Brainstorm the work next

Use the personalized starter in your handoff for a **separate planning conversation**. It already names your project/current documents and a suggested starting outcome. When generated files have no stable links, the handoff tells you to attach those actual project documents; you do not need to reconstruct the context.

You can also use this general starter and provide the project location or current documents:

```text
Read and follow [TASK_PLANNING.md](https://raw.githubusercontent.com/DJPajares/project-bootstrap-template/main/TASK_PLANNING.md) to brainstorm the next outcome with me using my current project documents. If you cannot retrieve that file, say so.
```

The process is **discuss → decide → draft tasks → approve creation**. The agent brings options and focused questions, waits for feedback, records accepted decisions, and prepares concrete tasks using the project's schema: description, scope, suggested models/reasoning, observable acceptance criteria, real dependencies, execution context/verification, and meaningful manual tests. It explores one useful outcome or related group at a time and handles routine decomposition itself. Generic tasks that could be pasted unchanged into another project need revision before publication.

Only the reviewed tasks you authorize are created in the selected system. Without a tracker, the briefs remain useful output. Task creation does not start implementation automatically, and settled decisions do not need repeated brainstorming.

## Existing projects and engineering constraints

Provide the repository/workspace and any constraints already decided. The agent reads relevant context, preserves approved requirements and unrelated work, reuses the established layout, and updates existing documents rather than generating competing versions. Explicit delivery and technology choices are respected. No new stack or workflow is imposed by this kit.

## Files and evaluation

| File                                                         | Purpose                                                            |
| ------------------------------------------------------------ | ------------------------------------------------------------------ |
| [PROMPT_TEMPLATE.md](PROMPT_TEMPLATE.md)                     | The short bootstrap prompt to copy.                                |
| [PROJECT_BOOTSTRAP.md](PROJECT_BOOTSTRAP.md)                 | Deeper instructions retrieved by the agent.                        |
| [templates/PRD.template.md](templates/PRD.template.md)       | Requirements reference, scaled to each project.                    |
| [templates/AGENTS.template.md](templates/AGENTS.template.md) | Structured operating rules, task workflow, and response format.    |
| [templates/CLAUDE.template.md](templates/CLAUDE.template.md) | One-way import of the authoritative agent rules.                   |
| [templates/TASK.template.md](templates/TASK.template.md)     | Concrete task fields and pre-publication quality checks.           |
| [TASK_PLANNING_PROMPT.md](TASK_PLANNING_PROMPT.md)           | General starter for the later planning conversation.               |
| [TASK_PLANNING.md](TASK_PLANNING.md)                         | Discussion, task review, and authorized creation.                  |
| [Evaluation guide](evaluations/README.md)                    | Maintainer scenarios, evidence requirements, and recorded results. |
| [CONTRIBUTING.md](CONTRIBUTING.md)                           | Rules for improving this kit.                                      |

The instructions define the intended experience. Evaluation records distinguish static checks, controlled model runs, connected integrations, and actual user studies; none alone proves every platform or project works.
