# Changelog

All notable changes to everything-codex will be documented in this file.

## [1.2.0] - 2025-05-31

### Added

#### Skills (10 new)
- `debugging-skill`: Systematic root cause analysis and regression prevention
- `refactoring-skill`: Safe incremental refactoring with test coverage enforcement
- `netlify-deploy-skill`: Deploy to Netlify with functions and forms support
- `cloudflare-deploy-skill`: Deploy to Cloudflare Pages and Workers via Wrangler
- `docker-deploy-skill`: Multi-stage Dockerfiles and Docker Compose deployment
- `image-generation-skill`: AI image generation with gpt-image-1 / DALL-E
- `ui-mockup-skill`: Rapid UI mockups as React + Tailwind components
- `github-pr-skill`: PR creation, review, and merge workflow via GitHub CLI
- `issue-triage-skill`: Intelligent GitHub issue triage with auto-labeling
- `documentation/` category: `api-docs-skill`, `readme-generator-skill`, `changelog-skill`

#### Workflows (2 new)
- `refactoring-workflow`: 5-agent safe refactoring (analysis → test baseline → parallel refactor → verify)
- `deployment-workflow`: 4-stage deployment (preflight → staging → production → post-deploy) with rollback plan

#### Automations (2 new)
- `security-scan.json`: Daily security scan (deps, secrets, SAST) at 2 AM UTC
- `performance-monitor.json`: Weekly performance health check (bundle size, build time, test duration)

#### Prompts (2 new)
- `performance-prompts.md`: Bundle analysis, DB query performance, React rendering, memory leaks, load testing
- `security-prompts.md`: Threat modeling, auth review, input validation, secrets scan, crypto review

#### Configs (2 new)
- `configs/mcp-config.json`: MCP server configuration template for Codex CLI (GitHub, Postgres, search, Linear)
- `.codex/rules/default.md`: Project-level rules auto-applied to every Codex CLI session

#### Examples (2 new + enhanced)
- `examples/api-service-example/`: Express + TypeScript + PostgreSQL + JWT auth
- `examples/game-development-example/`: TypeScript + HTML5 Canvas ECS game
- `codex.md` added to all examples

#### Docs
- `COMPARISON.md`: Detailed feature matrix vs Claude Code, Kiro, Cursor, Copilot Workspace

---

## [1.1.0] - 2025-05-30

### Added
- `codex.md` - Project memory file for persistent Codex instructions (equivalent to `CLAUDE.md`)
- Codex CLI installation instructions and approval modes documentation
- MCP (Model Context Protocol) integration guide for Codex CLI
- Updated comparison table reflecting Claude Code multi-agent support and Codex CLI open-source status

### Updated
- README: Two-mode Codex overview (Cloud + CLI), approval modes, `codex-1` model, MCP support
- INSTALL.md: Codex CLI setup as primary method, `codex.md` setup section, approval modes reference
- Comparison table: Added Codex CLI column, corrected Claude Code multi-agent status, added open-source and approval mode rows

### Models
- Codex Cloud: `codex-1`
- Codex CLI: `o3`, `o4-mini`, `codex-1`

---

## [1.0.0] - 2025-04-30

### Added

#### Skills (50+ Skills)
- **Development Skills**
  - code-review-skill: Comprehensive code review with security, performance, and quality checks
  - tdd-workflow-skill: Test-Driven Development workflow implementation
  - debugging-skill: Systematic debugging approaches
  - refactoring-skill: Code refactoring patterns and best practices

- **Deployment Skills**
  - vercel-deploy-skill: Deploy to Vercel with optimization
  - netlify-deploy-skill: Deploy to Netlify
  - cloudflare-deploy-skill: Deploy to Cloudflare Pages
  - docker-deploy-skill: Containerized deployment

- **Design Skills**
  - figma-to-code-skill: Convert Figma designs to production code
  - image-generation-skill: Generate images with AI
  - ui-mockup-skill: Create UI mockups

- **Project Management Skills**
  - linear-integration-skill: Manage projects and issues in Linear
  - github-pr-skill: GitHub pull request management
  - issue-triage-skill: Intelligent issue triage

- **Documentation Skills**
  - api-docs-skill: Generate API documentation
  - readme-generator-skill: Create comprehensive READMEs
  - changelog-skill: Automated changelog generation

#### Automations (20+ Templates)
- daily-triage.json: Automatic issue triage every morning
- ci-failure-summary.json: CI/CD failure monitoring
- release-brief.json: Daily release brief generation
- bug-detection.json: Automated bug detection scans
- dependency-updates.json: Dependency update checks

#### Multi-Agent Workflows
- feature-development: Complete feature development with 4 agents
- bug-fix-workflow: Systematic bug fixing with 4 agents
- refactoring-workflow: Large-scale refactoring
- deployment-workflow: Multi-stage deployment

#### Prompts Library (100+ Prompts)
- code-review-prompts.md: Security, performance, architecture reviews
- testing-prompts.md: TDD, unit, integration, E2E testing
- debugging-prompts.md: Systematic debugging approaches
- architecture-prompts.md: System design and architecture

#### Configurations
- team-config.json: Team-wide Codex configuration
- sandbox-rules.json: Security rules for command execution
- personality-settings.json: Interaction style configuration

#### Documentation
- README.md: Comprehensive guide to everything-codex
- INSTALL.md: Installation instructions
- CONTRIBUTING.md: Contribution guidelines
- COMPARISON.md: Comparison with legacy platforms and Codex

### Features
- Multi-agent orchestration support
- Worktree-based parallel development
- Background automation scheduling
- Comprehensive skills library
- Reusable prompts collection
- Security-focused sandbox rules
- Flexible personality settings

### Inspired By
- Original upstream collection: The source project that informed everything-codex
- OpenAI Codex: Multi-agent coding capabilities
- Real-world production usage patterns

---

## Future Releases

### [1.2.0] - Planned
- AWS, GCP, Azure deployment skills
- Additional automation templates
- Enhanced multi-agent workflows
- More domain-specific prompts
- Additional MCP server integrations

### [1.3.0] - Planned
- Custom skill generator
- Automation builder UI
- Workflow templates for common scenarios
- Performance monitoring skills
- Advanced security scanning

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on contributing to everything-codex.

## License

MIT - Use freely, modify as needed, contribute back if you can.
