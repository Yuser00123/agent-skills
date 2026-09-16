# Coding Skill

## Purpose

This skill defines how the agent should implement software changes safely, maintainably, and consistently with an existing project.

The objective is to produce working code that addresses the user's actual request while minimizing regressions, unnecessary complexity, and unrelated changes.

---

## When to Use This Skill

Use this skill when:

- Implementing a new feature.
- Fixing an identified code defect.
- Refactoring code.
- Adding or modifying APIs.
- Updating components.
- Updating configuration.
- Adding tests required by a change.
- Making a deliberate architectural change.

---

## Core Principles

### 1. Understand Before Editing

Use Repo Analysis and Code Search when necessary.

### 2. Make the Smallest Correct Change

Do not rewrite an entire subsystem when a focused change solves the problem.

### 3. Preserve Existing Behavior

Unless the requested change explicitly requires behavior to change.

### 4. Verify the Result

A code change is not complete merely because the file was successfully edited.

### 5. Follow Existing Conventions

Do not introduce a new coding style unnecessarily.

---

## Implementation Workflow

Use:

```text
Understand
 → Plan
 → Inspect
 → Implement
 → Test
 → Build
 → Review
 → Verify
```

---

## Before Coding

Determine:

- exact requested behavior
- affected files
- relevant dependencies
- existing implementation
- expected inputs/outputs
- error conditions
- testing approach

For a substantial change, create a concise internal implementation plan.

---

## Plan Proportionally

For a small fix:

```text
1. Inspect file.
2. Patch bug.
3. Test.
```

For a medium feature:

```text
1. Inspect architecture.
2. Identify affected modules.
3. Implement core behavior.
4. Update integration points.
5. Add/update tests.
6. Build.
```

For a large feature:

Break the change into independently verifiable stages.

---

## Existing Code First

Before introducing a new utility, component, service, or helper, search for existing equivalents.

Prefer reuse when the existing abstraction is appropriate.

Avoid creating:

```text
utils2
helperNew
newService
anotherApiClient
```

without determining whether the project already has suitable abstractions.

---

## Minimal Change Principle

Prefer:

```text
patch existing function
```

over:

```text
rewrite entire file
```

unless the current implementation genuinely requires replacement.

This reduces:

- accidental regressions
- formatting churn
- merge conflicts
- review difficulty
- loss of unrelated user changes

---

## Dependency Management

Do not add dependencies automatically.

Before adding a package:

1. Check whether the project already provides the capability.
2. Check existing dependencies.
3. Consider whether native functionality is sufficient.
4. Ensure the new dependency is appropriate for the project's ecosystem.
5. Update the correct package metadata.
6. Update the lockfile using the project's package manager.

Never silently change package manager strategy.

---

## API Changes

When modifying an API:

Inspect both sides of the contract when applicable.

Consider:

- request structure
- validation
- response structure
- status codes
- authentication
- error handling
- callers
- tests

Avoid breaking existing clients unless explicitly required.

---

## Error Handling

Handle errors at the appropriate layer.

Do not:

```text
catch error
return success
```

merely to make execution appear successful.

Errors should remain distinguishable from valid results.

Preserve useful diagnostic information while avoiding secret leakage.

---

## Security During Coding

Never hardcode:

- API keys
- passwords
- tokens
- private credentials
- secrets

Use the project's established secret/environment configuration.

Do not log sensitive values.

Never weaken authentication or validation merely to make a feature easier to implement.

---

## Async and Concurrency

Respect the existing asynchronous model.

Before introducing concurrent behavior, consider:

- shared state
- race conditions
- duplicate writes
- ordering
- retries
- cancellation
- resource limits

Do not use concurrency simply because it makes code shorter.

---

## User-Owned Changes

Check Git state before substantial modifications.

If files already contain unrelated changes:

- preserve them
- patch around them
- do not reset them
- do not overwrite broad file regions unnecessarily

---

## Refactoring Rules

Refactor when it meaningfully improves the requested change.

Do not turn a bug fix into an unrelated architecture rewrite.

When refactoring:

- preserve behavior
- keep changes logically grouped
- validate before and after where practical
- update tests when behavior or structure requires it

---

## New Feature Rules

A complete feature generally requires:

```text
implementation
+
integration
+
error handling
+
testing
+
verification
```

Do not stop after creating the visible UI if backend/API integration is required.

Do not stop after implementing a backend route if the user-facing flow requires more.

---

## Testing During Coding

Add or update tests when practical, especially for:

- business logic
- regression fixes
- APIs
- parsing
- validation
- security-sensitive behavior
- shared utilities

A test should verify meaningful behavior, not merely execute lines.

---

## Comments

Write comments when they explain:

- why something unusual exists
- non-obvious business logic
- constraints
- compatibility decisions
- security considerations

Do not add comments that merely repeat code.

Bad:

```js
// increment i
i++;
```

Useful:

```js
// Retry only idempotent requests because POST operations may already have side effects.
```

---

## Code Quality

Prefer:

- clear naming
- small focused functions
- understandable control flow
- consistent formatting
- explicit error handling
- reusable abstractions only when justified

Avoid unnecessary:

- abstraction
- indirection
- metaprogramming
- clever one-liners
- duplicate logic
- hidden global state

---

## Completion Handoff

After implementation, invoke:

- Testing
- Build Verification
- Self Review
- Completion Verification

as appropriate.

---

## Coding Failure Recovery

If implementation introduces an error:

1. Read the actual error.
2. Identify the failing layer.
3. Inspect relevant code.
4. Fix the root cause.
5. Re-run the failed validation.
6. Re-run broader validation when necessary.

Do not randomly change unrelated code.

---

## Final Rule

**Implement the requested behavior with the smallest maintainable change, then prove that the implementation works.**