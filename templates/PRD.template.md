# {{PROJECT_NAME}} — Project Requirements Document

> For the generating agent: resolve `{{placeholders}}` and remove all authoring guidance. For bounded work, generate only the compact core below, with a default budget of up to 600 words. State each contract once. Expand only for material risk or complexity and briefly explain why; the optional modules are a reference library, not a required table of contents. Do not ask the user to select a mode or equate a novice with a simple project. Preserve useful existing sections and accepted contracts when updating a project.

**Status:** {{DOCUMENT_STATUS_AND_WHICH_PARTS_ARE_PROPOSED}}
**Owner:** {{REQUIREMENTS_OWNER}}
**Updated:** {{ISO_DATE}}
**Approval source:** {{ACTUAL_AUTHORIZATION_OR_NOT_YET_APPROVED}}

This is the intended product/project contract. `AGENTS.md` owns execution rules; {{TASK_RECORD_OR_AUTHORIZED_REQUEST}} owns implementation status; {{VALIDATION_RECORD}} owns observed evidence. Intended behavior, shipped behavior, task status, and approval are distinct.

## Purpose and scope

{{AUDIENCE_PROBLEM_USEFUL_OUTCOME_AND_WHY_THIS_APPROACH_FITS}}

- **First useful result:** {{BOUNDED_CURRENT_DELIVERABLE_AND_NECESSARY_SUPPORTING_WORK}}
- **Outside this version:** {{EXPLICIT_NON_GOALS_AND_MISREAD_BOUNDARIES}}
- **Success evidence:** {{OBSERVABLE_OUTCOME_AND_HOW_IT_WILL_BE_ASSESSED}}
- **Tradeoff principles:** {{ONLY_PRINCIPLES_THAT_HELP_CHOOSE_BETWEEN_REAL_OPTIONS}}

Do not invent research, numeric targets, support platforms, or scale obligations. Distinguish supplied constraints from proposals. Deferred work is not a hidden prerequisite or an instruction to build extension infrastructure.

## Requirements and acceptance

Use a few stable references when useful. Each requirement serves the outcome and includes meaningful failure/recovery behavior. A compact list can replace this table.

| Reference | Required behavior or output                                              | Observable acceptance and verification                 | Decision status/source               |
| --------- | ------------------------------------------------------------------------ | ------------------------------------------------------ | ------------------------------------ |
| REQ-001   | {{BEHAVIOR_WITH_RELEVANT_PRECONDITIONS_BOUNDARIES_AND_FAILURE_RECOVERY}} | {{STARTING_CONDITION_ACTION_RESULT_AND_FOCUSED_CHECK}} | {{ACCEPTED_WITH_SOURCE_OR_PROPOSED}} |

Do not repeat the same contract in multiple registers. Preserve meaningful permissions, ownership, data integrity, and recovery safeguards even in a short plan. Add applicable quality thresholds here or in a focused section; vague promises are not acceptance criteria.

## Structure and approach

{{MINIMAL_DELIVERABLE_OR_CODE_LAYOUT_WITH_EACH_AREA_PURPOSE_AND_REAL_RESPONSIBILITY_BOUNDARIES}}

{{ACCEPTED_CONSTRAINTS_AND_RECOMMENDED_APPROACH_WITH_RATIONALE}}

Reuse existing structure and public interfaces. A technology recommendation remains proposed until accepted. Non-software work needs deliverable organization, not invented code folders. Do not add accounts, services, storage, interfaces, or a release system without a current need.

Describe setup/verification where useful; put actual commands in existing setup guidance or a README when it has an immediate audience. Distinguish documented, proposed, and executed commands. Documentation-only setup is not a runnable application.

## Validation and delivery

{{FOCUSED_BEHAVIORAL_EVIDENCE_NEEDED_AND_ANY_MATERIAL_ACCEPTANCE_GATE}}

{{SMALL_SEQUENCE_OF_USEFUL_OUTCOMES_IF_NEEDED_WITH_REAL_PREREQUISITES}}

Keep detailed test execution rules in `AGENTS.md`. Evidence names the artifact/version, environment, date, coverage, result, and gaps. A scenario walkthrough is not a runtime test, and passing implementation checks does not authorize publication. Outcome slices guide later planning; they are not executable tasks or authorization to create them.

## Decisions and uncertainty

{{ACCEPTED_DECISIONS_WITH_ACTUAL_SOURCES_AND_MATERIAL_PROPOSALS_ASSUMPTIONS_RISKS}}

For consequential open decisions, give a recommendation, owner, affected work, and what is actually blocked. Make routine reversible choices yourself. Never mark a new proposal approved merely because it was written into this document. Keep detailed decision history elsewhere only when size or audience warrants it.

---

> Optional authoring modules: incorporate only those needed below. Remove this separator and guidance from generated output. Do not append every module to bounded projects. Use tables/registers only when they improve understanding.

