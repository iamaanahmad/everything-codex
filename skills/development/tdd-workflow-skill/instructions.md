# TDD Workflow Skill

## Purpose
Guide implementation using Test-Driven Development (TDD) methodology.

## TDD Cycle

### RED → GREEN → REFACTOR

1. **RED**: Write a failing test
2. **GREEN**: Write minimal code to pass the test
3. **REFACTOR**: Improve code while keeping tests green

## Instructions

### Phase 1: RED (Write Failing Test)
1. Understand the requirement
2. Write a test that describes the expected behavior
3. Run the test to confirm it fails
4. Verify the failure message is meaningful

### Phase 2: GREEN (Make It Pass)
1. Write the simplest code that makes the test pass
2. Don't worry about perfection yet
3. Run the test to confirm it passes
4. Commit if test passes

### Phase 3: REFACTOR (Improve Code)
1. Look for code smells
2. Improve structure and readability
3. Remove duplication
4. Run tests after each change
5. Commit when refactoring is complete

## Example Workflow

```
User: Implement a function to calculate user age from birthdate

Codex: [Activates tdd-workflow-skill]

=== RED Phase ===
Writing failing test...

// tests/user.test.js
test('calculateAge returns correct age', () => {
  const birthdate = new Date('1990-01-01');
  const age = calculateAge(birthdate);
  expect(age).toBe(34); // Assuming current year is 2024
});

Running test... ✗ FAILED (calculateAge is not defined)

=== GREEN Phase ===
Implementing minimal code...

// src/user.js
function calculateAge(birthdate) {
  const today = new Date();
  const age = today.getFullYear() - birthdate.getFullYear();
  return age;
}

Running test... ✓ PASSED

=== REFACTOR Phase ===
Improving implementation to handle edge cases...

function calculateAge(birthdate) {
  const today = new Date();
  let age = today.getFullYear() - birthdate.getFullYear();
  const monthDiff = today.getMonth() - birthdate.getMonth();
  
  if (monthDiff < 0 || (monthDiff === 0 && today.getDate() < birthdate.getDate())) {
    age--;
  }
  
  return age;
}

Running test... ✓ PASSED

Adding edge case tests...

test('calculateAge handles birthday not yet occurred this year', () => {
  const birthdate = new Date('1990-12-31');
  const age = calculateAge(birthdate);
  expect(age).toBe(33); // If today is before Dec 31
});

Running tests... ✓ ALL PASSED

TDD cycle complete! ✓
```

## Best Practices

### Test Writing
- Write one test at a time
- Test behavior, not implementation
- Use descriptive test names
- Test edge cases
- Test error conditions

### Implementation
- Write minimal code first
- Don't over-engineer
- Keep functions small
- Follow single responsibility principle

### Refactoring
- Refactor only when tests are green
- Make small, incremental changes
- Run tests after each refactoring step
- Commit frequently

## Test Coverage Goals
- Aim for 80%+ code coverage
- 100% coverage for critical business logic
- Cover happy path, edge cases, and error cases

## Common Patterns

### Testing Pure Functions
```javascript
// Easy to test - no side effects
test('add returns sum of two numbers', () => {
  expect(add(2, 3)).toBe(5);
});
```

### Testing Async Functions
```javascript
test('fetchUser returns user data', async () => {
  const user = await fetchUser(1);
  expect(user.id).toBe(1);
  expect(user.name).toBeDefined();
});
```

### Testing Error Cases
```javascript
test('divide throws error when dividing by zero', () => {
  expect(() => divide(10, 0)).toThrow('Cannot divide by zero');
});
```

## When to Use TDD
- ✅ New feature development
- ✅ Bug fixes (write test that reproduces bug first)
- ✅ Refactoring existing code
- ✅ Complex business logic
- ✅ API endpoint development

## When TDD Might Not Fit
- ⚠️ Rapid prototyping/exploration
- ⚠️ UI/UX experimentation
- ⚠️ Simple CRUD operations
- ⚠️ Configuration files

## Output Format
Always show:
1. Current phase (RED/GREEN/REFACTOR)
2. Test code
3. Implementation code
4. Test results
5. Next steps
