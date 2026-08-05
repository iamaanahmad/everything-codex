# everything-codex contributor instructions

## Purpose

This is a curated **template library** for OpenAI Codex workflows. It is not a Codex plugin, package, or configuration schema. The JSON files in `automations/`, `workflows/`, and `configs/` are planning and adaptation templates; copying them into `~/.codex` does not make Codex execute or load them automatically.

## Repository layout

- `skills/`: reusable task instructions and related resources
- `automations/`: scheduled-work prompt templates for Codex Automations
- `workflows/`: multi-agent planning templates
- `prompts/`: copy-ready prompt libraries
- `configs/`: illustrative policy/configuration examples; validate against current official Codex documentation before use
- `examples/`: example projects and implementation references

## Contribution rules

- Keep a template focused on one job and state its assumptions, prerequisites, permissions, and expected output.
- Never include secrets, access tokens, or real customer data.
- Mark product-specific behavior as a template unless it is verified against current official Codex documentation.
- Prefer `AGENTS.md` for project instructions. Codex follows repository instruction files; keep instructions concise, testable, and scoped to the project.
- Do not claim that a CLI command, config key, model, or integration exists unless it has been verified in the official documentation.

## Documentation checks

Before submitting documentation changes:

1. Ensure documented paths exist.
2. Do not present templates as auto-discovered or executable product configuration.
3. Avoid hard-coded plan pricing, model inventories, or competitor assertions that rapidly become stale.
4. Add relevant official-source links for product behavior.
