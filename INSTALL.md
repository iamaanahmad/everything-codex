# Installation Guide

Complete installation guide for everything-codex.

## Prerequisites

### For Codex Cloud
- ChatGPT Plus, Pro, Business, Enterprise, or Edu subscription
- Git installed

### For Codex CLI
- Node.js v22+ (recommended) or v18+
- OpenAI API key (`OPENAI_API_KEY`)
- Git installed

### Optional
- **Python**: v3.8+ (for Python skills)
- **Docker**: For containerized deployments
- **Vercel CLI**: For Vercel deployments
- **Linear API Key**: For Linear integration

## Installation Methods

### Method 1: Install Codex CLI (Recommended for local use)

```bash
# Install globally
npm install -g @openai/codex

# Set your API key
export OPENAI_API_KEY="your-key-here"

# Run in your project (suggest mode - safest default)
codex

# Or with more autonomy
codex --approval-mode auto-edit
codex --approval-mode full-auto

# Use a specific model
codex --model o4-mini
codex --model codex-1
```

### Method 2: Clone Repository

```bash
git clone https://github.com/iamaanahmad/everything-codex.git
cd everything-codex
```

### Method 2: Install Skills Globally

Install skills to your global Codex directory (available in all projects):

```bash
# Create global skills directory if it doesn't exist
mkdir -p ~/.codex/skills

# Copy skills
cp -r everything-codex/skills/* ~/.codex/skills/

# Verify installation
ls ~/.codex/skills
```

### Method 3: Install Skills Per-Project

Install skills for a specific project:

```bash
# Navigate to your project
cd /path/to/your/project

# Create project skills directory
mkdir -p .codex/skills

# Copy skills
cp -r /path/to/everything-codex/skills/* .codex/skills/

# Verify installation
ls .codex/skills
```

### Method 4: Install Automations

```bash
# Create automations directory
mkdir -p ~/.codex/automations

# Copy automations
cp everything-codex/automations/* ~/.codex/automations/

# Verify installation
ls ~/.codex/automations
```

### Method 5: Install Prompts Library

```bash
# Create prompts directory
mkdir -p ~/.codex/prompts

# Copy prompts
cp everything-codex/prompts/* ~/.codex/prompts/

# Verify installation
ls ~/.codex/prompts
```

## Setting Up `codex.md` (Project Memory)

The `codex.md` file in your project root gives Codex persistent context about your project — like `CLAUDE.md` for Claude Code.

```bash
# Copy the template from this repo
cp codex.md /path/to/your/project/codex.md

# Edit for your project
nano /path/to/your/project/codex.md
```

Include:
- Project overview and structure
- Key commands (build, test, lint)
- Coding conventions
- Environment variable names
- Architecture decisions

## Configuration

### 1. Team Configuration

Copy and customize team configuration:

```bash
# Copy team config
cp everything-codex/configs/team-config.json ~/.codex/team-config.json

# Edit configuration
nano ~/.codex/team-config.json
```

Update the following:
- Team name
- Enabled skills
- Automation settings
- Sandbox rules
- Personality preference

### 2. Sandbox Rules

Configure security rules:

```bash
# Copy sandbox rules
cp everything-codex/configs/sandbox-rules.json ~/.codex/sandbox-rules.json

# Edit rules
nano ~/.codex/sandbox-rules.json
```

Customize:
- Allowed commands
- Network access rules
- File system permissions
- Default permission level

### 3. Personality Settings

Choose interaction style:

```bash
# Copy personality settings
cp everything-codex/configs/personality-settings.json ~/.codex/personality-settings.json

# Edit settings
nano ~/.codex/personality-settings.json
```

Choose between:
- **Terse**: Minimal, execution-focused
- **Conversational**: More communicative, engaging

## Skill Configuration

### Configure Individual Skills

Each skill may require configuration:

#### Linear Integration Skill

```bash
# Set Linear API key
export LINEAR_API_KEY="your-api-key"

# Or add to .env
echo "LINEAR_API_KEY=your-api-key" >> ~/.codex/.env
```

#### Figma to Code Skill

```bash
# Set Figma API token
export FIGMA_API_TOKEN="your-token"

# Or add to .env
echo "FIGMA_API_TOKEN=your-token" >> ~/.codex/.env
```

#### Vercel Deploy Skill

```bash
# Install Vercel CLI
npm install -g vercel

# Login to Vercel
vercel login
```

## Automation Setup

### Enable Automations

