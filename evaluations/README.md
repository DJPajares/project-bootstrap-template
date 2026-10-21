# Evaluating the bootstrap experience

This guide is for maintainers. It is not another setup step for people using the bootstrap.

The core question is whether an idea becomes useful direction and an appropriately sized project foundation with little work handed back to the user. Passing Markdown checks cannot establish that experience.

## Cases and execution

Use [cases.json](cases.json) as repeatable inputs. Each case declares its workflow, supplied context/capabilities, source availability, and observable expectations. The capabilities describe a test environment; they are not permission to configure real accounts or create resources.

1. Record the platform, actual reported model/settings, date, source revision and file fingerprints, case IDs, and test method. Do not hard-code a current model into standing instructions.
2. Start a fresh conversation for each case. For a controlled model test, supply the declared instruction/reference texts and capability context, then the user input. Record that URL retrieval and tools were simulated or unavailable. For a connected test, use the normal URL prompt and capture actual retrieval/tool outcomes instead.
3. Capture the response and any subsequent user turns, tool actions, or artifacts. Keep the test focused on its declared phase; initial-response cases need no full project generation.
4. Review the response against every applicable must/must-not expectation. Give pass, fail, blocked, or not tested, with concrete evidence. Do not let a lexical match stand in for a useful brief or a safe action.
5. For multi-turn delivery or task creation, add follow-up observations and verify actual destination effects only when that test and environment authorize them. Do not create real repositories/issues merely to test permissions.
6. Store a report and the necessary response evidence under `runs/`. Use synthetic examples; remove credentials and private account or project details. Prefer failed outcomes with an explanation over missing evidence.

## What to measure

| Measure                 | Observation                                                                                                                                                                                 |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| First useful value      | The first response identifies an audience/problem, recommends a bounded first version, and explains why. A repeated idea or setup menu does not pass.                                       |
| Blocking questions      | Count questions that require a reply before the next useful result. Separate the intended delivery choice, essential product clarification, and unnecessary service/technology questions.   |
| Setup friction          | Record authentication, destination, or service-selection requests before useful direction, and whether they were needed for the current action.                                             |
| Appropriate depth       | Scale product detail to scope without deleting agent-rule headings, numbered workflows, task fields, or completion formats. Do not reward a word limit at the cost of execution discipline. |
| Constraint preservation | Check stated technology, existing structure, approved requirements, user choices, and independent relationships.                                                                            |
| Concrete structure      | Verify the layout/setup approach fits the project, with proposed components/commands distinguished from existing or tested ones.                                                            |
| Handoff clarity         | Check file purpose, real references, material open decisions, and a usable next-stage starter with no editable placeholders.                                                                |
| Action boundaries       | Verify no target writes before delivery selection, no target changes for file-only output, and no tasks before concrete approval.                                                           |

Full-generation regressions must also verify the actual CLAUDE.md import, structured agent-rule sections, numbered execution workflow, task/model/manual-test fields, source-rule retention, and Current / Next completion format where applicable. A prose summary that mentions these topics is insufficient. Task-proposal review checks concrete project behavior, independently observable acceptance, real blockers, and meaningful manual steps; reject generic quality claims and repeated policy padding.

The first-response acceptance target is useful direction before setup questions. Optional tool setup must not block independent drafts. Existing explicit choices must not be asked again. Full delivery must contain resolved, tailored core documents and a usable planning handoff.

## Evidence levels

- **Static check:** file structure, links, references, formatting, or an instruction assertion.
- **Instruction walkthrough:** a reviewer reasons through a case without executing it in a fresh model conversation.
- **Controlled model run:** a model produces actual responses from the test inputs. Supplied sources or mocked capabilities do not prove real URL retrieval or integration behavior.
- **Connected integration run:** real retrieval or authorized tool effects are observed. Identify exactly which operations were exercised.
- **User study:** a real participant attempts the workflow. Record their experience and understanding with consent; a model role-playing a novice is not a user study.

Keep these levels separate in reports and PR descriptions. One model/configuration is not proof of cross-platform reliability, and a successful document-generation case is not a working application. A recorded model run can reveal instruction problems; it cannot establish that a first-time person understands or trusts the result.

## Records

- [2026-10-20 candidate review](runs/2026-10-20.md): static checks, actual controlled model responses, instruction refinements, and explicitly blocked or unverified coverage.

- [2026-10-21 structured-rule repair](runs/2026-10-21.md): source-rule retention, Claude bridge, and executable-task regression checks.
