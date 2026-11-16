# everything-codex status

## Status: active template library

**Last reviewed:** 2026-11-16

This repository is a documentation and template collection for teams using OpenAI Codex. It is not an executable package or an authoritative Codex configuration distribution.

## Current inventory

The repository contains these asset families:

- **Skills:** reusable development, deployment, design, project-management, and documentation procedures.
- **Automation briefs:** examples for issue triage, CI summaries, releases, bug detection, dependency updates, security scanning, and performance monitoring.
- **Workflow plans:** feature development, bug fixes, refactoring, and deployment coordination.
- **Prompt libraries:** review, architecture, testing, debugging, performance, and security prompts.
- **Configuration examples:** team/policy, sandbox, personality, and MCP concepts.
- **Examples:** web application, API service, and game-development sample projects.

Refer to the directory tree rather than this document for exact file counts; counts are intentionally omitted to avoid drift.

## Current Codex alignment

Repository guidance has been updated to align with current documented Codex patterns:

- `AGENTS.md` is the project-instructions convention used by this library.
- Skills, JSON configuration examples, workflow definitions, and automation definitions are described as **adaptable templates**, not auto-installed product artifacts.
- Current Codex usage is documented across ChatGPT/cloud, CLI, IDE, GitHub, skills/plugins/MCP, and scheduled work.
- The official documentation now also covers hooks, Git worktrees, cloud environments, the Codex SDK, App Server, GitHub Action, non-interactive mode, and GitLab (Beta), Slack, and Linear integrations.
- Product access, models, pricing, and client-specific command lines are deferred to official documentation rather than maintained as fragile repository claims.
- Permission, review, validation, and secret-handling guidance is now a first-class requirement.

## Known constraints

- Template fields may not match the current schema of a particular Codex client.
- Feature availability varies by ChatGPT plan, region, operating system, workspace policy, and rollout status.
- Any action involving external systems, network access, deployments, or credentials requires project-specific review.

## Maintenance policy

When Codex capabilities change, update the guidance only after checking official sources. Prefer durable operating principles over transient model lists and pricing tables. Review the following files together when making a platform-alignment change:

- `README.md`
- `INSTALL.md`
- `CONTRIBUTING.md`
- `AGENTS.md`
- `CHANGELOG.md`

## References

- [Codex in ChatGPT](https://chatgpt.com/codex/)
- [Official Codex documentation](https://learn.chatgpt.com/docs)
- [Codex changelog](https://learn.chatgpt.com/docs/changelog)
- [Feature maturity](https://learn.chatgpt.com/docs/feature-maturity)
- [Codex product updates](https://openai.com/index/introducing-upgrades-to-codex/)
