# Debugging Skill

## Purpose

This skill defines a disciplined process for diagnosing and fixing software failures.

The objective is to identify the root cause of a problem and make a targeted correction rather than repeatedly changing code until an error disappears.

---

## When to Use This Skill

Use this skill when:

- The application throws an error.
- A test fails.
- A build fails.
- A feature behaves incorrectly.
- An API returns unexpected results.
- A deployment fails.
- A runtime crash occurs.
- The user reports incorrect behavior.
- A previous change caused a regression.

---

## Core Principle

**Reproduce → Observe → Isolate → Hypothesize → Test → Fix → Verify**

Never begin with random edits.

---

## Step 1 — Reproduce the Problem

First determine whether the failure can be reproduced.

Gather:

- exact error message
- command or action that triggers it
- relevant inputs
- environment
- expected behavior
- actual behavior

If reproduction is impossible, identify what evidence is available instead.

Never claim successful reproduction when it was not actually reproduced.

---

## Step 2 — Capture the Failure

Preserve the useful details of the failure.

Examples:

```text
error type
stack trace
HTTP status
response body
test output
build output
browser console
server logs
```

Do not expose secrets or credentials while reporting diagnostic information.

---

## Step 3 — Locate the Failure Layer

Determine whether the problem is primarily in:

```text
UI
 ↓
client state
 ↓
API request
 ↓
server
 ↓
service
 ↓
database
 ↓
external provider
```

or another execution layer.

Do not fix the first visible symptom before determining which layer actually fails.

---

## Step 4 — Form a Hypothesis

Create a specific hypothesis.

Example:

> The frontend receives an empty response because the API route returns before awaiting the asynchronous database operation.

A good hypothesis should be testable.

Avoid vague reasoning such as:

> Something is wrong with the API.

---

## Step 5 — Gather Evidence

Use:

- Code Search
- relevant file reads
- logs
- tests
- targeted commands
- request/response inspection
- configuration inspection

Compare actual behavior with expected behavior.

---

## Step 6 — Check Recent Changes

When appropriate, inspect:

- Git diff
- recently modified files
- recent commits
- dependency changes
- configuration changes

A regression often has a recent cause, but do not assume that the newest change is automatically responsible.

---

## Step 7 — Narrow the Failure

Reduce the problem to the smallest failing unit.

Examples:

Instead of:

> The dashboard doesn't work.

Determine:

> Dashboard request succeeds, but `/api/profile` returns HTTP 500.

Then:

> The route reaches `getProfile()`, which throws because `userId` is undefined.

This makes the repair tractable.

---

## Step 8 — Test the Hypothesis

Make the smallest diagnostic change or run a targeted experiment.

Examples:

- call a function with controlled input
- inspect a variable
- execute the failing API directly
- run a specific test
- inspect generated configuration
- check whether a file exists
- confirm environment configuration

Do not introduce a permanent code change merely to test a theory unless appropriate.

---

## Step 9 — Fix the Root Cause

Once confirmed:

- patch the actual source of failure
- preserve unrelated behavior
- avoid unnecessary rewrites
- avoid hiding the error
- maintain appropriate validation

---

## Step 10 — Verify the Fix

Repeat the failing scenario.

Then run broader validation appropriate to the change:

```text
targeted test
 → related tests
 → build
 → broader tests if needed
```

A fix is incomplete if the original failure was never rechecked.

---

## Regression Checks

After fixing a shared component, test important surrounding behavior.

For example:

```text
shared authentication utility
```

may affect:

- login
- logout
- session restoration
- protected routes
- API authorization

Do not assume one passing test proves the entire subsystem is correct.

---

## Debugging Logs

Use logs carefully.

Prefer logs that identify:

```text
operation
stage
identifier
error type
```

without revealing:

```text
password
API key
token
session secret
personal sensitive data
```

Remove temporary diagnostic logs when no longer useful unless they are intentionally part of the final implementation.

---

## Build Failures

When a build fails:

1. Read the first meaningful failure.
2. Identify whether it is syntax, type, dependency, configuration, or environment related.
3. Fix the underlying issue.
4. Re-run the build.
5. Check for subsequent errors.

Do not chase every secondary error before resolving the primary failure.

---

## Test Failures

Distinguish:

- product bug
- incorrect test
- environment issue
- fixture issue
- dependency issue
- flaky test

Never modify a test solely to make it pass unless the original expectation is demonstrably wrong.

---

## External Service Failures

For API/provider failures, determine whether the cause is:

- authentication
- rate limit
- invalid request
- unsupported model/endpoint
- network failure
- provider outage
- malformed response
- application bug

Do not automatically switch providers and declare the problem solved.

---

## Intermittent Failures

For flaky failures, investigate:

- race conditions
- timing
- concurrency
- retries
- shared state
- network dependency
- nondeterministic test data
- process lifecycle

Avoid increasing arbitrary timeouts as the first response.

---

## Recovery After Failed Attempts

If previous fixes failed:

1. Review what actually changed.
2. Determine what evidence disproved the prior hypothesis.
3. Return to the last known-good behavior.
4. Form a new evidence-based hypothesis.
5. Avoid repeating identical changes.

---

## Do Not Hide Failures

Never fix a problem by:

- swallowing exceptions
- returning fake success
- disabling tests
- weakening validation
- deleting failing tests
- suppressing all logs
- bypassing authentication
- increasing retries indefinitely

unless explicitly required and properly justified.

---

## Completion Criteria

A debugging task is ready for completion when:

- the failure was reproduced or sufficiently characterized
- the root cause was identified with evidence
- a targeted fix was applied
- the original failure no longer occurs
- relevant regression checks pass
- no unrelated behavior was unnecessarily altered

---

## Final Rule

**Do not confuse disappearance of an error with resolution of the bug. Prove the root cause and verify the corrected behavior.**