1. Open Codex app
2. Go to Settings → Automations
3. Enable automations
4. Configure review requirements
5. Set notification preferences

### Configure Schedules

Edit automation files to customize schedules:

```bash
# Edit daily triage schedule
nano ~/.codex/automations/daily-triage.json
```

Change the `schedule` field (cron format):
```json
{
  "schedule": "0 9 * * *",  // 9 AM daily
  "timezone": "America/New_York"
}
```

## Approval Modes (Codex CLI)

Control how much autonomy Codex has:

| Mode | File Edits | Shell Commands | Best For |
|------|-----------|----------------|----------|
| `suggest` | Asks | Asks | Default, safest |
| `auto-edit` | Auto | Asks | Trusted projects |
| `full-auto` | Auto | Auto | CI/CD, automation |

```bash
codex                                    # suggest (default)
codex --approval-mode auto-edit          # auto file edits
codex --approval-mode full-auto          # fully autonomous
```

## MCP Integration (Codex CLI)

Connect external tools via Model Context Protocol:

```bash
# Add MCP server to Codex CLI config (~/.codex/config.json)
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": { "GITHUB_TOKEN": "<your-token>" }
    }
  }
}
```

## Verification

### Verify CLI Installation

```bash
# Check version
codex --version

# Run with a simple task
codex "list files in this directory"
```

### Verify Skills Installation

```bash
# List installed skills
codex skills list

# Test a skill
codex skills test code-review-skill
```

### Verify Automations

```bash
# List automations
codex automations list

# Check automation status
codex automations status
```

### Test Configuration

```bash
# Validate team config
codex config validate ~/.codex/team-config.json

# Validate sandbox rules
codex config validate ~/.codex/sandbox-rules.json
```

## Usage

### Using Skills

In Codex chat:
```
Use code-review-skill to review this PR
```

Or activate automatically:
```
Review this code for security issues
```
(If autoActivate is enabled, Codex will use appropriate skills)

### Using Automations

Automations run automatically on schedule. View results:
```
Show automation results
```

Or in Codex app:
- Go to Automations tab
- View review queue
- Approve/reject automation results

### Using Prompts

Reference prompts in your conversations:
```
Use the security-focused review prompt from the prompts library
```

Or copy-paste prompts directly from `prompts/` directory.

## Troubleshooting

### Skills Not Found

```bash
# Check skills directory
ls ~/.codex/skills

# Verify permissions
chmod -R 755 ~/.codex/skills

# Restart Codex app
```

### Automations Not Running

```bash
# Check automation status
codex automations status

# View automation logs
codex automations logs

# Verify schedule format
codex automations validate
```

### Permission Errors

```bash
# Fix permissions
chmod -R 755 ~/.codex

# Check sandbox rules
cat ~/.codex/sandbox-rules.json
```

### API Key Issues

```bash
# Verify environment variables
env | grep API

# Check .env file
cat ~/.codex/.env

# Reload environment
source ~/.codex/.env
```

## Updating

### Update Skills

```bash
# Pull latest changes
cd everything-codex
git pull

# Copy updated skills
cp -r skills/* ~/.codex/skills/
```

### Update Automations

```bash
# Copy updated automations
cp automations/* ~/.codex/automations/

# Restart automations
codex automations restart
```

### Update Configuration

```bash
# Backup current config
cp ~/.codex/team-config.json ~/.codex/team-config.json.backup

# Copy new config
cp configs/team-config.json ~/.codex/team-config.json

# Merge your customizations
```

## Uninstallation

### Remove Skills

```bash
# Remove global skills
rm -rf ~/.codex/skills

# Remove project skills
rm -rf .codex/skills
```

### Remove Automations

```bash
# Remove automations
rm -rf ~/.codex/automations
```

### Remove Configuration

```bash
# Remove all Codex configuration
rm -rf ~/.codex
```

## Next Steps

1. **Explore Skills**: Try different skills in your projects
2. **Customize Automations**: Adjust schedules and notifications
3. **Create Workflows**: Set up multi-agent workflows
4. **Contribute**: Share your custom skills and automations

- **Codex CLI (open-source)**: [github.com/openai/codex](https://github.com/openai/codex)
- **Codex Documentation**: [platform.openai.com/docs/codex](https://platform.openai.com/docs/codex)
- **Community**: [community.openai.com](https://community.openai.com)
- **Original upstream repository**: [github.com/affaan-m/everything-claude-code](https://github.com/affaan-m/everything-claude-code)
