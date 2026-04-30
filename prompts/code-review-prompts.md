# Code Review Prompts

## Security-Focused Review

```
Review this code for security vulnerabilities:

Focus Areas:
- Hardcoded secrets (API keys, passwords, tokens)
- SQL injection vulnerabilities
- XSS vulnerabilities
- CSRF protection
- Input validation
- Authentication/authorization
- Insecure dependencies
- Sensitive data exposure
- Error messages that leak information

Provide:
- List of security issues found
- Severity rating (critical, high, medium, low)
- Specific line numbers
- Recommended fixes
- Security best practices to follow
```

## Performance Review

```
Analyze this code for performance issues:

Focus Areas:
- Algorithm complexity (O(n²) or worse)
- N+1 query problems
- Unnecessary re-renders (React)
- Memory leaks
- Inefficient loops
- Missing database indexes
- Large bundle sizes
- Unoptimized images
- Blocking operations

Provide:
- Performance issues found
- Impact assessment
- Specific line numbers
- Optimization suggestions
- Expected performance improvement
```

## Architecture Review

```
Review this code from an architectural perspective:

Focus Areas:
- Separation of concerns
- SOLID principles
- Design patterns usage
- Code organization
- Dependency management
- Scalability considerations
- Maintainability
- Technical debt

Provide:
- Architectural issues
- Design pattern suggestions
- Refactoring recommendations
- Long-term maintainability concerns
```

## Code Quality Review

```
Assess code quality and maintainability:

Focus Areas:
- Naming conventions
- Function/method length
- Code duplication (DRY)
- Cyclomatic complexity
- Error handling
- Documentation
- Code smells
- Readability

Provide:
- Quality issues found
- Specific improvements
- Refactoring suggestions
- Best practices to follow
```

## Test Coverage Review

```
Review test coverage and quality:

Focus Areas:
- Test coverage percentage
- Unit test quality
- Integration test coverage
- E2E test coverage
- Edge case testing
- Error case testing
- Test maintainability
- Test performance

Provide:
- Coverage gaps
- Missing test scenarios
- Test quality issues
- Recommendations for improvement
```

## API Design Review

```
Review API design and implementation:

Focus Areas:
- RESTful principles
- Endpoint naming
- HTTP methods usage
- Status codes
- Request/response structure
- Error handling
- Versioning
- Documentation
- Rate limiting
- Authentication

Provide:
- API design issues
- Consistency problems
- Best practices violations
- Improvement suggestions
```

## Database Review

```
Review database design and queries:

Focus Areas:
- Schema design
- Normalization
- Indexes
- Query efficiency
- N+1 queries
- Transaction handling
- Data integrity
- Migration strategy

Provide:
- Database issues found
- Query optimization suggestions
- Schema improvements
- Performance recommendations
```

## Frontend Review

```
Review frontend code and UI implementation:

Focus Areas:
- Component structure
- State management
- Props drilling
- Re-render optimization
- Accessibility (WCAG)
- Responsive design
- Browser compatibility
- Bundle size
- Loading states
- Error boundaries

Provide:
- Frontend issues
- Component refactoring suggestions
- Performance optimizations
- Accessibility improvements
```

## React-Specific Review

```
Review React code for best practices:

Focus Areas:
- Hooks usage (useState, useEffect, useMemo, useCallback)
- Component composition
- Props validation
- Key props in lists
- Unnecessary re-renders
- Context usage
- Custom hooks
- Error boundaries
- Suspense and lazy loading

Provide:
- React-specific issues
- Hooks optimization
- Component structure improvements
- Performance optimizations
```

## TypeScript Review

```
Review TypeScript code for type safety:

Focus Areas:
- Type definitions
- Any usage
- Type assertions
- Generic usage
- Interface vs Type
- Enum usage
- Null/undefined handling
- Type narrowing
- Utility types

Provide:
- Type safety issues
- Better type definitions
- Generic improvements
- Type narrowing opportunities
```

## Quick Review Template

```
Perform a quick code review covering:

1. Security: Any obvious security issues?
2. Performance: Any performance red flags?
3. Quality: Is the code clean and maintainable?
4. Tests: Are there adequate tests?
5. Documentation: Is the code well-documented?

Provide:
- Quick assessment (APPROVE / REQUEST CHANGES / BLOCK)
- Top 3 issues to address
- Quick wins for improvement
```

## Comprehensive Review Template

```
Perform a comprehensive code review:

1. Security Analysis
   - Check for vulnerabilities
   - Verify input validation
   - Check authentication/authorization

2. Performance Analysis
   - Algorithm efficiency
   - Database queries
   - Resource usage

3. Code Quality
   - SOLID principles
   - Design patterns
   - Code organization

4. Testing
   - Test coverage
   - Test quality
   - Edge cases

5. Documentation
   - Code comments
   - API documentation
   - README updates

Provide detailed report with:
- Issues by category
- Severity ratings
- Specific recommendations
- Overall assessment
```
