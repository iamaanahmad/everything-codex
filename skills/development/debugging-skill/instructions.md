# Debugging Skill

## Purpose
Systematically debug issues using root cause analysis, hypothesis testing, and regression prevention.

## Debugging Process

### 1. Reproduce
- Confirm the bug is reproducible
- Identify exact steps to trigger it
- Note environment, inputs, and conditions
- Capture error messages and stack traces

### 2. Gather Information
- Collect relevant logs
- Check recent git changes (`git log --oneline -20`)
- Review error monitoring (Sentry, Datadog)
- Identify affected users/scope

### 3. Form Hypothesis
- List possible root causes
- Rank by likelihood
- Start with simplest explanation

### 4. Test Hypothesis
- Add targeted logging or breakpoints
- Isolate the failing component
- Confirm or eliminate each hypothesis

### 5. Implement Fix
- Write a failing test that reproduces the bug first
- Apply the minimal fix
- Verify the test now passes

### 6. Verify & Prevent
- Run full test suite
- Check for side effects
- Add regression test
- Document the fix

## Common Patterns

### Null/Undefined Errors
```
Symptom: TypeError: Cannot read property 'x' of undefined
Approach:
1. Trace where the value originates
2. Check all code paths that set it
3. Add null guard or optional chaining
```

### Async/Race Conditions
```
Symptom: Intermittent failures, works sometimes
Approach:
1. Add timestamps to logs
2. Check for missing await
3. Look for shared mutable state
4. Use proper synchronization
```

### Performance Regression
```
Symptom: Suddenly slow after a change
Approach:
1. git bisect to find the commit
2. Profile before/after
3. Check for N+1 queries or O(n²) loops
```

### Memory Leaks
```
Symptom: Memory grows over time, eventual crash
Approach:
1. Take heap snapshots
2. Look for event listeners not removed
3. Check for circular references
4. Review setInterval/setTimeout cleanup
```

## Output Format

```
Debugging Report
================

Issue: {{issue-description}}

Root Cause:
{{root-cause}}

Evidence:
- {{log-line or stack trace}}
- {{relevant code location}}

Fix Applied:
{{description of fix}}

Regression Test Added: ✓
Full Test Suite: ✓ PASSING

Prevention:
{{how to avoid this class of bug in future}}
```

## Best Practices
- Never guess — always verify with evidence
- Fix the root cause, not the symptom
- Always add a regression test
- Document non-obvious fixes with a comment
