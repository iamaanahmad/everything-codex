# Issue Triage Skill

## Purpose
Systematically triage new GitHub issues: classify type, assign priority, add labels, suggest assignees, and flag duplicates or security issues.

## Triage Process

### 1. Classify Issue Type
| Type | Indicators |
|------|-----------|
| `bug` | "crash", "error", "broken", "not working", "regression" |
| `feature` | "add", "support", "would be nice", "request" |
| `question` | "how do I", "is it possible", "does X support" |
| `documentation` | "docs", "readme", "unclear", "confusing" |
| `security` | "vulnerability", "CVE", "injection", "auth bypass" |
| `performance` | "slow", "timeout", "memory", "CPU" |

### 2. Assign Priority
| Priority | Criteria |
|----------|---------|
| P0 — Critical | Production down, data loss, security vulnerability |
| P1 — High | Major feature broken, affects many users |
| P2 — Medium | Feature partially broken, workaround exists |
| P3 — Low | Minor issue, cosmetic, edge case |

### 3. Check for Duplicates
```bash
# Search for similar issues
gh issue list --search "keyword" --state all
```

### 4. Request Missing Info
If the issue lacks reproduction steps, version info, or error logs, post:

```markdown
Thanks for the report! To help us investigate, could you provide:

- [ ] Steps to reproduce
- [ ] Expected vs actual behavior
- [ ] Version/environment (`node --version`, OS, browser)
- [ ] Error message or stack trace (if applicable)
```

### 5. Apply Labels & Assign
```bash
# Add labels
gh issue edit 42 --add-label "bug,P1,backend"

# Assign
gh issue edit 42 --add-assignee "backend-team-member"

# Close duplicate
gh issue close 42 --comment "Duplicate of #38" --reason "not planned"
```

## Triage Output Format

```
Issue Triage Report
===================
Issue #{{number}}: {{title}}

Type:     bug
Priority: P1 — High
Labels:   bug, backend, authentication
Assignee: @backend-team
Status:   Needs investigation

Reason: User reports login failure affecting production.
        No duplicate found. Reproduction steps provided.

Action: Assigned to backend team for immediate investigation.
```

## Security Issue Handling
If a security vulnerability is detected:
1. **Do not** add public labels like "security vulnerability"
2. Close the public issue with: "Thanks — please report security issues via our security policy."
3. Escalate privately to the security team
4. Reference your `SECURITY.md` file

## Best Practices
- Triage within 24 hours of issue creation
- Never leave an issue without at least a type label
- P0 issues must be assigned immediately
- Close stale issues (no response in 30 days) with a friendly message
