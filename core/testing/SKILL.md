# Testing Skill

## Purpose

This skill defines how the agent should validate software changes using the project's existing testing infrastructure and appropriate targeted checks.

Testing exists to provide evidence that behavior is correct and that important existing behavior has not been broken.

---

## When to Use This Skill

Use this skill when:

- Implementing a feature.
- Fixing a bug.
- Refactoring behavior.
- Modifying APIs.
- Changing shared utilities.
- Changing security-sensitive code.
- Changing build or configuration behavior.
- Preparing a task for completion.

---

## Core Principle

**Test behavior, not merely execution.**

A test that runs without failing is not useful if it does not verify the intended outcome.

---

## Before Testing

Inspect the project to determine:

- testing framework
- test command
- test directory
- test scripts
- test configuration
- fixtures
- mocks
- coverage configuration

Do not invent a testing framework when the repository already has one.

---

## Test Hierarchy

Use the smallest useful validation first.

### Level 1 — Targeted Test

Run the specific test associated with the changed behavior.

### Level 2 — Related Tests

Run tests for the surrounding module or feature.

### Level 3 — Full Test Suite

Run the full suite when:

- the change is broad
- shared code was modified
- the repository is small enough
- integration behavior may be affected
- the project convention expects it

---

## Choosing What to Test

For a change, ask:

```text
What behavior changed?
What could regress?
What is the narrowest meaningful test?
```

Examples:

### Utility change

Test:

- normal input
- edge cases
- invalid input

### API change

Test:

- valid request
- validation failure
- authentication behavior
- expected response
- relevant error paths

### UI change

Test when applicable:

- rendering
- user interaction
- state update
- API integration
- accessibility-critical behavior

---

## Regression Testing

Every bug fix should have a regression test when practical.

The regression test should reproduce the original failure before the fix and validate the corrected behavior after the fix.

---

## Edge Cases

Consider:

- empty input
- null/undefined
- boundary values
- malformed data
- missing configuration
- duplicate requests
- network failure
- permission failure
- timeout
- unexpected external responses

Do not add unrealistic tests purely to increase test count.

---

## Testing User Interfaces

UI tests should focus on meaningful user behavior.

Prefer:

```text
user action
 → application behavior
 → observable result
```

over implementation details.

Avoid tests that become fragile because they depend unnecessarily on internal component structure.

---

## Testing APIs

Test:

- method
- path
- input validation
- authentication/authorization where relevant
- successful result
- expected failure modes
- response structure

Do not treat HTTP 200 as success if the returned application state is incorrect.

---

## Testing Async Code

Ensure tests actually await asynchronous behavior.

Be careful with:

- timers
- promises
- callbacks
- polling
- retries
- network mocks
- concurrent requests

Avoid tests that pass only because they finish before asynchronous failures occur.

---

## Mocking

Use mocks when they make tests:

- deterministic
- fast
- isolated
- independent of unavailable external systems

Do not over-mock the entire system.

For critical integration behavior, use integration tests where the project supports them.

---

## External APIs

Do not perform unnecessary real external calls in normal tests.

Prefer existing mocking fixtures or test environments.

For external integrations, verify:

- request shape
- response handling
- error handling
- timeout behavior
- fallback behavior

---

## Database Testing

Respect the project's established database testing approach.

Potential strategies:

- isolated test database
- transactions
- fixtures
- mocks
- repositories with test doubles

Never modify production data during testing.

---

## Test Failures

When a test fails:

1. Read the failure.
2. Determine whether code, test, fixture, environment, or dependency caused it.
3. Reproduce if necessary.
4. Fix the root cause.
5. Re-run the failing test.
6. Run relevant broader tests.

Never blindly update expected output.

---

## Flaky Tests

Do not hide flaky tests.

Investigate:

- timing
- shared state
- ordering assumptions
- network behavior
- nondeterministic data
- process cleanup

Only change retries/timeouts when there is evidence that timing is the real issue.

---

## Test Quality

A strong test:

- has clear intent
- checks meaningful behavior
- fails when behavior regresses
- does not depend unnecessarily on implementation details
- is deterministic
- is maintainable

---

## Coverage

Coverage can be useful, but it is not proof of correctness.

A high coverage percentage can still miss important behavior.

Prioritize:

- critical paths
- business logic
- security-sensitive logic
- complex branches
- regression cases

---

## When Tests Do Not Exist

If the repository has no testing infrastructure:

1. Determine whether adding tests is appropriate.
2. Use existing validation mechanisms.
3. Consider adding focused tests for important new behavior if the task warrants it.
4. Do not build a large testing framework for a trivial change.

---

## Command Safety

Run test commands using the project's intended environment.

Respect:

- sandbox restrictions
- timeouts
- working directory
- resource limits

Do not run destructive commands merely to make a test pass.

---

## Reporting

Internally track:

```text
targeted tests: pass/fail
related tests: pass/fail/not run
full suite: pass/fail/not run
reason when not run
```

When reporting to the user, distinguish:

- verified
- partially verified
- not verified

Never claim tests passed if they were not actually executed.

---

## Completion Criteria

Testing is complete when the relevant behavior has been validated at an appropriate level and important regressions have been checked.

---

## Final Rule

**A test is evidence. Run the test that provides the evidence needed for the change.**