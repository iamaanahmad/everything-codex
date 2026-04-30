# Web App Example

Example of using everything-codex for a full-stack web application.

## Project Structure

```
web-app-example/
├── frontend/          # React + TypeScript
├── backend/           # Node.js + Express
├── database/          # PostgreSQL
├── .codex/           # Codex configuration
│   ├── skills/       # Project-specific skills
│   └── workflows/    # Custom workflows
└── README.md
```

## Skills Used

### Development
- **code-review-skill**: Review all PRs
- **tdd-workflow-skill**: TDD for new features
- **debugging-skill**: Debug production issues

### Deployment
- **vercel-deploy-skill**: Deploy frontend to Vercel
- **docker-deploy-skill**: Deploy backend to Docker

### Design
- **figma-to-code-skill**: Convert designs to React components

### Project Management
- **linear-integration-skill**: Manage issues and sprints

## Automations Configured

### Daily Triage (9 AM)
```json
{
  "name": "Daily Issue Triage",
  "schedule": "0 9 * * *",
  "instructions": "Triage new GitHub issues, assign priorities and labels"
}
```

### CI Failure Summary (Every 6 hours)
```json
{
  "name": "CI Failure Summary",
  "schedule": "0 */6 * * *",
  "instructions": "Summarize CI failures and suggest fixes"
}
```

### Release Brief (5 PM Daily)
```json
{
  "name": "Release Brief",
  "schedule": "0 17 * * *",
  "instructions": "Generate daily release brief with merged PRs"
}
```

## Workflows

### Feature Development
```
User: Build user authentication feature

Codex: Creating 4-agent workflow...

Agent 1 (Backend): 
- Branch: feature/auth-backend
- Tasks: JWT auth, login/register endpoints, password hashing
- Skills: tdd-workflow-skill

Agent 2 (Frontend):
- Branch: feature/auth-frontend
- Tasks: Login/register forms, auth context, protected routes
- Skills: figma-to-code-skill, react-patterns-skill

Agent 3 (Testing):
- Branch: feature/auth-tests
- Tasks: Integration tests, E2E tests, security tests
- Skills: testing-skill

Agent 4 (Docs):
- Branch: feature/auth-docs
- Tasks: API docs, user guide, security docs
- Skills: documentation-skill

All agents working in parallel using worktrees.
```

### Bug Fix
```
User: Fix login redirect bug

Codex: Creating bug fix workflow...

Agent 1 (Investigation):
- Reproduce bug
- Analyze logs
- Identify root cause

Agent 2 (Fix):
- Write failing test
- Implement fix
- Verify fix

Agent 3 (Testing):
- Add regression tests
- Test related functionality
- Run full test suite

Agent 4 (Docs):
- Update changelog
- Document fix
```

## Example Conversations

### Code Review
```
User: Review this PR for security issues

Codex: [Activates code-review-skill]

Security Analysis:
✗ Password stored in plain text (line 45)
✗ No rate limiting on login endpoint
✗ JWT secret hardcoded (line 12)
⚠ Missing CSRF protection

Recommendation: BLOCK - Critical security issues
```

### TDD Implementation
```
User: Implement password reset using TDD

Codex: [Activates tdd-workflow-skill]

=== RED Phase ===
test('sendPasswordResetEmail sends email with token', async () => {
  const result = await sendPasswordResetEmail('user@example.com');
  expect(result.sent).toBe(true);
  expect(result.token).toBeDefined();
});

Running test... ✗ FAILED

=== GREEN Phase ===
async function sendPasswordResetEmail(email) {
  const token = generateToken();
  await sendEmail(email, token);
  return { sent: true, token };
}

Running test... ✓ PASSED

=== REFACTOR Phase ===
// Add token expiration, validation, etc.
```

### Deployment
```
User: Deploy frontend to Vercel

Codex: [Activates vercel-deploy-skill]

Pre-Deployment Checks:
✓ Tests passing
✓ Build successful
✓ No security issues

Deploying...
✓ Deployed to https://my-app.vercel.app

Post-Deployment:
✓ URLs accessible
✓ Performance score: 95/100
```

## Configuration

### Team Config
```json
{
  "team": "web-app-team",
  "skills": {
    "enabled": [
      "code-review-skill",
      "tdd-workflow-skill",
      "vercel-deploy-skill",
      "linear-integration-skill"
    ],
    "autoActivate": true
  },
  "personality": "terse"
}
```

### Sandbox Rules
```json
{
  "rules": [
    {
      "command": "npm install",
      "permission": "allow"
    },
    {
      "command": "vercel deploy",
      "permission": "ask"
    }
  ]
}
```

## Results

### Before everything-codex
- Manual code reviews (slow, inconsistent)
- No automated testing workflow
- Manual deployments (error-prone)
- Scattered documentation

### After everything-codex
- ✅ Automated code reviews (consistent, thorough)
- ✅ TDD workflow (better test coverage)
- ✅ Automated deployments (fast, reliable)
- ✅ Auto-generated documentation
- ✅ Multi-agent parallel development
- ✅ Background automations

### Metrics
- **Code review time**: 2 hours → 15 minutes
- **Test coverage**: 45% → 87%
- **Deployment time**: 30 minutes → 5 minutes
- **Bug detection**: Reactive → Proactive
- **Development velocity**: 2x faster

## Lessons Learned

### What Worked Well
- ✅ TDD workflow improved code quality
- ✅ Automated code reviews caught issues early
- ✅ Multi-agent workflows enabled parallel development
- ✅ Automations saved hours of manual work

### Challenges
- ⚠ Initial setup took time
- ⚠ Learning curve for workflows
- ⚠ Needed to tune automation schedules

### Best Practices
- Start with a few skills, add more gradually
- Use terse personality for faster execution
- Review automation results regularly
- Customize skills for your project
- Use worktrees for parallel development

## Next Steps

1. Add more skills (performance monitoring, security scanning)
2. Create custom workflows for common tasks
3. Integrate with more tools (Jira, Slack)
4. Expand automation coverage
5. Share learnings with team

---

**This example demonstrates the power of everything-codex for real-world web application development.**
