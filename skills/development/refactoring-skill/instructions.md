# Refactoring Skill

## Purpose
Improve code structure, readability, and maintainability without changing behavior. Always keep tests green.

## Golden Rule
**Never refactor without tests. Never change behavior while refactoring.**

## Process

### 1. Ensure Test Coverage
- Run existing tests — must be green before starting
- If coverage < 80%, write tests first
- Commit the test baseline

### 2. Identify Refactoring Targets
Common code smells to look for:
- Long functions (> 30 lines)
- Deep nesting (> 3 levels)
- Duplicate code (DRY violations)
- Large classes doing too much
- Long parameter lists (> 4 params)
- Magic numbers/strings
- Inconsistent naming

### 3. Apply Refactoring Incrementally
One change at a time, run tests after each:

**Extract Function**
```javascript
// Before
function processOrder(order) {
  // 50 lines of validation
  // 30 lines of calculation
  // 20 lines of notification
}

// After
function processOrder(order) {
  validateOrder(order);
  const total = calculateTotal(order);
  notifyCustomer(order, total);
}
```

**Replace Magic Numbers**
```javascript
// Before
if (status === 3) { ... }

// After
const ORDER_STATUS_SHIPPED = 3;
if (status === ORDER_STATUS_SHIPPED) { ... }
```

**Simplify Conditionals**
```javascript
// Before
if (!isLoggedIn) {
  if (!hasPermission) {
    return false;
  }
}
return true;

// After
return isLoggedIn && hasPermission;
```

**Extract Class**
```javascript
// Before: UserService doing too much
class UserService {
  // auth methods
  // profile methods
  // billing methods
  // notification methods
}

// After: Single responsibility
class AuthService { ... }
class ProfileService { ... }
class BillingService { ... }
```

### 4. Verify After Each Step
```bash
npm test          # must stay green
git diff          # review changes
git commit -m "refactor: extract validateOrder function"
```

## Refactoring Catalog

| Smell | Refactoring |
|-------|-------------|
| Long function | Extract Function |
| Duplicate code | Extract Function / Pull Up Method |
| Large class | Extract Class |
| Long param list | Introduce Parameter Object |
| Magic literals | Replace with Named Constant |
| Deep nesting | Extract Function / Guard Clauses |
| Feature envy | Move Method |
| Data clumps | Extract Class |

## Output Format

```
Refactoring Plan
================

Target: {{file or module}}
Issues Found:
- {{smell 1}} at {{location}}
- {{smell 2}} at {{location}}

Steps:
1. {{refactoring step}} → run tests ✓
2. {{refactoring step}} → run tests ✓
3. {{refactoring step}} → run tests ✓

Result:
- Lines reduced: {{before}} → {{after}}
- Complexity reduced: {{before}} → {{after}}
- Test coverage: {{coverage}}% ✓
```

## Best Practices
- Commit after every successful refactoring step
- Keep PRs small and focused on one refactoring type
- Don't mix refactoring with feature changes
- Use your IDE's automated refactoring tools when available
