# Setup Automation Boundaries

The bootstrap should automate everything that can be safely performed through connected tools, but it must not pretend that account-level authorization and local machine access can be skipped.

## Automate by default

After GitHub and Linear are connected, ChatGPT should:

- create or update repository planning documents
- create or reuse the Linear Project
- create milestones, parent issues, executable issues, labels, priorities, and blocker relations
- include provider-neutral model routing in every executable issue
- publish full repository and Linear URLs

After Codex and Linear MCP are connected, Codex should:

- select or fetch the requested ready issue
- move the issue to In Progress
- verify the mutation before editing
- implement and run verification
- create and push the branch
- open the GitHub PR
- update Linear according to the configured completion mode
- post the completion report
- fetch and recommend the next ready issue

## Manual once, because authorization or device access is required

- create the GitHub repository, unless an authenticated GitHub CLI is deliberately used
- authorize GitHub and Linear apps in ChatGPT
- authorize the Linear MCP OAuth session in Codex
- install and sign in to Codex or the VS Code extension
- grant access to the local repository folder
- connect GitHub to Linear and configure workspace/team workflow automations
- enable and authorize ChatGPT mobile Remote access

## Semi-automatable

### Repository creation

A local authenticated GitHub CLI can create and clone a repository:

```bash
gh repo create owner/repository --private --clone
```

Do not make this the generic default because it depends on local CLI installation, GitHub authentication, organization permissions, visibility choices, and a selected filesystem location.

### Repository cloning

Codex can run:

```bash
gh repo clone owner/repository
```

The user must still choose or approve the local location and grant folder access.

### MCP configuration

The command can write configuration automatically:

```bash
codex mcp add linear --url https://mcp.linear.app/mcp
```

The OAuth approval remains manual.

## Rule for bootstrap-generated guides

Describe the shortest supported path. Do not add an optional integration to the mandatory first-time checklist. Put Codex Cloud, Claude Code, alternative IDEs, and advanced automation in optional sections unless the user selects them as the primary execution mode.
