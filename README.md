# Everything Codex

**The complete collection of Codex configurations, skills, automations, and workflows from real-world production use.**

Production-ready skills, automations, multi-agent workflows, and best practices evolved from intensive daily development with OpenAI's Codex. Unlock the full potential of Codex with battle-tested patterns.

---

## The Guides

This repo is the raw code only. For comprehensive guides, see:

### **[Codex Documentation](https://developers.openai.com/codex)**

The foundation - what each config type does, how to structure your setup, multi-agent orchestration, and the philosophy behind these configs.

---

## What is Codex?

**Codex is OpenAI's powerful coding agent that changes how software gets built.**

From pairing with a single coding agent on targeted edits to supervising coordinated teams of agents across the full lifecycle of designing, building, shipping, and maintaining software.

### Key Capabilities

- **Multi-Agent Orchestration** - Run multiple agents in parallel on different tasks
- **Long-Running Tasks** - Agents can work for hours, days, or weeks
- **Skills System** - Extend Codex with custom workflows and tool integrations
- **Automations** - Background tasks that run on schedules
- **Worktrees** - Multiple agents work on same repo without conflicts
- **Full Lifecycle** - Design, build, ship, and maintain software
- **Computer Control** - Codex can operate your computer alongside you

---

## What's Inside

This repo is organized for **Codex** - install components directly or copy manually.

```
everything-codex/
├── skills/                  # Codex Skills (extend capabilities)
│   ├── development/
│   │   ├── code-review-skill/
│   │   ├── tdd-workflow-skill/
│   │   ├── debugging-skill/
│   │   └── refactoring-skill/
│   ├── deployment/
│   │   ├── cloudflare-deploy-skill/
│   │   ├── vercel-deploy-skill/
│   │   ├── netlify-deploy-skill/
│   │   └── docker-deploy-skill/
│   ├── design/
│   │   ├── figma-to-code-skill/
│   │   ├── image-generation-skill/
│   │   └── ui-mockup-skill/
│   ├── project-management/
│   │   ├── linear-integration-skill/
│   │   ├── github-pr-skill/
│   │   └── issue-triage-skill/
│   └── documentation/
│       ├── api-docs-skill/
│       ├── readme-generator-skill/
│       └── changelog-skill/
│
├── automations/             # Background automations
│   ├── daily-triage.json
│   ├── ci-failure-summary.json
│   ├── release-brief.json
│   ├── bug-detection.json
│   └── dependency-updates.json
│
├── workflows/               # Multi-agent workflows
│   ├── feature-development/
│   ├── bug-fix-workflow/
│   ├── refactoring-workflow/
│   └── deployment-workflow/
│
├── prompts/                 # Reusable prompts
│   ├── code-review-prompts.md
│   ├── architecture-prompts.md
│   ├── testing-prompts.md
│   └── debugging-prompts.md
│
├── configs/                 # Codex configurations
│   ├── team-config.json
│   ├── sandbox-rules.json
│   └── personality-settings.json
│
└── examples/               # Example projects
    ├── web-app-example/
    ├── api-service-example/
    └── game-development-example/
```

---

## Key Concepts

### Skills

Skills bundle instructions, resources, and scripts so Codex can reliably connect to tools, run workflows, and complete tasks according to your preferences.

**Example Skill Structure:**
```
my-skill/
├── skill.json           # Skill metadata and configuration
├── instructions.md      # Detailed instructions for Codex
├── resources/          # Supporting files (templates, configs)
└── scripts/            # Executable scripts
```

**Skill Types:**
- **Development Skills** - Code review, testing, debugging
- **Deployment Skills** - Deploy to cloud platforms
- **Design Skills** - Figma integration, image generation
- **Project Management** - Linear, GitHub, issue triage
- **Documentation Skills** - API docs, README generation

### Automations

Automations let Codex work in the background on an automatic schedule. When an Automation finishes, results land in a review queue.

**Example Automation:**
```json
{
  "name": "Daily Issue Triage",
  "schedule": "0 9 * * *",
  "instructions": "Review all new GitHub issues, categorize by priority, assign labels, and suggest assignees",
  "skills": ["github-pr-skill", "issue-triage-skill"],
  "reviewRequired": true
}
```

**Common Automations:**
- Daily issue triage
- CI failure summaries
- Release brief generation
- Bug detection scans
- Dependency update checks
- Security vulnerability scans

### Multi-Agent Workflows

Codex can run multiple agents in parallel, each working on different tasks without conflicts using worktrees.

**Example Workflow:**
```
Agent 1: Implement user authentication (feature/auth branch)
Agent 2: Add payment integration (feature/payments branch)
Agent 3: Refactor database layer (refactor/db branch)

All working simultaneously on the same repo!
```

