# Contributing to everything-codex

Thank you for improving this template library. Contributions must be useful without claiming unsupported Codex behavior.

## Contribution principles

1. **Templates are templates.** Unless verified against current official documentation, do not describe a JSON file, folder, command, or metadata field as automatically loaded or executed by Codex.
2. **Be explicit.** State a template’s purpose, prerequisites, inputs, permissions, review point, output, and failure behavior.
3. **Use least privilege.** Default external writes, production actions, network access, and scheduled work to review/approval.
4. **Protect secrets.** Never commit credentials, customer data, real URLs containing tokens, or unredacted logs.
5. **Avoid stale product claims.** Do not pin model names, pricing, plan availability, or competitor matrices unless an official source is cited and a review date is included.

## Asset formats in this repository

These formats are repository conventions, not necessarily Codex product schemas:

- `skills/<category>/<name>/instructions.md`: reusable task procedure.
- `skills/<category>/<name>/skill.json`: local metadata for organizing a template.
- `automations/*.json`: scheduling and review brief.
- `workflows/<name>/workflow.json`: parallel-work planning document.
- `configs/*.json`: conceptual configuration example.
- `prompts/*.md`: copy-ready prompt collection.

If a contribution targets a real Codex client configuration, link the official documentation that defines the exact format.

## Add a Skill template

Create `skills/<category>/<skill-name>/` with:

```text
skill-name/
├── skill.json
└── instructions.md
```

`instructions.md` should include:

```md
# Skill name

## Use when
Describe the triggering situation.

## Prerequisites
- Required local tools or approved integrations
- Required access, if any

## Procedure
1. Establish scope and success criteria.
2. Inspect the relevant context.
3. Make or propose the minimum necessary change.
4. Run task-appropriate validation.
5. Report evidence, limitations, and next steps.

## Permissions and safety
State whether file writes, shell commands, network access, MCP, or external updates are needed.

## Expected output
Describe the final report or artifact.
```

Keep `skill.json` metadata descriptive and secret-free.

## Add an automation brief

An automation must specify:

- purpose and trigger/schedule;
- time zone and owner;
- input sources and trust boundaries;
- permissions required;
- expected output/destination;
- error and retry behavior;
- a review gate before any merge, deployment, ticket mutation, or external notification.

Favor read-only summaries before proposing autonomous changes.

## Add a workflow plan

Define a clear integration owner, isolated work boundaries, and dependencies. Parallel agents should not modify the same files without an explicit coordination plan. Every workflow needs a final validation and human-review step.

## Documentation changes

- Use relative links for repository files and official links for Codex behavior.
- Check every documented path and command before submitting.
- Keep platform guidance client-neutral unless it has a cited, current source.
- Update `CHANGELOG.md` when an asset or material guidance changes.

## Submission checklist

- [ ] I have not included secrets or sensitive data.
- [ ] The asset has a clear scope and expected output.
- [ ] Permissions and review requirements are stated.
- [ ] Product-specific statements link to current official documentation, where needed.
- [ ] I have checked referenced paths and JSON syntax.
- [ ] I updated the changelog when appropriate.

## Pull requests

Use a descriptive title and explain:

- What changed and which problem it solves.
- How the template was reviewed or exercised.
- Any external tools, permissions, or environment assumptions.
- Any follow-up or compatibility risk.

See the [official Codex documentation](https://developers.openai.com/codex) for the current product setup and capability details.
