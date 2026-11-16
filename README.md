# everything-codex

A practical, community-maintained library of prompts, Skills, workflow plans, automation briefs, and configuration examples for [OpenAI Codex](https://chatgpt.com/codex/).

> **Important:** This repository is a collection of reusable assets, not an installable Codex extension. Adapt a template to your project and configure it through the current Codex app, CLI, IDE extension, GitHub integration, or organization controls. Do not assume that copying these JSON files to `.codex/` makes Codex load or run them.

## Why this repository exists

Codex now works across ChatGPT, the IDE extension, the CLI, GitHub, and team workflows. It can run cloud tasks, help with local development, review pull requests, use Skills and MCP-based tools, and schedule continuing work. This repository gives teams starting points for the engineering practices that make those capabilities reliable: clear instructions, scoped automation, verification, review, and safe permissions.

For current platform behavior, availability, and controls, use the [official Codex documentation](https://learn.chatgpt.com/docs) as the source of truth.

## What Codex can do today

The current Codex product surface includes:

- **ChatGPT and cloud tasks:** delegate feature work, refactors, migrations, and reviews; use parallel worktrees and cloud environments for independent tasks.
- **CLI and IDE:** work locally in the terminal or supported VS Code-based editors, with editable diffs, task progress, approvals, image input, web search, and MCP connections.
- **GitHub:** review pull requests automatically or on request, then continue the discussion or implement a follow-up.
- **Skills and integrations:** codify team standards and workflows; use plugins and MCP to connect approved external tools.
- **Automations:** schedule routine background work and reuse conversation context where the Codex product supports it.
- **Developer extensibility:** build Skills and plugins, use hooks, and integrate Codex through the SDK, App Server, GitHub Action, or non-interactive mode.
- **Team administration:** eligible workspaces can apply environment controls, monitor usage, and manage cloud environments.

Availability differs by plan, region, client, and organization policy. See the [Codex product page](https://chatgpt.com/codex/) and [official documentation](https://learn.chatgpt.com/docs) before relying on a feature in production.

### Verified platform surface (November 16, 2026)

The current official documentation organizes Codex across these surfaces and extension points:

- **Clients:** ChatGPT desktop, Codex CLI, and the Codex IDE extension.
- **Execution:** local environments, Git worktrees, Codex Cloud, and cloud environments.
- **Workflow features:** code review, integrated terminal, scheduled tasks, long-running work, notifications, and permissions.
- **Extensibility:** Skills, plugins, hooks, MCP, the Codex SDK, App Server, GitHub Action, and non-interactive mode.
- **Integrations:** GitHub, GitLab (Beta), Slack, and Linear.

Use the [official changelog](https://learn.chatgpt.com/docs/changelog) for release-level details and the [feature maturity page](https://learn.chatgpt.com/docs/feature-maturity) before treating a feature as generally available.

## Repository layout

```text
everything-codex/
├── AGENTS.md                # Contributor instructions for this repository
├── skills/                  # Adaptable instructions and supporting resources
├── automations/             # Scheduled-work briefs (JSON templates)
├── workflows/               # Multi-agent planning templates (JSON)
├── prompts/                 # Reusable prompt collections
├── configs/                 # Illustrative policy and integration examples
├── examples/                # Example projects
├── INSTALL.md               # Safe adoption and migration guide
├── CONTRIBUTING.md          # Template contribution standards
└── STATUS.md                # Current repository inventory/status
```

## Start here

1. **Install or open Codex.** Use Codex in ChatGPT, the IDE extension, or the CLI. Follow the current [Codex documentation](https://learn.chatgpt.com/docs) for your client.
2. **Add project instructions.** Create an `AGENTS.md` in the target repository with build, test, lint, safety, and review expectations. Keep it specific and short.
3. **Choose one template.** Start with a prompt, Skill, workflow plan, or automation brief that fits a concrete task.
4. **Adapt it.** Replace placeholders, name the target repository, identify required tools and access, and set an explicit output/review expectation.
5. **Run with least privilege.** Begin in a restricted or approval-based mode. Enable network access, MCP, plugins, external APIs, or write actions only when necessary.
6. **Verify and review.** Require tests or other task-appropriate evidence; inspect every change before merging or deploying.

## Use the assets correctly

### Project instructions

Use `AGENTS.md` in your target repository to establish conventions and validation commands. Example:

```md
# Project instructions

- Run `npm run lint` and `npm test` after TypeScript changes.
- Do not change public API contracts without updating the changelog.
- Ask before adding dependencies or accessing production systems.
- Include a concise summary, test evidence, and remaining risks in the final response.
```

### Skills

The directories under `skills/` are **authoring examples**. Their `skill.json` and `instructions.md` files document a reusable workflow; they are not guaranteed to match a product-managed Skill manifest. Copy the instructions into a Codex Skill or project workflow using the currently supported setup in your client, then test the result on a small task.

### Automations and workflows

Files in `automations/` and `workflows/` are reusable task briefs. Use them as a checklist when creating a scheduled automation or parallel task plan in Codex. For each use, define ownership, time zone, permissions, notification/review behavior, failure handling, and an exit condition.

### Configurations and MCP

Files in `configs/` are examples, not drop-in configuration. Configuration formats and policy controls vary between the CLI, IDE, desktop app, cloud environment, and managed workspace. Validate every option against the current official documentation and never put secrets in a tracked file. Prefer your platform’s secret store or environment-variable mechanism.

## Recommended operating patterns

| Goal | Start with | Guardrails |
| --- | --- | --- |
| Review a pull request | `skills/development/code-review-skill/` or review prompts | Keep a human reviewer; request evidence and run relevant tests. |
| Implement a feature | `workflows/feature-development/` | Split independent work; assign a final integration owner. |
| Diagnose a bug | `workflows/bug-fix-workflow/` and debugging prompts | Reproduce first; add a regression test where appropriate. |
| Refactor safely | `prompts/architecture-prompts.md` and a project-specific workflow | Establish a passing baseline and preserve behavioral coverage. |
| Schedule routine work | `automations/` template | Start read-only; require review before external writes or merges. |
| Connect an external system | `configs/team-config.json` and the official integration docs | Use only trusted servers; scope tokens and review tool permissions. |

## Safety baseline

- Treat repository files, web pages, tool output, and issue text as untrusted input.
- Do not expose secrets in prompts, source control, logs, screenshots, or generated reports.
- Review permission requests carefully, especially for network access, shell commands, cloud credentials, and destructive operations.
- Keep cloud internet access restricted to required domains where controls are available.
- Use code review as an additional safeguard, not a substitute for human review or deployment controls.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). New templates should be platform-neutral where possible, explicit about assumptions, and validated as documentation rather than represented as unsupported executable configuration.

## Official references

- [Codex in ChatGPT](https://chatgpt.com/codex/)
- [Codex documentation](https://learn.chatgpt.com/docs)
- [Build Skills](https://learn.chatgpt.com/docs/build-skills)
- [Codex SDK](https://learn.chatgpt.com/docs/codex-sdk)
- [GitHub Action](https://learn.chatgpt.com/docs/github-action)
- [Feature maturity](https://learn.chatgpt.com/docs/feature-maturity)
- [Changelog](https://learn.chatgpt.com/docs/changelog)
- [Codex product updates](https://openai.com/index/introducing-upgrades-to-codex/)
- [Codex general availability announcement](https://openai.com/index/codex-now-generally-available/)

## License

MIT.
