# Contributing to everything-codex

Thank you for your interest in contributing! This guide will help you get started.

## How to Contribute

### 1. Skills

#### Creating a New Skill

Skills extend Codex capabilities. To create a new skill:

```bash
# Create skill directory
mkdir -p skills/category/your-skill-name

# Create required files
touch skills/category/your-skill-name/skill.json
touch skills/category/your-skill-name/instructions.md
```

#### Skill Structure

**skill.json** - Metadata and configuration:
```json
{
  "name": "your-skill-name",
  "version": "1.0.0",
  "description": "Brief description",
  "author": "your-name",
  "category": "development|deployment|design|project-management|documentation",
  "tags": ["tag1", "tag2"],
  "permissions": {
    "fileSystem": "read|write|none",
    "network": true|false,
    "shell": true|false
  },
  "dependencies": ["dependency1", "dependency2"],
  "configuration": {
    "key": "value"
  }
}
```

**instructions.md** - Detailed instructions for Codex:
```markdown
# Skill Name

## Purpose
What this skill does and when to use it.

## Prerequisites
- Required tools
- API keys
- Dependencies

## Instructions
Step-by-step instructions for Codex to follow.

## Examples
Example usage scenarios.

## Best Practices
Tips for optimal usage.
```

#### Skill Categories

- **development**: Code review, testing, debugging, refactoring
- **deployment**: Cloud deployments, CI/CD
- **design**: Figma integration, UI generation
- **project-management**: Linear, GitHub, Jira integration
- **documentation**: API docs, README generation

#### Skill Guidelines

- ✅ Single responsibility - one skill, one purpose
- ✅ Clear instructions - Codex should understand exactly what to do
- ✅ Include examples - show expected input/output
- ✅ Document prerequisites - API keys, tools, dependencies
- ✅ Test thoroughly - verify skill works as expected
- ✅ Version properly - use semantic versioning

### 2. Automations

#### Creating an Automation

Automations run on schedules in the background:

```bash
# Create automation file
touch automations/your-automation.json
```

#### Automation Structure

```json
{
  "name": "Automation Name",
  "version": "1.0.0",
  "description": "What this automation does",
  "schedule": "0 9 * * *",
  "timezone": "UTC",
  "enabled": true,
  "instructions": "Detailed instructions for what to do",
  "skills": ["skill1", "skill2"],
  "reviewRequired": true,
  "notifications": {
    "onComplete": true,
    "onError": true,
    "channels": ["slack", "email"]
  },
  "output": {
    "format": "markdown",
    "destination": "review-queue"
  }
}
```

#### Schedule Format (Cron)

```
* * * * *
│ │ │ │ │
│ │ │ │ └─ Day of week (0-7, 0 and 7 are Sunday)
│ │ │ └─── Month (1-12)
│ │ └───── Day of month (1-31)
│ └─────── Hour (0-23)
└───────── Minute (0-59)
```

Examples:
- `0 9 * * *` - Every day at 9 AM
- `0 */6 * * *` - Every 6 hours
- `0 0 * * 1` - Every Monday at midnight
- `0 17 * * 1-5` - Weekdays at 5 PM

#### Automation Guidelines

- ✅ Clear purpose - what problem does it solve?
- ✅ Appropriate schedule - not too frequent
- ✅ Review required - especially for critical tasks
- ✅ Notifications configured - keep team informed
- ✅ Error handling - what happens if it fails?

### 3. Workflows

#### Creating a Multi-Agent Workflow

Workflows orchestrate multiple agents:

```bash
# Create workflow directory
mkdir -p workflows/your-workflow

# Create workflow file
touch workflows/your-workflow/workflow.json
```

#### Workflow Structure

```json
{
  "name": "Workflow Name",
  "version": "1.0.0",
  "description": "What this workflow accomplishes",
  "agents": [
    {
      "id": "agent-1",
      "name": "Agent Name",
      "role": "What this agent does",
      "branch": "branch-name",
      "tasks": ["task1", "task2"],
      "skills": ["skill1"],
      "dependencies": []
    }
  ],
  "mergeStrategy": "sequential|parallel",
  "reviewRequired": true
}
```

#### Workflow Guidelines

- ✅ Clear agent roles - each agent has specific responsibility
- ✅ Proper dependencies - agents run in correct order
- ✅ Isolated branches - use worktrees for parallel work
- ✅ Review checkpoints - review before merging
- ✅ Error handling - what if an agent fails?

### 4. Prompts

#### Creating Prompts

Prompts are reusable templates:

```bash
# Create prompt file
touch prompts/your-prompts.md
```

#### Prompt Structure

```markdown
# Prompt Category

## Specific Prompt Name

\`\`\`
Prompt template with {{placeholders}}

Instructions:
- Step 1
- Step 2

Expected output:
- Output format
\`\`\`

## Another Prompt

...
```

