# {{PROJECT_NAME}} — Project Requirements Document

> For the agent generating this file: resolve `{{placeholders}}` from the project context, remove this note, and delete irrelevant optional sections. Handle routine gaps yourself; record consequential unknowns as open decisions. Produce a complete project-specific document. A draft is not approved merely because this reference has been filled in.

**Status:** {{DRAFT_OR_APPROVED_STATE}}
**Owner:** {{REQUIREMENTS_OWNER}}
**Updated:** {{ISO_DATE}}
**Approval source:** {{EXPLICIT_APPROVAL_REFERENCE_OR_NOT_YET_APPROVED}}
**Current scope:** {{SCOPE_LABEL}}

This document defines the project's intended outcome and requirements. Approved sections are the product contract; proposals remain proposals. {{TASK_RECORD}} tracks implementation, dependencies, and known gaps. `AGENTS.md` defines execution and governance. {{VALIDATION_RECORD}} records observed evidence. Shipped behavior and task status do not silently amend requirements or prove launch readiness.

## 1. Overview

### Problem and context

{{WHO_HAS_WHAT_PROBLEM_IN_WHAT_CONTEXT_AND_WHY_CURRENT_ALTERNATIVES_FALL_SHORT}}

### Direction

{{CONCISE_VALUE_PROPOSITION_OR_PROJECT_OUTCOME}}

### Audience and stakeholders

| Audience/role               | Need or responsibility     | Relevant constraints        |
| --------------------------- | -------------------------- | --------------------------- |
| {{AUDIENCE_OR_STAKEHOLDER}} | {{NEED_OR_RESPONSIBILITY}} | {{CONTEXT_AND_CONSTRAINTS}} |

### Core principles

{{A_SMALL_SET_OF_PROJECT_SPECIFIC_PRINCIPLES_THAT_RESOLVE_TRADEOFFS}}

Principles guide decisions within scope; they do not authorize additional features or override explicit requirements.

## 2. Outcomes and success

| ID      | Desired outcome | Measure and evidence source | Target and evaluation window          | Status/owner                        |
| ------- | --------------- | --------------------------- | ------------------------------------- | ----------------------------------- |
| OUT-001 | {{OUTCOME}}     | {{OBSERVABLE_MEASURE}}      | {{TARGET_OR_OPEN_DECISION_REFERENCE}} | {{CONFIRMED_OR_PROPOSED_AND_OWNER}} |

Separate outcome measures from delivery milestones. Do not invent numeric targets, baselines, or research findings. Mark unknown targets as decisions to resolve.

## 3. Current scope and exclusions

### Current capabilities or deliverables

| ID        | Capability/deliverable        | Outcome served | Boundary                   | Requirement references | Decision status          |
| --------- | ----------------------------- | -------------- | -------------------------- | ---------------------- | ------------------------ |
| SCOPE-001 | {{CAPABILITY_OR_DELIVERABLE}} | OUT-001        | {{EXACT_CURRENT_BOUNDARY}} | REQ-001                | {{ACCEPTED_OR_PROPOSED}} |

Identify core work and necessary supporting work. Record approved extensions only when there is a real prior baseline and an explicit approval reference; a narrow extension does not authorize a broader deferred capability.

### Explicit non-goals

{{WHAT_THIS_SCOPE_DOES_NOT_PROVIDE_AND_ANY_EASY_TO_MISREAD_BOUNDARIES}}

### Deferred register

| Idea                     | Why outside current scope | Revisit condition               |
| ------------------------ | ------------------------- | ------------------------------- |
| {{DEFERRED_IDEA_IF_ANY}} | {{REASON}}                | {{EVIDENCE_OR_DECISION_NEEDED}} |

Deferred ideas are not requirements or instructions to build future infrastructure. Extend current concepts only when needed for accepted scope. Remove this table if there are no relevant deferred ideas.

## 4. Concepts, ownership, and lifecycle

### Shared vocabulary

| Concept     | Meaning                | Ownership/authority               | Boundary or important distinction   |
| ----------- | ---------------------- | --------------------------------- | ----------------------------------- |
| {{CONCEPT}} | {{PRECISE_DEFINITION}} | {{OWNER_OR_AUTHORITATIVE_SOURCE}} | {{WHAT_IT_DOES_AND_DOES_NOT_IMPLY}} |

### Relationships and invariants

