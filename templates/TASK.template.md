# {{CONCRETE_TASK_TITLE}}

> Authoring instructions: this reference is for the planning agent. Resolve fields from the accepted outcome, project rules, relevant implementation, and actual task destination. Remove this note and all placeholders. Use the project's established task format if it is more specific; never replace it with generic prose. Keep all core sections below, with short concrete entries. Manual Test is conditional on meaningful human verification. Do not create or publish tasks before the reviewed batch is authorized.

## Description

{{SPECIFIC_CHANGE_AFFECTED_BEHAVIOR_AND_WHY_IT_IS_USEFUL}}

Requirements: {{RELEVANT_CURRENT_PRD_SECTIONS_OR_REQUIREMENT_REFERENCES_AND_DECISION_STATUS}}.

## Scope

**Included**

- {{EXACT_IN_SCOPE_BEHAVIOR_OR_DELIVERABLE}}

**Excluded**

- {{NEARBY_WORK_DELIBERATELY_NOT_INCLUDED}}

## Suggested Models & Reasoning

- **Platform/model:** {{SMALLEST_CAPABLE_CURRENTLY_VERIFIED_MODEL_OR_CAPABILITY_WITH_EXACT_MODEL_UNVERIFIED}}
- **Reasoning:** {{SUITABLE_REASONING_EFFORT}}
- **Reason:** {{BRIEF_TASK_SPECIFIC_JUSTIFICATION}}

Resolve names at drafting time. Missing catalog access does not justify inventing a model or blocking the task draft. Do not require delegation unless authorized.

## Acceptance Criteria

1. {{STARTING_CONDITION_ACTION_AND_OBSERVABLE_RESULT}}
2. {{MATERIAL_BOUNDARY_OR_FAILURE_RESULT}}
3. {{INTEGRITY_OR_COMPATIBILITY_RESULT_WHEN_RELEVANT}}

Use only meaningful criteria; a real task may need fewer or more. “Complete implementation,” “works correctly,” and “follow best practices” are not acceptance criteria. Do not move consequential behavior into an undefined “agreed policy.” Reference the actual accepted decision, or identify a blocker.

## Dependencies

- **Blocked by:** {{ACTUAL_TASK_OR_DECISION_AND_EXACT_BLOCKED_WORK_OR_NONE}}
- **Blocking:** {{KNOWN_ACTUAL_TASK_REFERENCES_OR_NONE_KNOWN}}
- **Readiness:** {{READY_CONDITIONAL_OR_BLOCKED_WITH_CONCRETE_REASON}}

Use proposal references before creation and map them to real IDs/relationships afterward. Never invent identifiers, depend on every preceding task by default, or create unapproved prerequisites.

## Execution Context and Verification

- **Read/reuse:** {{TASK_RELEVANT_REQUIREMENTS_DECISIONS_EXISTING_COMPONENTS_AND_INSPECTED_PATHS}}
- **Checks:** {{FOCUSED_AUTOMATED_INSPECTION_OR_RUNTIME_CHECKS_AND_EXPECTED_EVIDENCE}}
- **Commands:** {{ACTUAL_PROJECT_COMMANDS_IF_KNOWN_OTHERWISE_WHAT_MUST_BE_ESTABLISHED}}

Label proposed paths as proposed. Link to global execution rules instead of repeating their authorization/evidence disclaimers in every issue. Do not imply implementation or tests already ran.

## Manual Test

Retain only when a person can meaningfully verify the result. Use real product terms and starting state; when UI does not yet exist, label this as a future verification procedure.

1. {{CONCRETE_SETUP_OR_ENTRY}}
2. {{ACTION_WITH_SPECIFIC_INPUT}}
3. {{OBSERVABLE_EXPECTED_RESULT}}
4. {{IMPORTANT_FAILURE_OR_RECOVERY_CHECK_WHEN_RELEVANT}}

> Pre-publication check: could this task be pasted unchanged into an unrelated project? If so, add the missing project behavior, constraint, affected area, or observable result. Remove generic adjectives and copied policy padding. Check the scope is one reviewable outcome, the acceptance is independently verifiable, dependencies are real, and the model/manual-test fields follow the project rules. This check is for the author, not text to append to the issue.