### Worktrees

Each agent works on an isolated copy of your code, allowing exploration of different paths without impacting your codebase.

**Benefits:**
- No git conflicts between agents
- Parallel development
- Easy to review changes per agent
- Can check out changes locally anytime

### Personalities

Choose between two interaction styles:
- **Terse/Pragmatic** - Blunt, execution-focused
- **Conversational/Empathetic** - More communicative, engaging

Use `/personality` command to switch.

---

## Installation

### Prerequisites

- Codex app installed (macOS or Windows)
- ChatGPT Plus, Pro, Business, Enterprise, or Edu subscription
- Git installed
- Node.js (for some skills)

### Option 1: Clone Repository

```bash
# Clone the repository
git clone https://github.com/iamaanahmad/everything-codex.git

# Navigate to directory
cd everything-codex
```

### Option 2: Install Skills

```bash
# Copy skills to Codex skills directory
cp -r skills/* ~/.codex/skills/

# Or project-specific
cp -r skills/* .codex/skills/
```

### Option 3: Set Up Automations

```bash
# Copy automations to Codex automations directory
cp automations/* ~/.codex/automations/
```

---

## Usage Examples

### Using Skills

```
User: Use the code-review-skill to review this PR

Codex: [Activates code-review-skill]

Running comprehensive code review...

Security Analysis:
✓ No hardcoded secrets
✓ Input validation present
✓ SQL injection prevention

Performance Analysis:
✓ Efficient algorithms
⚠ Consider caching for /api/users endpoint

Code Quality:
✓ Well-structured functions
✓ Good test coverage (87%)
✓ Clear naming conventions

Recommendation: APPROVE with suggestion to add caching
```

### Multi-Agent Workflow

```
User: I need to add user authentication, payment integration, and refactor the database layer

Codex: I'll create three parallel agents for this:

Agent 1 (Thread 1): Implementing user authentication
- Creating feature/auth branch
- Setting up JWT authentication
- Adding login/register endpoints

Agent 2 (Thread 2): Adding payment integration
- Creating feature/payments branch
- Integrating Stripe API
- Building payment flow

Agent 3 (Thread 3): Refactoring database layer
- Creating refactor/db branch
- Optimizing queries
- Adding connection pooling

All agents working in parallel. You can switch between threads to review progress.
```

### Using Automations

```
User: Set up daily issue triage automation

Codex: Creating automation...

Automation: Daily Issue Triage
Schedule: Every day at 9 AM
Tasks:
- Review new GitHub issues
- Categorize by priority (P0, P1, P2, P3)
- Assign appropriate labels
- Suggest assignees based on expertise
- Flag security issues

Results will appear in your review queue each morning.

Automation created! ✓
```

### Deploying with Skills

```
User: Deploy this web app to Vercel

Codex: [Activates vercel-deploy-skill]

Deployment Process:
1. Building production bundle... ✓
2. Running tests... ✓
3. Optimizing assets... ✓
4. Deploying to Vercel... ✓

Deployment successful!
URL: https://your-app.vercel.app
Preview: https://your-app-git-main.vercel.app

Would you like me to set up automatic deployments for future commits?
```

---

## Key Features

### 🤖 Skills Library (50+ Skills)

Comprehensive skills for:
- Development workflows (code review, TDD, debugging)
- Cloud deployment (Vercel, Netlify, Cloudflare, Render)
- Design integration (Figma, image generation)
- Project management (Linear, GitHub, Jira)
- Documentation (API docs, README, changelog)
- Testing (unit, integration, E2E)
- Security (vulnerability scanning, audit)
- Performance (optimization, profiling)

### ⚡ Automations (20+ Templates)

Background tasks for:
- Daily issue triage
- CI/CD failure summaries
- Release brief generation
- Bug detection and reporting
- Dependency updates
- Security scans
- Performance monitoring
- Documentation updates

### 🔄 Multi-Agent Workflows

Orchestrate multiple agents:
- Parallel feature development
- Simultaneous bug fixes
- Concurrent refactoring
- Independent testing
- Isolated experimentation

### 🎯 Prompts Library (100+ Prompts)

Reusable prompts for:
- Code review
- Architecture design
- Testing strategies
- Debugging approaches
- Refactoring patterns
- Documentation generation
- Performance optimization
- Security auditing

### 🔧 Configurations

Team and project configs:
- Sandbox security rules
- Personality settings
- Skill permissions
- Automation schedules
- Worktree management

---

## Skill Examples

### Code Review Skill

