# Provider-compatible model routing

## Principle

Linear issues must be runnable by either Codex/OpenAI or Claude/Anthropic. The stable recommendation is a capability profile and reasoning requirement, not a permanent model name.

## Issue format

Every executable issue includes:

```md
## Suggested AI

- Capability profile: `implementation-general`
- Reasoning requirement: `high`
- Codex/OpenAI recommendation: `<current compatible model or current provider alias>`
- Claude/Anthropic recommendation: `<current compatible model or current provider alias>`
- Recommendation resolved at: `<ISO timestamp>`
- Selection rationale: `<one sentence tied to task complexity>`
```

## Resolution algorithm

At bootstrap creation, bootstrap refresh, or issue refresh:

1. Inspect the models actually available in the target Codex/OpenAI environment.
2. Inspect the models actually available in the target Claude/Anthropic environment.
3. Select one compatible recommendation from each provider based on the capability profile, context needs, tools, multimodality, latency, and cost.
4. Confirm the selected model supports the requested reasoning/effort control. If the provider does not expose the same levels, map the requirement to its closest supported mode.
5. Write both current recommendations and a resolution timestamp into the Linear issue.
6. Keep the capability profile canonical so future refreshes can replace stale names without changing task intent.

When a provider/model catalog cannot be inspected, write:

```text
Codex/OpenAI recommendation: resolve at execution time
Claude/Anthropic recommendation: resolve at execution time
```

Do not invent a model name.

## Capability profiles

### `deep-architecture`

Use the strongest available coding/reasoning model for architecture, auth, migrations, complex data flow, major refactors, and ambiguous cross-cutting work. Typical reasoning: high or xhigh.

### `implementation-general`

Use the balanced current coding model for normal feature implementation, non-trivial forms, API work, and integration tests. Typical reasoning: medium or high.

### `fast-bounded`

Use a current fast/cost-efficient coding model for clear, small, repeatable changes with narrow verification. Typical reasoning: low or medium.

### `visual-design`

Use a current model with strong visual/multimodal and frontend ability when screenshots or visual references matter. Typical reasoning: high.

### `research-analysis`

Use a strong current research/reasoning model for discovery, comparison, technical investigation, and evidence synthesis. Typical reasoning: high.

### `verification-review`

Use an independent strong reviewer model for security, architecture validation, regression review, and high-risk changes. Typical reasoning: high or xhigh.

## Refresh rule

When the bootstrap is rerun, identify issues whose `Recommendation resolved at` value is older than the project's configured freshness window or whose model is unavailable. Update only the recommendation fields and timestamp; do not alter scope, acceptance criteria, status, or dependencies.

## Completion rule

The completed issue report must fetch the next issue and reproduce its provider recommendations and reasoning exactly. The agent may explain the choice, but it must not silently replace the Linear recommendation.
