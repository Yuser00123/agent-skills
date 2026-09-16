# Code Documentation Skill

## Purpose

Document code in a way that helps future developers understand intent, behavior, constraints, and important implementation decisions without creating unnecessary documentation noise.

This skill is more specific than the general Documentation skill.

---

## When to Use

Use this skill when:

- Writing or updating comments
- Documenting functions
- Documenting classes
- Documenting modules
- Adding TypeScript/JSDoc documentation
- Documenting complex algorithms
- Documenting public APIs
- Documenting configuration interfaces
- Explaining non-obvious design decisions

---

## Core Principle

Document the parts of the code that are difficult to infer.

Good documentation explains:

> Why this exists and what important constraints apply.

It should not merely repeat:

> What this line visibly does.

---

## Before Writing Documentation

Inspect:

- Actual implementation
- Callers
- Related types
- Tests
- Configuration
- Error behavior

Documentation should describe current behavior.

---

## Comments

Use comments for:

- Non-obvious decisions
- Security constraints
- Workarounds
- Compatibility requirements
- Performance considerations
- Important invariants
- External system constraints

Avoid obvious comments.

Bad:

```js
// Add user to array
users.push(user);
```

Better:

```js
// Preserve insertion order because downstream synchronization uses the order
// to generate deterministic change events.
users.push(user);
```

---

## Why vs What

Prefer documenting **why**.

Avoid:

```text
// Loop through users.
```

Prefer:

```text
// Process sequentially because the remote API rate limit is applied per account.
```

---

## Functions

For important functions document:

- Purpose
- Parameters
- Return value
- Errors/failures
- Important side effects
- Constraints

Do not document trivial functions unnecessarily.

---

## Public APIs

For public APIs, document:

- Inputs
- Outputs
- Authentication
- Errors
- Required constraints
- Examples when useful

Keep documentation synchronized with the implementation.

---

## Complex Algorithms

Document:

- Problem being solved
- Important assumptions
- Why the algorithm was selected
- Important complexity considerations
- Edge cases

Do not explain every line of a straightforward algorithm.

---

## Types and Interfaces

For important types, document fields when their meaning is not obvious.

Especially document:

- Units
- Allowed values
- Optionality
- Defaults
- Lifecycle states
- Security sensitivity

Example:

```ts
interface RetryConfig {
  // Maximum number of additional attempts after the initial request.
  maxRetries: number;
}
```

---

## Error Documentation

When functions can fail in meaningful ways, document important failure conditions.

Examples:

- Authentication failure
- Missing resource
- Validation error
- Timeout
- External-service failure

Do not list every theoretically possible error if the caller cannot act differently on them.

---

## Security Documentation

Document security-sensitive assumptions.

Examples:

- Why authentication is required
- Why an endpoint must remain server-side
- Why a token must not be logged
- Why a file path is restricted
- Why validation occurs before processing

Never put actual credentials in code comments.

---

## Performance Documentation

Document performance constraints when they affect architecture.

Examples:

- Why batching exists
- Why caching is required
- Why a particular algorithm was selected
- Why concurrency is intentionally bounded

Do not keep outdated performance claims.

---

## Temporary Workarounds

If a workaround is necessary, document:

- The problem
- The workaround
- Why it is currently required
- What condition would allow removal

Avoid comments like:

```text
// TODO fix this later
```

without useful context.

---

## Generated Code

Do not manually add large amounts of documentation to generated files unless the project explicitly expects it.

Document the source/configuration that generates the artifact instead.

---

## Documentation Maintenance

When changing behavior:

1. Search for related documentation.
2. Identify stale comments.
3. Update affected documentation.
4. Remove misleading comments.
5. Verify examples.

Outdated comments can be worse than missing comments because they actively mislead future developers.

---

## Documentation Quality Check

Before completion, ask:

- Does this explain something non-obvious?
- Is it accurate?
- Is it still true?
- Is it located near the relevant code?
- Does it reveal any secrets?
- Does it duplicate obvious implementation details?
- Would another developer actually benefit from it?

---

## Completion Criteria

Code documentation is complete when:

- Important non-obvious behavior is documented.
- Security and architectural constraints are captured where necessary.
- Public interfaces are understandable.
- Comments match current implementation.
- Stale documentation has been removed or corrected.
- Documentation adds useful context without unnecessary noise.