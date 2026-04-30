# Code Review Skill

## Purpose
Perform comprehensive code reviews covering security, performance, code quality, and testing.

## When to Use
- Reviewing pull requests
- Pre-merge code validation
- Security audits
- Performance optimization reviews
- Code quality assessments

## Instructions

### 1. Security Analysis
Check for:
- Hardcoded secrets (API keys, passwords, tokens)
- SQL injection vulnerabilities
- XSS vulnerabilities
- CSRF protection
- Input validation
- Authentication/authorization issues
- Insecure dependencies
- Sensitive data exposure

### 2. Performance Analysis
Check for:
- Algorithm complexity (O(n²) or worse)
- N+1 query problems
- Unnecessary re-renders (React)
- Memory leaks
- Inefficient loops
- Missing indexes (database)
- Large bundle sizes
- Unoptimized images

### 3. Code Quality
Check for:
- SOLID principles adherence
- DRY violations
- Code smells
- Naming conventions
- Function/method length
- Cyclomatic complexity
- Error handling
- Documentation

### 4. Testing
Check for:
- Test coverage (minimum 80%)
- Unit tests for business logic
- Integration tests for APIs
- E2E tests for critical flows
- Edge case coverage
- Error case testing

## Output Format

```
Code Review Summary
==================

Security Analysis:
✓ No hardcoded secrets
✓ Input validation present
⚠ Missing CSRF protection on /api/update endpoint

Performance Analysis:
✓ Efficient algorithms
⚠ Consider caching for /api/users endpoint
✗ N+1 query detected in getUserPosts()

Code Quality:
✓ Well-structured functions
✓ Good naming conventions
⚠ Function getUserData() is too long (150 lines)

Testing:
✓ Good test coverage (87%)
✓ Edge cases covered
✗ Missing tests for error scenarios

Recommendation: REQUEST CHANGES
Priority Issues:
1. Fix N+1 query in getUserPosts()
2. Add CSRF protection
3. Add error scenario tests
```

## Examples

### Example 1: Security-Focused Review
```
User: Review this authentication code for security issues

Codex: [Activates code-review-skill]

Security Analysis:
✗ Password stored in plain text (line 45)
✗ No rate limiting on login endpoint
✗ JWT secret hardcoded (line 12)
⚠ Missing password complexity requirements

Recommendation: BLOCK - Critical security issues must be fixed
```

### Example 2: Performance Review
```
User: Review this API endpoint for performance

Codex: [Activates code-review-skill]

Performance Analysis:
✗ N+1 query: Loading users in loop (lines 23-27)
⚠ Missing database index on email field
✓ Efficient pagination implementation
⚠ Consider adding Redis caching

Recommendation: REQUEST CHANGES - Fix N+1 query before merge
```

## Best Practices
- Always check all four areas (security, performance, quality, testing)
- Prioritize security issues
- Provide specific line numbers
- Suggest concrete fixes
- Use clear symbols: ✓ (good), ⚠ (warning), ✗ (critical)
