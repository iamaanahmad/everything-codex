# Adopt everything-codex safely

This repository provides templates and examples. It does **not** install a Codex plugin, register Skills, create automations, or set CLI policy merely by copying files. The supported setup varies by Codex client and changes over time, so use the [official Codex documentation](https://developers.openai.com/codex) for exact installation and configuration commands.

## 1. Choose your Codex surface

Use the surface that matches the work:

- **ChatGPT / cloud:** delegated work, remote environments, worktrees, background tasks, and scheduled automations.
- **IDE extension:** local development with editor context, diffs, and handoff to/from cloud tasks.
- **CLI:** local terminal workflows, approvals, scripts, and developer-controlled tool access.
- **GitHub:** pull-request review and repository workflow integration.
- **Managed workspace:** organization-wide policies, environment administration, monitoring, and analytics where available.

Availability depends on plan, region, device, and workspace policy. Do not hard-code models, pricing, commands, or plan eligibility in local documentation; verify them in the official docs at setup time.

## 2. Clone this library

```bash
git clone https://github.com/iamaanahmad/everything-codex.git
cd everything-codex
```

This is optional if you only need an individual template.

## 3. Add project instructions in the target repository

Create `AGENTS.md` at the target repository root. Codex uses repository instructions to understand your standards and expected validation.

```md
# Project instructions

## Commands
- Install: `npm ci`
- Lint: `npm run lint`
- Test: `npm test`

## Rules
- Preserve public API compatibility unless the task explicitly authorizes a breaking change.
- Never commit secrets or generated credentials.
- Ask before adding dependencies, changing infrastructure, or accessing production.
- Include tests run and any remaining risks in the final summary.
```

Keep instructions accurate. Do not add universal commands that the project cannot run.

## 4. Adapt an asset

### Prompt

Copy a relevant prompt from `prompts/`, replace placeholders, and provide it to Codex with the exact target and success criteria.

### Skill

Use a `skills/` directory as source material for a reusable Codex Skill or a project-specific instruction set. Read `instructions.md`, adapt tool requirements and validation steps, then create the Skill through the workflow supported by your Codex client. `skill.json` is a repository metadata template, not a guaranteed Codex manifest.

### Workflow

Use a directory in `workflows/` to plan parallel work. Name an integration owner, identify dependencies, and make each agent’s branch/worktree scope explicit. Do not assume a workflow JSON file launches agents by itself.

### Automation

Use an `automations/*.json` file as the brief for a scheduled task. Create the automation in the Codex client, then configure its schedule, time zone, notifications, context/thread behavior, access, and review requirements there. Start with read-only reporting before authorizing external writes.

### Configuration or MCP

Treat `configs/` as conceptual examples. Configure the CLI, IDE, app, or managed workspace using the current documented format. Keep credentials in a secret store or environment variables, and scope every token to the least capability needed.

## 5. Select an appropriate permission level

Start restricted. As you allow more capability, add compensating safeguards:

| Capability | When it is justified | Minimum safeguard |
| --- | --- | --- |
| Repository writes | A scoped implementation task | Review diff and run validation. |
| Shell commands | Build, tests, or a known local tool | Require confirmation outside the workspace. |
| Network access | Dependency installation or a known API | Restrict domains where supported; never send secrets. |
| MCP/plugin access | A task needs an approved external system | Use trusted servers and least-privilege credentials. |
| Scheduled work | Repetitive, low-risk work | Require review before merges, deployments, or ticket changes. |

## 6. Verify a small task

Before broad rollout, have Codex perform a reversible task such as:

1. Explain the project structure.
2. Run the documented test or lint command.
3. Draft a change without applying it, or make a small documentation change.
4. Report files changed, validation evidence, and remaining risks.
5. Review the result manually.

Only then enable deeper permissions or regular automations.

## Troubleshooting

### A template is not being recognized

Expected behavior: repository templates are not auto-discovered by Codex. Copy or adapt their instructions into the client-supported Skill, automation, project instruction, or prompt workflow.

### Instructions are ignored

Check that `AGENTS.md` is in the target repository and contains concrete, task-relevant guidance. Reduce conflicting or overly broad instructions, then start a new task/session if needed.

### An integration needs credentials

Never add a secret to a template or tracked config. Use the supported secrets/environment configuration for your Codex client and rotate exposed credentials immediately.

### An automation could make an external change

Disable or make it read-only until you have checked its scope, permissions, schedule, output destination, error behavior, and review gate.

## Keep current

Codex evolves quickly. Recheck the [official documentation](https://developers.openai.com/codex), the [Codex product page](https://chatgpt.com/codex/), and your client’s release notes whenever you upgrade or introduce a new integration.