#### Prompt Guidelines

- ✅ Clear instructions - no ambiguity
- ✅ Use placeholders - {{variable}} for customization
- ✅ Include examples - show expected usage
- ✅ Specify output format - what should result look like
- ✅ Cover edge cases - handle various scenarios

### 5. Configurations

#### Contributing Configurations

Share useful configurations:

```bash
# Add to configs directory
touch configs/your-config.json
```

#### Configuration Guidelines

- ✅ Well-documented - explain each setting
- ✅ Sensible defaults - work out of the box
- ✅ Customizable - easy to adapt
- ✅ Secure - no hardcoded secrets
- ✅ Validated - test before sharing

## Contribution Process

### 1. Fork the Repository

```bash
# Fork on GitHub, then clone
git clone https://github.com/your-username/everything-codex.git
cd everything-codex
```

### 2. Create a Branch

```bash
# Create feature branch
git checkout -b feature/your-feature-name

# Or for bug fixes
git checkout -b bugfix/issue-description
```

### 3. Make Changes

- Add your skill/automation/workflow/prompt
- Follow the guidelines above
- Test thoroughly
- Update documentation

### 4. Test Your Contribution

#### Test Skills
```bash
# Test skill locally
codex skills test your-skill-name

# Verify skill works as expected
```

#### Test Automations
```bash
# Validate automation
codex automations validate your-automation.json

# Test run (if possible)
codex automations test your-automation
```

#### Test Workflows
```bash
# Validate workflow
codex workflows validate your-workflow.json
```

### 5. Update Documentation

- Add entry to README.md
- Update CHANGELOG.md
- Add examples if applicable
- Update INSTALL.md if needed

### 6. Commit Changes

```bash
# Stage changes
git add .

# Commit with descriptive message
git commit -m "Add: Your feature description"

# Use conventional commits
# feat: New feature
# fix: Bug fix
# docs: Documentation
# refactor: Code refactoring
# test: Tests
# chore: Maintenance
```

### 7. Push and Create PR

```bash
# Push to your fork
git push origin feature/your-feature-name

# Create pull request on GitHub
```

### 8. PR Guidelines

**PR Title**: Clear and descriptive
```
Add: Linear integration skill
Fix: Bug in code review skill
Docs: Update installation guide
```

**PR Description**: Include:
- What does this add/fix?
- Why is it needed?
- How was it tested?
- Any breaking changes?
- Screenshots (if applicable)

**PR Template**:
```markdown
## Description
Brief description of changes

## Type of Change
- [ ] New skill
- [ ] New automation
- [ ] New workflow
- [ ] New prompts
- [ ] Bug fix
- [ ] Documentation
- [ ] Configuration

## Testing
How was this tested?

## Checklist
- [ ] Follows contribution guidelines
- [ ] Tested thoroughly
- [ ] Documentation updated
- [ ] CHANGELOG.md updated
- [ ] No breaking changes (or documented)
```

## Code of Conduct

### Be Respectful
- Treat everyone with respect
- Welcome newcomers
- Be patient with questions
- Provide constructive feedback

### Be Collaborative
- Share knowledge
- Help others
- Review PRs thoughtfully
- Discuss ideas openly

### Be Professional
- Keep discussions on-topic
- Avoid personal attacks
- Respect different opinions
- Focus on the code, not the person

## Quality Standards

### Skills
- ✅ Clear, focused purpose
- ✅ Comprehensive instructions
- ✅ Working examples
- ✅ Proper error handling
- ✅ Security considerations

### Automations
- ✅ Appropriate schedule
- ✅ Clear instructions
- ✅ Review requirements
- ✅ Notification setup
- ✅ Error handling

### Workflows
- ✅ Clear agent roles
- ✅ Proper dependencies
- ✅ Merge strategy defined
- ✅ Review checkpoints
- ✅ Error handling

### Prompts
- ✅ Clear instructions
- ✅ Placeholders for customization
- ✅ Examples included
- ✅ Output format specified
- ✅ Edge cases covered

### Documentation
- ✅ Clear and concise
- ✅ Examples included
- ✅ Up-to-date
- ✅ Properly formatted
- ✅ No typos

## Getting Help

### Questions?
- Open a GitHub Discussion
- Ask in community forums
- Check existing issues

### Found a Bug?
- Search existing issues first
- Create detailed bug report
- Include reproduction steps
- Provide environment details

### Feature Request?
- Check if already requested
- Explain use case
- Describe expected behavior
- Discuss implementation approach

## Recognition

Contributors will be:
- Listed in README.md
- Credited in CHANGELOG.md
- Mentioned in release notes
- Appreciated by the community!

## License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

**Thank you for contributing to everything-codex!**

Your contributions help developers worldwide build better software with AI assistance.
