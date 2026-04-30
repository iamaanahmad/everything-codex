# Testing Prompts

## TDD Implementation

```
Implement this feature using Test-Driven Development:

Feature: {{feature-description}}

Follow TDD cycle:
1. RED: Write failing test first
2. GREEN: Implement minimal code to pass
3. REFACTOR: Improve code while keeping tests green

Requirements:
- Write tests before implementation
- One test at a time
- Minimal implementation first
- Refactor only when tests are green
- Aim for 80%+ coverage

Provide:
- Test code
- Implementation code
- Test results
- Coverage report
```

## Unit Test Generation

```
Generate comprehensive unit tests for this code:

Focus on:
- Happy path scenarios
- Edge cases
- Error cases
- Boundary conditions
- Input validation
- Return values

Test framework: {{framework}}

Provide:
- Complete test suite
- Test descriptions
- Mock/stub setup
- Assertions
- Coverage estimate
```

## Integration Test Generation

```
Create integration tests for this API/module:

Test scenarios:
- API endpoint integration
- Database integration
- External service integration
- Error handling
- Data flow

Requirements:
- Test real integrations (not mocked)
- Setup and teardown
- Test data management
- Isolation between tests

Provide:
- Integration test suite
- Setup/teardown code
- Test data fixtures
- Expected results
```

## E2E Test Generation

```
Create end-to-end tests for this user flow:

User Flow: {{flow-description}}

Test framework: Playwright/Cypress

Cover:
- Happy path
- Error scenarios
- Edge cases
- Different user roles
- Mobile/desktop views

Provide:
- E2E test suite
- Page objects (if applicable)
- Test data setup
- Assertions
- Screenshots/videos on failure
```

## Test Coverage Analysis

```
Analyze test coverage and suggest improvements:

Current coverage: {{coverage}}%

Identify:
- Untested code paths
- Missing test scenarios
- Edge cases not covered
- Error handling gaps
- Integration points not tested

Provide:
- Coverage gaps
- Suggested test cases
- Priority order
- Estimated effort
```

## Regression Test Suite

```
Create regression test suite for this bug fix:

Bug: {{bug-description}}
Fix: {{fix-description}}

Requirements:
- Test that reproduces original bug
- Test that verifies fix
- Tests for related functionality
- Tests to prevent similar bugs

Provide:
- Regression test suite
- Test descriptions
- Expected behavior
- How to run tests
```

## Performance Testing

```
Create performance tests for this code:

Performance requirements:
- Response time: {{time}}ms
- Throughput: {{requests}}/sec
- Memory usage: < {{memory}}MB
- CPU usage: < {{cpu}}%

Test scenarios:
- Normal load
- Peak load
- Stress testing
- Endurance testing

Provide:
- Performance test suite
- Load testing scripts
- Performance benchmarks
- Bottleneck identification
```

## API Testing

```
Generate API tests for these endpoints:

Endpoints: {{endpoints}}

Test:
- Request/response structure
- Status codes
- Error handling
- Authentication
- Rate limiting
- Input validation
- Edge cases

Provide:
- API test suite
- Request examples
- Expected responses
- Error scenarios
```

## Component Testing (React)

```
Create component tests for this React component:

Component: {{component-name}}

Test:
- Rendering with different props
- User interactions
- State changes
- Event handlers
- Conditional rendering
- Error boundaries

Testing library: React Testing Library

Provide:
- Component test suite
- Render scenarios
- User interaction tests
- Assertions
```

## Snapshot Testing

```
Create snapshot tests for UI components:

Components: {{components}}

Requirements:
- Initial snapshots
- Props variations
- State variations
- Responsive breakpoints

Provide:
- Snapshot test suite
- Snapshot descriptions
- Update strategy
- Review guidelines
```

## Test Refactoring

```
Refactor these tests for better maintainability:

Issues to address:
- Test duplication
- Hard-to-read tests
- Brittle tests
- Slow tests
- Flaky tests

Improvements:
- Extract common setup
- Use test helpers
- Improve test names
- Reduce coupling
- Improve assertions

Provide:
- Refactored test suite
- Helper functions
- Improved structure
- Performance improvements
```

## Mock/Stub Strategy

```
Design mocking strategy for this code:

External dependencies:
- {{dependency-1}}
- {{dependency-2}}

Decide for each:
- Mock or real implementation?
- Mock at what level?
- Shared mocks or per-test?
- Mock data strategy

Provide:
- Mocking strategy
- Mock implementations
- Mock data fixtures
- Best practices
```

## Test Data Management

```
Design test data management strategy:

Requirements:
- Consistent test data
- Easy to maintain
- Isolated between tests
- Realistic data
- Edge case data

Provide:
- Test data structure
- Data generation strategy
- Fixtures/factories
- Setup/teardown approach
```

## Flaky Test Debugging

```
Debug and fix flaky tests:

Flaky tests: {{test-names}}

Investigate:
- Timing issues
- Race conditions
- Shared state
- External dependencies
- Random data

Provide:
- Root cause analysis
- Fixes for flaky tests
- Prevention strategies
- Monitoring approach
```

## Test Automation Strategy

```
Design test automation strategy for this project:

Project type: {{project-type}}

Define:
- Test pyramid (unit/integration/e2e ratio)
- Test frameworks
- CI/CD integration
- Test environments
- Reporting
- Maintenance approach

Provide:
- Automation strategy
- Tool recommendations
- CI/CD configuration
- Best practices
```
