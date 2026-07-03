# Performance Prompts

## Bundle Size Analysis

```
Analyze this project's bundle size and suggest optimizations:

Steps:
1. Run `npm run build` and capture bundle stats
2. Identify the largest modules (use source-map-explorer or bundlesize)
3. Check for duplicate dependencies
4. Look for opportunities to lazy-load routes/components
5. Identify unused exports that tree-shaking missed

Provide:
- Top 10 largest modules with sizes
- Duplicate packages and their total cost
- Specific lazy-loading opportunities
- Expected size reduction per recommendation
```

## Database Query Performance

```
Analyze these database queries for performance issues:

{{queries}}

Check for:
- Missing indexes (look at WHERE, JOIN, ORDER BY columns)
- N+1 query patterns
- Full table scans
- Inefficient JOINs
- Queries that could be batched
- Missing query result caching opportunities

Provide:
- Each problematic query with explanation
- Suggested index definitions
- Rewritten query where applicable
- Expected improvement (e.g., "O(n) → O(log n)")
```

## React Rendering Performance

```
Review this React component tree for rendering performance:

{{component-code}}

Check for:
- Components re-rendering unnecessarily
- Missing useMemo / useCallback
- Expensive computations in render
- Large lists without virtualization
- Context causing wide re-renders
- Missing React.memo on pure components

Provide:
- Components with unnecessary re-renders and why
- Specific memoization opportunities
- Virtualization recommendations for lists > 100 items
- Context refactoring suggestions
```

## API Response Time

```
Investigate why this API endpoint is slow:

Endpoint: {{method}} {{path}}
Current p99 latency: {{latency}}ms
Target: < 200ms

Analyze:
1. Database queries executed (count and duration)
2. External API calls (count and duration)
3. CPU-bound operations
4. Memory allocations
5. Serialization overhead

Provide:
- Bottleneck identified with evidence
- Optimization steps in priority order
- Expected latency after each optimization
- Caching strategy if applicable
```

## Memory Leak Investigation

```
Investigate a memory leak in this application:

Symptoms: {{symptoms}}
Environment: {{environment}}

Steps:
1. Take heap snapshot before and after the suspected operation
2. Compare retained objects
3. Look for event listeners not removed
4. Check for closures holding references
5. Review setInterval/setTimeout cleanup
6. Check for growing arrays/maps/sets

Provide:
- Root cause of the leak
- Specific code location
- Fix with before/after code
- How to verify the fix resolved the leak
```

## Load Testing Analysis

```
Analyze these load test results and identify bottlenecks:

{{load-test-results}}

Evaluate:
- Throughput (requests/second) at different concurrency levels
- Latency percentiles (p50, p95, p99) under load
- Error rate under load
- Where performance degrades (the "knee" of the curve)
- Resource utilization (CPU, memory, DB connections)

Provide:
- Bottleneck identification
- Maximum safe concurrency level
- Scaling recommendations (vertical vs horizontal)
- Quick wins to improve throughput
```

## Build Time Optimization

```
Analyze and optimize this project's build time:

Current build time: {{duration}}
Target: < {{target}}

Check:
- TypeScript compilation settings (incremental, skipLibCheck)
- Webpack/Vite/Turbopack configuration
- Unnecessary transpilation of node_modules
- Parallelization opportunities
- Cache configuration (babel-loader, ts-loader)
- Dead code that increases compilation scope

Provide:
- Current bottlenecks with timing breakdown
- Configuration changes with expected improvement
- CI caching strategy
```