**Location:** `skills/development/code-review-skill/`

**Purpose:** Comprehensive code review with security, performance, and quality checks

**Usage:**
```
Use code-review-skill to review PR #123
```

**Features:**
- Security vulnerability detection
- Performance analysis
- Code quality assessment
- Test coverage verification
- Best practices enforcement

### Figma to Code Skill

**Location:** `skills/design/figma-to-code-skill/`

**Purpose:** Convert Figma designs to production-ready code

**Usage:**
```
Use figma-to-code-skill to implement this design: [Figma URL]
```

**Features:**
- Fetches design context and assets
- Generates pixel-perfect UI code
- Responsive design implementation
- Component extraction
- Style system integration

### Vercel Deploy Skill

**Location:** `skills/deployment/vercel-deploy-skill/`

**Purpose:** Deploy web applications to Vercel

**Usage:**
```
Use vercel-deploy-skill to deploy this app
```

**Features:**
- Automatic build optimization
- Environment variable management
- Preview deployments
- Production deployments
- Rollback support

### Linear Integration Skill

**Location:** `skills/project-management/linear-integration-skill/`

**Purpose:** Manage projects in Linear

**Usage:**
```
Use linear-integration-skill to triage bugs
```

**Features:**
- Issue creation and updates
- Sprint planning
- Team workload management
- Priority assignment
- Status tracking

---

## Automation Examples

### Daily Issue Triage

**File:** `automations/daily-triage.json`

**Schedule:** Every day at 9 AM

**Tasks:**
- Review new GitHub issues
- Categorize by priority
- Assign labels
- Suggest assignees
- Flag security issues

### CI Failure Summary

**File:** `automations/ci-failure-summary.json`

**Schedule:** Every 6 hours

**Tasks:**
- Check CI/CD pipeline status
- Summarize failures
- Identify patterns
- Suggest fixes
- Notify team

### Release Brief

**File:** `automations/release-brief.json`

**Schedule:** Daily at 5 PM

**Tasks:**
- Collect merged PRs
- Summarize changes
- Generate changelog
- Identify breaking changes
- Create release notes

---

## Multi-Agent Workflow Examples

### Feature Development Workflow

**Scenario:** Building a complete feature with multiple components

**Agents:**
1. **Backend Agent** - API endpoints and business logic
2. **Frontend Agent** - UI components and integration
3. **Testing Agent** - Comprehensive test suite
4. **Documentation Agent** - API docs and README updates

**Workflow:**
```
User: Build a user profile feature with avatar upload

Codex: Creating 4-agent workflow...

Thread 1 (Backend): 
- Creating /api/profile endpoints
- Adding avatar upload to S3
- Implementing profile update logic

Thread 2 (Frontend):
- Building ProfilePage component
- Creating AvatarUpload component
- Integrating with backend API

Thread 3 (Testing):
- Writing unit tests for API
- Creating integration tests
- Adding E2E tests for profile flow

Thread 4 (Documentation):
- Documenting API endpoints
- Updating README
- Creating usage examples

All agents working in parallel. Review progress in each thread.
```

### Bug Fix Workflow

**Scenario:** Fixing a critical bug across multiple files

**Agents:**
1. **Investigation Agent** - Root cause analysis
2. **Fix Agent** - Implement the fix
3. **Testing Agent** - Verify fix and prevent regression
4. **Documentation Agent** - Update docs if needed

### Refactoring Workflow

**Scenario:** Large-scale refactoring

**Agents:**
1. **Analysis Agent** - Identify refactoring opportunities
2. **Refactor Agent 1** - Refactor module A
3. **Refactor Agent 2** - Refactor module B
4. **Testing Agent** - Ensure no regressions

---

## Prompts Library

### Code Review Prompts

```markdown
# Security-Focused Review
Review this code for security vulnerabilities:
- Check for hardcoded secrets
- Verify input validation
- Look for SQL injection risks
- Check authentication/authorization
- Verify error handling doesn't leak info

# Performance Review
Analyze this code for performance issues:
- Check algorithm complexity
- Look for N+1 query problems
- Identify unnecessary re-renders
- Check for memory leaks
- Suggest optimization opportunities

# Architecture Review
Review this code from an architectural perspective:
- Check separation of concerns
- Verify SOLID principles
- Look for code smells
- Suggest design patterns
- Identify technical debt
```

### Testing Prompts

