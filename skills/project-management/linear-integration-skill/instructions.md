# Linear Integration Skill

## Purpose
Manage projects, issues, and workflows in Linear with intelligent automation.

## Prerequisites
- Linear API key
- Linear workspace access
- Team and project configuration

## Capabilities

### Issue Management
- Create issues
- Update issue status
- Assign issues
- Set priorities
- Add labels
- Link related issues

### Project Management
- Create projects
- Track progress
- Manage sprints
- Generate reports
- Team workload analysis

### Automation
- Auto-triage new issues
- Auto-assign based on expertise
- Auto-prioritize based on impact
- Auto-label based on content
- Link to related PRs

## Instructions

### Create Issue
```
User: Create a Linear issue for implementing user authentication

Codex: [Activates linear-integration-skill]

Creating issue in Linear...

Issue Created:
Title: Implement user authentication
ID: ENG-123
Status: Backlog
Priority: High
Assignee: Auto-assigned to @auth-team
Labels: feature, security, backend
Estimate: 5 points

Description:
Implement JWT-based authentication system with:
- User registration
- Login/logout
- Password reset
- Session management
- Rate limiting

Acceptance Criteria:
- [ ] User can register with email/password
- [ ] User can login and receive JWT token
- [ ] User can logout and invalidate token
- [ ] Password reset flow works
- [ ] Rate limiting prevents brute force

Issue created: https://linear.app/team/issue/ENG-123
```

### Triage Issues
```
User: Triage all new Linear issues

Codex: [Activates linear-integration-skill]

Triaging 12 new issues...

ENG-124: "App crashes on startup"
- Priority: P0 (Critical)
- Assigned: @mobile-team
- Labels: bug, mobile, critical
- Sprint: Current

ENG-125: "Add dark mode"
- Priority: P2 (Medium)
- Assigned: @frontend-team
- Labels: feature, ui
- Sprint: Next

ENG-126: "Improve search performance"
- Priority: P1 (High)
- Assigned: @backend-team
- Labels: performance, backend
- Sprint: Current

... (9 more issues)

Triage complete! ✓
- 2 P0 issues (immediate attention)
- 4 P1 issues (high priority)
- 6 P2 issues (medium priority)
```

### Sprint Planning
```
User: Plan next sprint in Linear

Codex: [Activates linear-integration-skill]

Analyzing team capacity and backlog...

Team Capacity:
- Frontend: 40 points
- Backend: 35 points
- Mobile: 30 points
- Total: 105 points

Recommended Sprint Scope:
High Priority (60 points):
- ENG-123: User authentication (5 pts)
- ENG-127: Payment integration (8 pts)
- ENG-128: Email notifications (5 pts)
- ENG-129: Admin dashboard (13 pts)
- ENG-130: API rate limiting (3 pts)

Medium Priority (35 points):
- ENG-131: Dark mode (8 pts)
- ENG-132: Export data feature (5 pts)
- ENG-133: Improve onboarding (8 pts)

Bug Fixes (10 points):
- ENG-134: Fix login redirect (2 pts)
- ENG-135: Fix mobile layout (3 pts)

Sprint created: Sprint 24 (Jan 15 - Jan 29)
Total: 105 points across 10 issues
```

### Generate Report
```
User: Generate Linear progress report

Codex: [Activates linear-integration-skill]

Sprint 23 Progress Report
========================

Duration: Jan 1 - Jan 14 (2 weeks)
Status: Completed

Velocity:
- Planned: 100 points
- Completed: 95 points
- Completion rate: 95%

Issues:
- Completed: 18/20
- In Progress: 2
- Blocked: 0

By Priority:
- P0: 3/3 completed ✓
- P1: 8/9 completed
- P2: 7/8 completed

By Team:
- Frontend: 38/40 points (95%)
- Backend: 35/35 points (100%)
- Mobile: 22/25 points (88%)

Highlights:
✓ User authentication shipped
✓ Payment integration completed
✓ Mobile app performance improved 40%

Challenges:
⚠ Dark mode delayed (dependency issues)
⚠ Export feature needs more testing

Next Sprint Focus:
- Complete delayed features
- Focus on performance optimization
- Reduce technical debt
```

## Best Practices

### Issue Creation
- Use clear, descriptive titles
- Provide detailed descriptions
- Add acceptance criteria
- Set appropriate priority
- Assign to right team/person
- Add relevant labels

### Prioritization
- P0: Critical bugs, security issues
- P1: Important features, major bugs
- P2: Nice-to-have features
- P3: Low priority improvements

### Labels
- Type: bug, feature, improvement, docs
- Area: frontend, backend, mobile, infra
- Status: blocked, needs-review, ready

### Sprint Planning
- Don't overcommit
- Leave buffer for bugs
- Balance feature work and tech debt
- Consider team capacity
- Account for holidays/PTO

## Automation Rules

### Auto-Assign
```
Bug in mobile app → @mobile-team
Security issue → @security-team
Performance issue → @backend-team
UI/UX issue → @frontend-team
```

### Auto-Prioritize
```
"crash" or "down" → P0
"security" or "vulnerability" → P0
"slow" or "performance" → P1
"feature request" → P2
```

### Auto-Label
```
Contains "login" or "auth" → security
Contains "slow" or "performance" → performance
Contains "UI" or "design" → frontend
Contains "API" or "database" → backend
```

## Integration with Git

### Link Issues to PRs
```bash
# In commit message
git commit -m "Implement user auth (ENG-123)"

# In PR description
Fixes ENG-123
```

### Auto-Update Status
```
PR opened → Issue status: In Progress
PR merged → Issue status: Done
PR closed → Issue status: Canceled
```

## Reporting

### Daily Standup Report
- Issues completed yesterday
- Issues in progress today
- Blockers

### Weekly Progress Report
- Sprint velocity
- Completion rate
- Team performance
- Upcoming risks

### Monthly Summary
- Features shipped
- Bugs fixed
- Team productivity trends
- Technical debt status
