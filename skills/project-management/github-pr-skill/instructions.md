# GitHub PR Skill

## Purpose
Create well-structured pull requests, manage reviews, and maintain a clean PR workflow using the GitHub CLI.

## Prerequisites
- GitHub CLI: `npm install -g gh` or `brew install gh`
- Authenticated: `gh auth login`

## Creating a PR

### Standard PR
```bash
# Push branch and create PR
git push -u origin feature/my-feature

gh pr create \
  --title "feat: add user authentication" \
  --body "$(cat .github/pull_request_template.md)" \
  --reviewer teammate1,teammate2 \
  --label "feature,backend" \
  --assignee "@me"
```

### Draft PR (work in progress)
```bash
gh pr create --draft --title "WIP: payment integration"
```

## PR Description Template

```markdown
## Summary
Brief description of what this PR does and why.

## Changes
- Added JWT authentication middleware
- Created login/register endpoints
- Added password hashing with bcrypt

## Testing
- [ ] Unit tests added/updated
- [ ] Integration tests pass
- [ ] Tested manually in dev environment

## Screenshots (if UI changes)
<!-- Add before/after screenshots -->

## Related Issues
Closes #123
```

## Review Workflow

```bash
# List open PRs
gh pr list

# Check out a PR locally for review
gh pr checkout 42

# Review and approve
gh pr review 42 --approve --body "LGTM! Clean implementation."

# Request changes
gh pr review 42 --request-changes --body "Please add error handling for the edge case on line 45."

# Merge when approved
gh pr merge 42 --squash --delete-branch
```

## PR Checklist (auto-comment on open)

```markdown
### PR Checklist
- [ ] Tests added for new functionality
- [ ] No hardcoded secrets or credentials
- [ ] Breaking changes documented
- [ ] CHANGELOG updated (if applicable)
- [ ] Self-reviewed the diff
```

## Automation

### Auto-label by branch name
```
feature/* → label: feature
bugfix/*  → label: bug
hotfix/*  → label: hotfix
docs/*    → label: documentation
```

### Link PR to Linear/Jira
```bash
# In PR title or body, reference issue
# Linear: ENG-123 auto-links
# Jira: PROJECT-456 auto-links
```

## Best Practices
- Keep PRs small (< 400 lines changed) — easier to review
- One logical change per PR
- Always link to the issue being resolved
- Respond to review comments within 24 hours
- Squash merge to keep main branch history clean
- Delete branches after merge
