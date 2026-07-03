# everything-codex

Production-ready collection of Codex configurations, skills, automations, and workflows.

## Project Structure

- `skills/` - Codex Skills organized by category (development, deployment, design, project-management, documentation)
- `automations/` - Background automation JSON templates
- `workflows/` - Multi-agent workflow definitions
- `prompts/` - Reusable prompt library
- `configs/` - Team, sandbox, and personality configurations
- `examples/` - Example projects

## Conventions

- Skill directories follow: `skill.json` + `instructions.md` + optional `resources/` and `scripts/`
- Automation files are JSON with cron `schedule`, `instructions`, `skills`, and `reviewRequired` fields
- Workflow files define `agents[]` with `branch`, `tasks`, `skills`, and `dependencies`
- All configs use JSON with `version` field for tracking

## Key Commands (Codex CLI)

```bash
# Install CLI
npm install -g @openai/codex

# Run with approval modes
codex                          # suggest mode (default, safest)
codex --approval-mode auto-edit  # auto-edit files, ask for shell
codex --approval-mode full-auto  # fully autonomous

# Use specific model
codex --model o4-mini
codex --model codex-1
```

## Environment

- Node.js v18+
- Set `OPENAI_API_KEY` for CLI usage
- Skills requiring external APIs: set `LINEAR_API_KEY`, `FIGMA_API_TOKEN` as env vars