- INV-001: {{A_RULE_THAT_MUST_REMAIN_TRUE_AND_THE_REQUIREMENTS_IT_CONSTRAINS}}
- {{INDEPENDENT_RELATIONSHIP_OR_SIGNAL_BOUNDARIES_IF_RELEVANT}}
- {{DELETION_UNLINKING_COPYING_AND_HISTORY_BOUNDARIES_IF_RELEVANT}}

### Lifecycle, if applicable

| From      | Trigger/actor                | Preconditions | To        | Effects and invalid/repeated-action behavior |
| --------- | ---------------------------- | ------------- | --------- | -------------------------------------------- |
| {{STATE}} | {{EXPLICIT_EVENT_OR_ACTION}} | {{GUARD}}     | {{STATE}} | {{OBSERVABLE_EFFECTS_AND_RECOVERY}}          |

Do not collapse independent states into a single flag. Distinguish user-declared, inferred, computed, and observed state where it affects behavior. Do not infer permission or completion from an unrelated signal.

## 5. Primary workflows

Repeat for each essential workflow or deliverable lifecycle. Use a workflow description rather than inventing an interface for a project that does not need one.

### FLOW-001 — {{WORKFLOW_NAME}}

- **Actor and purpose:** {{WHO_IS_TRYING_TO_ACHIEVE_WHAT}}
- **Entry/preconditions:** {{STARTING_CONTEXT_AND_REQUIRED_ACCESS}}
- **Minimum input:** {{WHAT_IS_NECESSARY_TO_START_AND_WHAT_CAN_WAIT}}
- **Sequence:** {{SHORTEST_COMPLETE_PATH}}
- **Result:** {{OBSERVABLE_OUTPUT_AND_STATE_CHANGE}}
- **Alternate/failure paths:** {{APPLICABLE_EMPTY_INVALID_DENIED_CANCELLED_INTERRUPTED_OR_UNAVAILABLE_STATES}}
- **Recovery:** {{WHAT_IS_PRESERVED_AND_HOW_WORK_CAN_RESUME_OR_BE_RETRIED}}
- **Requirement references:** {{REQ_IDS}}

## 6. Requirements

Repeat this block for each meaningful behavior or deliverable in current scope. Keep IDs stable when editing. Include only applicable fields; move implementation detail elsewhere when it obscures the behavioral contract.

### REQ-001 — {{REQUIREMENT_TITLE}}

- **Decision status/source:** {{ACCEPTED_WITH_REFERENCE_OR_PROPOSED}}
- **Purpose and scope:** {{OUTCOME_AND_SCOPE_IDS}}
- **Trigger and preconditions:** {{WHEN_IT_APPLIES_AND_REQUIRED_ACCESS_OR_INPUT}}
- **Required behavior/output:** {{PRECISE_OBSERVABLE_CONTRACT}}
- **Rules and invariants:** {{VALIDATION_PRECEDENCE_OWNERSHIP_AND_RELEVANT_INV_IDS}}
- **Failure and recovery:** {{REJECTION_PARTIAL_FAILURE_RETRY_CANCELLATION_AND_DATA_PRESERVATION_WHERE_RELEVANT}}
- **Dependencies:** {{ACTUAL_PREREQUISITES_OR_NONE}}
- **Acceptance criteria:**
  1. {{STARTING_CONDITION_ACTION_AND_OBSERVABLE_RESULT}}
  2. {{IMPORTANT_BOUNDARY_OR_FAILURE_RESULT}}
- **Verification:** {{FOCUSED_TEST_INSPECTION_OR_MANUAL_CHECK_AND_REQUIRED_EVIDENCE}}

An intended behavior is not evidence it is implemented. Keep live task status outside this section. A proposed solution must not become a required technology unless it has been accepted as a constraint.

## 7. Experience and quality requirements

Retain only relevant categories. Use observable expectations and accepted thresholds; link consequential unknowns to open gates.

| ID       | Applicable area  | Requirement/threshold                           | Verification | Decision status          |
| -------- | ---------------- | ----------------------------------------------- | ------------ | ------------------------ |
| QUAL-001 | {{QUALITY_AREA}} | {{OBSERVABLE_CONSTRAINT_OR_DECISION_REFERENCE}} | {{METHOD}}   | {{ACCEPTED_OR_PROPOSED}} |

Consider, where relevant:

- **Interface/content:** minimum input, progressive disclosure, navigation, loading, empty/error states, clarity, and preservation of context.
- **Accessibility:** target users, semantics, keyboard/focus behavior, assistive technology, reduced motion, and required standard if one is specified.
- **Language and formatting:** initial language scope, translation-ready content, units, number/date formats, and time interpretation where needed. Readiness for expansion is not a commitment to ship every locale.
- **Privacy/access:** private/public boundaries, permission enforcement, account or stakeholder isolation, and destructive-action safeguards.
- **Reliability/performance:** workload assumptions, response or processing targets, availability needs, recovery, and resource ceilings.
- **Maintainability/operations:** supported environments, compatibility, observable health, and responsibility for failure response.

Do not turn these categories into features or legal promises without context. Omit irrelevant categories and record unresolved consequential requirements explicitly.

## 8. Technical direction — optional

Retain for software or technically constrained work. Do not assume client/server separation, a database, a service architecture, or a particular repository layout.

### Constraints and decisions

| Area               | Requirement/constraint | Proposed or accepted direction | Rationale/tradeoff | Decision reference |
| ------------------ | ---------------------- | ------------------------------ | ------------------ | ------------------ |
| {{TECHNICAL_AREA}} | {{CONSTRAINT_OR_NEED}} | {{DIRECTION_AND_STATUS}}       | {{WHY_IT_FITS}}    | {{DEC_ID}}         |

### Responsibilities and interfaces

{{MINIMUM_STRUCTURE_NEEDED_FOR_CURRENT_SCOPE_WITH_CLEAR_OWNERSHIP_AND_BOUNDARIES}}

{{APPLICABLE_INPUT_OUTPUT_ERROR_CONCURRENCY_IDEMPOTENCY_AND_AUTHORIZATION_CONTRACTS}}

### Change and compatibility

{{APPLICABLE_MIGRATION_EXTERNAL_RESOURCE_OWNERSHIP_BACKWARD_COMPATIBILITY_AND_RECOVERY_REQUIREMENTS}}

Keep frequently changing commands, credentials, model identifiers, and environment configuration in supporting guidance. Do not create extension frameworks or extra systems solely for hypothetical future needs.

## 9. Information and external dependencies — optional

Retain for projects that store data, reuse external material, or call external services.

| Information/dependency        | Authoritative source and owner | Access and purpose                | Provenance/freshness                      | Permitted storage, reuse, attribution, and deletion | Failure behavior                           |
| ----------------------------- | ------------------------------ | --------------------------------- | ----------------------------------------- | --------------------------------------------------- | ------------------------------------------ |
| {{INFORMATION_OR_DEPENDENCY}} | {{SOURCE_AND_OWNER}}           | {{MINIMUM_NEEDED_ACCESS_AND_USE}} | {{SOURCE_TIME_VALIDITY_AND_REFRESH_RULE}} | {{VERIFIED_PERMISSION_AND_INTERNAL_POLICY}}         | {{WHAT_REMAINS_USABLE_AND_HOW_TO_RECOVER}} |

- Separate project-owned truth, user-authored information, external evidence, and derived results when their authority differs.
- Internal retention limits cannot override external permissions. Check rights before promising storage or reuse; preserve source and original evidence age through reuse and derivation.
- Define ownership, visibility, independent relationships, deletion, revocation, and incomplete-cleanup recovery where relevant.
- Bound external work across the whole operation: fan-out, retries, concurrency, quota, cost, and cancellation. Do not assume a cheap individual request remains cheap at aggregate scale.
- Specify unavailable, stale, ambiguous, or conflicting-evidence behavior. Do not invent missing facts or block core work unnecessarily when optional enrichment fails.

**Resource policy:** {{BUDGET_OWNER_OPERATION_BOUNDARIES_LIMITS_AND_VERIFICATION_OR_OPEN_GATE}}

## 10. Specialist contracts — optional

Retain only applicable subsections. Using AI to develop the project does not activate an AI product requirement.

### AI-assisted product behavior

{{ALLOWED_INPUTS_OUTPUTS_ACTIONS_AND_HUMAN_AUTHORITY}}

Specify evidence versus assumptions, deterministic validation, acceptance/apply boundaries, prevention of partial writes or duplicates, bounded calls and resource use, cancellation/recovery, privacy/retention, and quality evaluation. Model output and retrieved content cannot alter authorization or trusted rules. Identify required fallback behavior without assuming every product needs a manual equivalent. Keep model/provider configuration outside the enduring product contract unless explicitly constrained.