```markdown
# TDD Implementation
Implement this feature using TDD:
1. Write failing tests first (RED)
2. Implement minimal code to pass (GREEN)
3. Refactor while keeping tests green (REFACTOR)
4. Ensure 80%+ coverage

# E2E Test Generation
Create E2E tests for this user flow:
- Use Playwright
- Test happy path
- Test error cases
- Test edge cases
- Add visual regression tests

# Test Coverage Analysis
Analyze test coverage and suggest improvements:
- Identify untested code paths
- Suggest missing test cases
- Check for edge cases
- Verify error handling tests
```

### Debugging Prompts

```markdown
# Systematic Debugging
Debug this issue systematically:
1. Reproduce the issue
2. Gather information (logs, metrics)
3. Form hypothesis
4. Test hypothesis
5. Implement fix
6. Verify fix
7. Add regression test

# Performance Debugging
Investigate this performance issue:
- Profile the code
- Identify bottlenecks
- Analyze database queries
- Check network requests
- Suggest optimizations
```

---

## Configuration

### Team Config

**File:** `configs/team-config.json`

```json
{
  "team": "engineering",
  "skills": {
    "enabled": [
      "code-review-skill",
      "tdd-workflow-skill",
      "vercel-deploy-skill",
      "linear-integration-skill"
    ],
    "autoActivate": true
  },
  "automations": {
    "enabled": true,
    "reviewRequired": true
  },
  "sandbox": {
    "allowedCommands": [
      "npm",
      "git",
      "node"
    ],
    "networkAccess": "ask"
  },
  "personality": "terse"
}
```

### Sandbox Rules

**File:** `configs/sandbox-rules.json`

```json
{
  "rules": [
    {
      "command": "npm install",
      "permission": "allow",
      "reason": "Safe package installation"
    },
    {
      "command": "git push",
      "permission": "ask",
      "reason": "Requires confirmation before pushing"
    },
    {
      "command": "rm -rf",
      "permission": "deny",
      "reason": "Dangerous deletion command"
    },
    {
      "pattern": "curl *",
      "permission": "ask",
      "reason": "Network access requires approval"
    }
  ],
  "defaultPermission": "ask"
}
```

---

## Best Practices

### Skill Development
- ✅ Keep skills focused on single responsibility
- ✅ Provide clear instructions in instructions.md
- ✅ Include examples and templates
- ✅ Test skills thoroughly before sharing
- ✅ Document prerequisites and dependencies
- ✅ Version your skills properly

### Multi-Agent Orchestration
- ✅ Use worktrees for parallel work
- ✅ Keep agents focused on specific tasks
- ✅ Review each agent's progress regularly
- ✅ Merge agents' work incrementally
- ✅ Communicate dependencies between agents
- ✅ Use descriptive thread names

### Automation Setup
- ✅ Start with simple automations
- ✅ Always require review for critical tasks
- ✅ Set appropriate schedules
- ✅ Monitor automation results
- ✅ Adjust based on feedback
- ✅ Document automation purposes

### Security
- ✅ Configure sandbox rules appropriately
- ✅ Review elevated permission requests
- ✅ Use environment variables for secrets
- ✅ Enable security scanning skills
- ✅ Regular security audits
- ✅ Keep dependencies updated

---

## Comparison with Claude Code and Kiro

| Feature | Claude Code | Kiro | Codex |
|---------|-------------|------|-------|
| Multi-Agent | No | Yes (sub-agents) | Yes (parallel threads) |
| Skills/Powers | Skills | Powers | Skills |
| Automations | Hooks | Hooks | Automations |
| Worktrees | No | No | Yes |
| Long-Running | Limited | Yes | Yes (hours/days/weeks) |
| Computer Control | No | Limited | Yes |
| Personalities | No | No | Yes |
| Cloud Execution | No | No | Yes |

**Codex Advantages:**
- Native multi-agent orchestration
- Worktrees for conflict-free parallel work
- Background automations with scheduling
- Computer control beyond code
- Skills work across app, CLI, and IDE

---

## Contributing

Contributions are welcome! If you have:
- New skills for common workflows
- Improved automation templates
- Better multi-agent workflows
- Useful prompts and patterns
- Configuration improvements

Please submit a pull request. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

---

## Resources

- **Codex App:** [Download](https://openai.com/codex)
- **Codex Documentation:** [Official Docs](https://developers.openai.com/codex)
- **Skills Repository:** [Open Source Skills](https://github.com/openai/codex-skills)
- **Community:** [Codex Community](https://community.openai.com/c/codex)
- **Inspired by:** [everything-claude-code](https://github.com/affaan-m/everything-claude-code)

---

## License

MIT - Use freely, modify as needed, contribute back if you can.

---

**Transform your development workflow with AI-powered multi-agent orchestration. Start with everything-codex and build something extraordinary.**

Star this repo if it helps. Customize for your needs. Build something great.
