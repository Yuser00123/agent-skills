# Performance Skill

## Purpose

Improve application performance using evidence-driven changes while preserving correctness and maintainability.

Performance optimization should solve measurable problems rather than introduce complexity based on assumptions.

---

## When to Use

Use this skill when:

- Users report slowness
- Builds are becoming large
- Pages load slowly
- APIs respond slowly
- Memory usage is high
- CPU usage is high
- Large datasets are processed
- Rendering is inefficient
- Deployment resources are excessive

---

## Core Principle

Measure before optimizing when measurement is practical.

Identify:

1. What is slow?
2. Where is the bottleneck?
3. How large is the impact?
4. What change could address it?
5. How will improvement be measured?

---

## Performance Areas

Consider:

- Network
- Server response time
- Database queries
- Rendering
- JavaScript execution
- Bundle size
- Images
- Fonts
- Memory
- CPU
- Caching
- Storage
- Build time

---

## Frontend Performance

Consider:

- Bundle size
- Code splitting
- Lazy loading
- Image optimization
- Font loading
- Caching
- Rendering frequency
- Unnecessary client-side JavaScript
- Duplicate network requests

Do not add optimization mechanisms without understanding their tradeoffs.

---

## React / Component Performance

Where applicable, investigate:

- Unnecessary renders
- Expensive computations
- Large lists
- Unstable dependencies
- Excessive state updates
- Poor component boundaries

Do not add memoization everywhere.

Memoization should be justified by actual or likely repeated work.

---

## Network Performance

Minimize unnecessary:

- Requests
- Payload size
- Duplicate requests
- Blocking resources

Use:

- Caching
- Pagination
- Compression
- Appropriate data fetching
- Batching where useful

Do not sacrifice correctness simply to reduce request count.

---

## Backend Performance

Investigate:

- Slow database queries
- N+1 queries
- Blocking operations
- Unnecessary serialization
- Excessive API calls
- Large payloads
- Inefficient algorithms

Prefer algorithmic improvements when they provide substantial benefit.

---

## Database

Consider:

- Query plans
- Indexes
- Pagination
- Fetching only required fields
- Connection management
- Query frequency

Do not add indexes or caching blindly.

---

## Memory

Watch for:

- Unbounded arrays
- Caches without limits
- Event-listener leaks
- Large temporary objects
- Unreleased resources

Long-running services require special attention to memory growth.

---

## Caching

Caching should consider:

- Cache key correctness
- Expiration
- Invalidation
- Stale data
- Memory usage
- User-specific data

Never cache private data in a way that allows cross-user exposure.

---

## Performance Verification

When optimizing, compare before and after when tooling allows.

Possible measures:

- Response time
- Bundle size
- Memory usage
- CPU usage
- Render time
- Lighthouse-style metrics
- Test execution time
- Build duration

Do not invent performance improvements without measurements or evidence.

---

## Completion Criteria

Performance work is complete when:

- A meaningful bottleneck was identified.
- The change addresses that bottleneck.
- Correctness remains intact.
- Relevant measurements or observations support the result.
- No unnecessary complexity was introduced.