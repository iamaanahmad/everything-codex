# Debugging Prompts

## Systematic Debugging

```
Debug this issue systematically:

Issue: {{issue-description}}

Follow these steps:
1. Reproduce the issue
2. Gather information (logs, stack traces, metrics)
3. Form hypothesis about root cause
4. Test hypothesis
5. Implement fix
6. Verify fix resolves issue
7. Add regression test

Provide:
- Reproduction steps
- Information gathered
- Root cause analysis
- Fix implementation
- Verification results
- Regression test
```

## Performance Debugging

```
Investigate this performance issue:

Issue: {{performance-issue}}
Current: {{current-performance}}
Expected: {{expected-performance}}

Steps:
1. Profile the code
2. Identify bottlenecks
3. Analyze database queries
4. Check network requests
5. Review algorithm complexity
6. Suggest optimizations

Provide:
- Profiling results
- Bottleneck identification
- Optimization suggestions
- Expected improvement
- Implementation plan
```

## Memory Leak Debugging

```
Debug memory leak in this application:

Symptoms: {{symptoms}}

Investigate:
1. Take memory snapshots
2. Identify growing objects
3. Find references preventing GC
4. Check for event listener leaks
5. Review closure usage
6. Check for global variables

Provide:
- Memory analysis
- Leak sources identified
- Fix recommendations
- Prevention strategies
```

## Race Condition Debugging

```
Debug race condition:

Issue: {{race-condition-description}}

Investigate:
1. Identify concurrent operations
2. Find shared state
3. Analyze timing dependencies
4. Check synchronization
5. Review async code

Provide:
- Race condition analysis
- Timing diagram
- Fix implementation
- Testing strategy
```

## API Debugging

```
Debug API issue:

Endpoint: {{endpoint}}
Issue: {{issue}}

Check:
1. Request format
2. Response format
3. Status codes
4. Headers
5. Authentication
6. Rate limiting
7. Server logs

Provide:
- Request/response analysis
- Issue identification
- Fix recommendation
- Testing approach
```

## Database Debugging

```
Debug database issue:

Issue: {{database-issue}}

Investigate:
1. Query execution plan
2. Index usage
3. Lock contention
4. Connection pooling
5. Transaction isolation
6. Data integrity

Provide:
- Query analysis
- Performance metrics
- Optimization suggestions
- Fix implementation
```

## Frontend Debugging

```
Debug frontend issue:

Issue: {{frontend-issue}}
Browser: {{browser}}

Check:
1. Console errors
2. Network requests
3. React DevTools (if React)
4. Performance profiling
5. Memory usage
6. Event listeners

Provide:
- Error analysis
- Root cause
- Fix implementation
- Browser compatibility check
```

## Network Debugging

```
Debug network issue:

Issue: {{network-issue}}

Investigate:
1. Request/response headers
2. Status codes
3. Payload size
4. Latency
5. CORS issues
6. SSL/TLS issues
7. Timeout settings

Provide:
- Network analysis
- Issue identification
- Fix recommendations
- Monitoring suggestions
```

## Crash Debugging

```
Debug application crash:

Crash: {{crash-description}}
Stack trace: {{stack-trace}}

Analyze:
1. Stack trace
2. Error message
3. State at crash time
4. Recent changes
5. Environment factors

Provide:
- Crash analysis
- Root cause
- Fix implementation
- Prevention measures
```

## Intermittent Bug Debugging

```
Debug intermittent bug:

Bug: {{bug-description}}
Frequency: {{frequency}}

Investigate:
1. Identify patterns
2. Check timing dependencies
3. Review state management
4. Check external dependencies
5. Add logging
6. Reproduce consistently

Provide:
- Pattern analysis
- Root cause hypothesis
- Reproduction steps
- Fix strategy
```

## Production Issue Debugging

```
Debug production issue:

Issue: {{production-issue}}
Impact: {{impact}}
Priority: {{priority}}

Immediate actions:
1. Assess impact
2. Implement mitigation
3. Gather logs/metrics
4. Identify root cause
5. Implement fix
6. Deploy fix
7. Monitor

Provide:
- Impact assessment
- Mitigation strategy
- Root cause analysis
- Fix implementation
- Deployment plan
- Monitoring approach
```

## Error Message Debugging

```
Debug cryptic error message:

Error: {{error-message}}

Investigate:
1. Search error message
2. Check documentation
3. Review stack trace
4. Check recent changes
5. Verify environment
6. Test in isolation

Provide:
- Error explanation
- Root cause
- Fix implementation
- Prevention tips
```

## Integration Debugging

```
Debug integration issue:

Integration: {{integration-name}}
Issue: {{issue}}

Check:
1. API compatibility
2. Data format
3. Authentication
4. Network connectivity
5. Rate limits
6. Error handling

Provide:
- Integration analysis
- Issue identification
- Fix recommendations
- Testing approach
```

## State Management Debugging

```
Debug state management issue:

Issue: {{state-issue}}
Framework: {{framework}}

Investigate:
1. State flow
2. State mutations
3. Side effects
4. Race conditions
5. State persistence

Provide:
- State flow diagram
- Issue identification
- Fix implementation
- Best practices
```

## Build/Deployment Debugging

```
Debug build or deployment issue:

Issue: {{build-issue}}
Environment: {{environment}}

Check:
1. Build logs
2. Dependencies
3. Environment variables
4. Configuration files
5. Permissions
6. Resource limits

Provide:
- Build analysis
- Issue identification
- Fix recommendations
- Deployment checklist
```
