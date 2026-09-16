# Code Quality Skill

## Purpose

Keep the codebase understandable, maintainable, consistent, and resilient as it evolves.

Code quality is about long-term correctness, not merely passing a compiler.

---

## When to Use

Use this skill for:

- New features
- Bug fixes
- Refactoring
- Code reviews
- Architecture changes
- Cleanup
- Performance work
- Production preparation

---

## Quality Principles

Prefer code that is:

- Correct
- Clear
- Maintainable
- Testable
- Consistent
- Focused
- Predictable

Avoid cleverness that makes code harder to understand.

---

## Understand Before Changing

Inspect:

- Existing architecture
- Naming conventions
- Error handling
- Data flow
- Existing abstractions
- Testing patterns
- Configuration

Follow established project conventions unless there is a documented reason to change them.

---

## Functions

Prefer functions with clear responsibilities.

Avoid functions that:

- Do too many unrelated tasks
- Have excessive branching
- Mix business logic and presentation without reason
- Depend on hidden global state

Split code when doing so makes responsibilities clearer.

---

## Naming

Use names that communicate intent.

Prefer:

```text
validateUserInput()
createDeployment()
getRepositoryStatus()
```

over vague names such as:

```text
doThing()
processData()
handleStuff()
```

Use the project's established naming conventions.

---

## Duplication

Look for duplicated logic when changing an area.

Do not automatically abstract every repeated line.

Abstract when:

- Behavior is genuinely shared.
- Duplication creates maintenance risk.
- The abstraction remains understandable.

---

## Error Handling

Errors should:

- Be detectable
- Preserve useful diagnostic information
- Be handled at the correct layer
- Not be silently swallowed

Avoid:

```text
catch -> ignore
```

unless the failure is intentionally harmless and documented by the context.

---

## Complexity

Avoid unnecessary:

- Nested conditionals
- Global state
- Abstractions
- Dependencies
- Configuration
- Indirection

Use simple solutions when simple solutions are sufficient.

---

## Refactoring

When refactoring:

1. Understand current behavior.
2. Establish tests or verification.
3. Make focused changes.
4. Preserve external behavior unless intentionally changing it.
5. Run checks.
6. Review the diff.

Do not combine a large unrelated refactor with a feature unless necessary.

---

## Maintainability

Consider:

- Future debugging
- Testability
- Extension points
- Error recovery
- Configuration
- Documentation
- Ownership boundaries

Code should be understandable by another developer who did not create it.

---

## Review Checklist

Inspect for:

- Dead code
- TODO placeholders
- Duplicate logic
- Suspicious workarounds
- Hidden side effects
- Poor naming
- Excessive complexity
- Missing error handling
- Missing tests
- Unnecessary dependencies

---

## Completion Criteria

Code-quality work is complete when the implementation is clear, consistent with the codebase, appropriately tested, and does not introduce unnecessary complexity or obvious maintenance problems.