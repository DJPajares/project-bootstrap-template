# MCP and Context Budget

## Default local tool set

For routine implementation:

```text
Linear MCP  -> issue fetch, relations, comments when required, status updates
filesystem  -> repository reads and edits
git         -> branch, diff, commit, push
gh          -> pull request creation and URL
```

This is usually enough.

## Use other MCP servers on demand

Enable or invoke specialized tools only when the issue requires them:

- design-system MCP for component discovery or updates
- browser automation for browser-only verification
- database MCP for remote schema/data operations
- deployment MCP for environment or release work
- GitHub MCP when local `gh` cannot perform the required action

Avoid loading or invoking overlapping tools for the same information.

## Output controls

Prefer commands with bounded output:

```bash
rg -n "pattern" path
rg --files path | head -n 80
git diff --stat
git diff -- path/to/file
pnpm --filter <package> test -- <focused test>
```

Avoid unbounded recursive listings, full logs, or full repository diffs.

## Context escalation

Start at the issue's declared context budget. Escalate only when evidence requires it:

```text
lean -> standard -> deep
```

State the reason for escalation once. Do not restart broad discovery from scratch.

## Model escalation

Use the issue's minimum sufficient recommendation. Escalate to a stronger capability only when:

- architecture is materially ambiguous
- security or data integrity risk appears
- migration/concurrency/idempotency complexity exceeds issue assumptions
- repeated implementation attempts fail for reasoning rather than tooling

Do not escalate merely because the task has many files or a long test suite.