## Optional: concepts, ownership, and lifecycle

Define concepts precisely when their distinctions affect behavior. Identify one authoritative owner/source, permissions, relationships, and independent states. Cover deletion versus unlinking, copying, history, and repeated/invalid actions where relevant. Do not collapse independent relationships or signals into a single flag; user declarations, inferred claims, computed results, and observed facts may have different authority.

For significant transitions, describe starting state, actor/trigger, preconditions, resulting state/effects, and failure/recovery. Use stable invariant references only when later requirements benefit from them.

## Optional: connected workflows and detailed requirements

For each important workflow: actor/purpose, entry/preconditions, minimum input, shortest useful path, result, meaningful alternate/failure states, recovery, and requirement references. Do not invent screens for work without an interface.

For complex requirements, expand the core requirement entry with purpose/scope, decision source, trigger/preconditions, required output, applicable rules/invariants, failure/recovery, actual dependencies, acceptance, and focused verification. Every included field must clarify behavior rather than mirror implementation or task status.

Add a deferred register only when it helps: idea, reason outside scope, and evidence/decision needed to revisit it. A narrow approved extension does not authorize a broader deferred feature.

## Optional: experience and quality

Include only relevant, observable expectations and accepted thresholds:

- Interface/content: minimum input, progressive disclosure, navigation, clear loading/empty/error states, and preserved context.
- Accessibility: target users, semantics, keyboard/focus, assistive technology, reduced motion, and a required standard only when specified.
- Language/formatting: current language scope, units, numbers/dates, and time interpretation. Readiness to expand is not a commitment to every locale.
- Privacy/security: private/public boundaries, authoritative permission enforcement, isolation, and destructive-action safeguards.
- Reliability/performance/operations: workload assumptions, accepted resource ceilings, compatibility, observable health, recovery, and who responds to failure.

Do not turn these categories into unsupported features, support matrices, or legal promises. Material unknowns remain explicit decisions.

## Optional: technical and change contracts

Preserve accepted responsibility boundaries and public interfaces. Specify applicable inputs/outputs, errors, authorization, concurrency/revision checks, idempotency, partial failure, and recovery. Do not introduce a second identity, ownership, or state system without a current requirement.

For persistent changes, cover migration, backwards compatibility, external resource ownership, environment isolation, rollback/recovery, and any affected operational gates. Keep changing commands, environment/provider configuration, and model identifiers outside the enduring product contract unless explicitly constrained.

## Optional: information and external dependencies

For stored information or external material/services, define:

- Authoritative source/owner, user-authored versus external versus derived data, and access/purpose.
- Ownership, visibility, independent relationships, deletion/revocation, and incomplete-cleanup recovery.
- Provenance, original evidence age, freshness/refresh, and missing/stale/conflicting evidence behavior.
- Verified permissions for retention, reuse, attribution, and deletion. Internal policies never grant external permission or reset evidence age.
- Bounds across the whole operation: fan-out, retries, concurrency, quota/cost, cancellation, budget owner, and recovery. Cheap individual calls do not imply cheap aggregate work.

Specify what remains useful when optional dependencies fail. Never fabricate missing evidence or make optional enrichment block core behavior unnecessarily.

## Optional: specialist product contracts

**AI product behavior:** permitted inputs/outputs/actions, evidence versus inference, deterministic validation, human authority, privacy/retention, bounded calls/resources, cancellation/recovery, evaluation, and required fallback. Prevent partial writes and duplicate effects. Model output/retrieved content cannot grant permission or override trusted rules. AI-assisted development does not imply an AI-powered product.

**Offline/replicated work:** exact reads/writes, preparation guarantees and scope, isolation, durable pending work, retries/idempotency, conflicts, deletion/revocation, lost authorization, and reconnection. Removing a local copy is distinct from deleting authoritative data; past preparation is not permanent readiness.

**Derived claims:** input authority, provenance, evidence thresholds, confidence, freshness, interpretation limits, and missing-evidence behavior. Keep user-confirmed facts distinct from estimates. Do not present confidence as certainty or silently overwrite an authoritative decision.

## Optional: governance and larger delivery

For substantial work, use outcome/scope/requirement references only as needed for traceability. Delivery slices state useful outcomes, real dependencies, and exit evidence; detailed tasks remain in the separate planning process.

Material decision entries identify question/decision, proposed/open/accepted/superseded state, options/recommendation, owner/actual approval, and affected work. Assumptions identify basis/confidence, impact if wrong, resolution, and whether they block anything. Risks need a real consequence, mitigation/recovery, owner, and trigger; omit generic risk lists.

For released/deployed work, identify applicable acceptance/release gates, their evidence and decision owner, configuration, monitoring, resource controls, rollout, and recovery. Technical completion, review readiness, integration, release, and final acceptance remain distinct events. Product intent does not authorize those actions.