### Offline or synchronized work

{{EXACT_SUPPORTED_READS_WRITES_PREPARATION_AND_DEVICE_OR_ACCOUNT_SCOPE}}

Specify durable pending work, retry/idempotency, conflict handling, deletion/revocation, lost authorization, and reconnection. Distinguish removing a local copy from deleting authoritative data. Do not equate a past successful preparation with permanent readiness.

### Derived claims, estimates, or assessments

{{INPUT_AUTHORITY_EVIDENCE_THRESHOLDS_PROVENANCE_FRESHNESS_AND_INTERPRETATION_LIMITS}}

Keep user-confirmed facts distinct from estimates. Define missing/stale-evidence behavior and whether a result may be withheld. Do not present confidence as certainty or let derived advice silently overwrite an authoritative user decision.

## 11. Delivery, validation, and acceptance

### Dependency-based delivery slices

| Slice          | Useful outcome           | Requirements | Real prerequisites       | Exit evidence        |
| -------------- | ------------------------ | ------------ | ------------------------ | -------------------- |
| {{SLICE_NAME}} | {{REVIEWABLE_INCREMENT}} | {{REQ_IDS}}  | {{DEPENDENCIES_OR_NONE}} | {{OBSERVABLE_PROOF}} |

This sequence guides implementation at outcome level; it is not an executable task list or the live backlog and does not authorize task creation. Detailed decomposition follows a separate discussion and task-proposal review. Prefer useful increments over infrastructure for deferred capabilities.

### Validation policy

{{APPLICABLE_TESTS_INSPECTIONS_USER_WALKTHROUGHS_AND_OPERATIONAL_CHECKS_WITHOUT_DUPLICATING_AGENTS_EXECUTION_RULES}}

Validation records identify the artifact/version, environment, date, coverage, result, and known gaps. Distinguish simulation from live integration, specification review from runtime checks, and implementation checks from launch gates. Revalidate affected requirements after changes; preserve historical results as historical.

### Acceptance and release gates

| Gate                   | Required evidence | Decision owner | Work it blocks       |
| ---------------------- | ----------------- | -------------- | -------------------- |
| {{GATE_IF_APPLICABLE}} | {{EVIDENCE}}      | {{OWNER}}      | {{DEPENDENT_ACTION}} |

Define final acceptance against current requirements and outcome measures. For released or deployed work, identify applicable configuration, monitoring, resource controls, rollout, and recovery checks. Technical completion alone does not authorize publication or production changes.

## 12. Decisions, assumptions, and risks

### Decision register

| ID      | Question/decision | Status                                   | Options and recommendation/rationale | Owner and approval source           | Affected requirements or blocked work |
| ------- | ----------------- | ---------------------------------------- | ------------------------------------ | ----------------------------------- | ------------------------------------- |
| DEC-001 | {{DECISION}}      | {{PROPOSED_OPEN_ACCEPTED_OR_SUPERSEDED}} | {{OPTIONS_TRADEOFFS_AND_REASON}}     | {{OWNER_AND_REFERENCE_IF_ACCEPTED}} | {{IMPACT}}                            |

Only explicit authorization makes a decision accepted. Record meaningful changes and their impact; do not convert implementation drift into an approved requirement. Move detailed decision history to a separate record only when its size or audience warrants it.

### Assumptions and open questions

| ID      | Assumption/question        | Basis and confidence       | Impact if wrong | How to resolve/owner | Blocks work?                  |
| ------- | -------------------------- | -------------------------- | --------------- | -------------------- | ----------------------------- |
| ASM-001 | {{ASSUMPTION_OR_QUESTION}} | {{KNOWN_BASIS_OR_UNKNOWN}} | {{IMPACT}}      | {{RESOLUTION}}       | {{SPECIFIC_DEPENDENCY_OR_NO}} |

### Risks

| Risk              | Likelihood/impact | Mitigation or recovery     | Owner     | Trigger for action     |
| ----------------- | ----------------- | -------------------------- | --------- | ---------------------- |
| {{MATERIAL_RISK}} | {{ASSESSMENT}}    | {{PROPORTIONATE_RESPONSE}} | {{OWNER}} | {{OBSERVABLE_TRIGGER}} |

Keep this register proportionate to the project. Do not add generic risks or approval gates that have no material consequence for the current work.
