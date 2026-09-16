# Self Review Skill

## Purpose

This skill defines how the agent should critically inspect its own changes before declaring a task complete.

The purpose is to catch defects that basic testing may miss, including unintended edits, incomplete integration, poor error handling, security problems, unnecessary complexity, and mismatch with the user's request.

---

## When to Use This Skill

Use this skill:

- After implementing a feature.
- After fixing a bug.
- Before a commit.
- Before deployment.
- Before reporting task completion.
- After substantial changes.
- After recovery from a failed model/provider turn.

---

## Core Principle

**Review the result as though another engineer will have to maintain it.**

Do not assume your own previous reasoning was correct.

---

## Review Workflow

Use:

```text
Re-read request
 ↓
Inspect diff
 ↓
Check behavior
 ↓
Check integration
 ↓
Check errors
 ↓
Check security
 ↓
Check tests/build
 ↓
Check unintended changes
 ↓
Determine completion status
```

---

## Step 1 — Re-read the User's Request

Compare implementation against the actual requested outcome.

Ask:

- Did I implement the requested feature?
- Did I solve the requested problem?
- Did I preserve explicitly stated constraints?
- Did I avoid adding unrelated behavior?
- Did I miss any acceptance criteria?

Do not substitute a different interpretation merely because it was easier to implement.

---

## Step 2 — Inspect the Diff

Use Git diff or equivalent workspace comparison.

Check:

- modified files
- new files
- deleted files
- suspiciously large changes
- formatting-only changes
- unrelated modifications

Large diffs require explanation.

A task that should change two files should not accidentally modify fifty.

---

## Step 3 — Review Correctness

Inspect changed code for:

- logic errors
- incorrect assumptions
- missing branches
- invalid state handling
- wrong return values
- incorrect API contracts
- race conditions
- async mistakes
- error propagation problems

---

## Step 4 — Review Integration

Ask:

```text
Is the new code actually connected?
Are callers updated?
Are routes registered?
Are imports correct?
Are configuration values available?
Does the UI call the correct API?
Does the backend return what the client expects?
```

A feature that exists but is not wired into the application is incomplete.

---

## Step 5 — Review Error Handling

For every meaningful failure path:

- Is the error caught where appropriate?
- Is it propagated correctly?
- Is invalid input handled?
- Is external failure handled?
- Does the system avoid fake success?
- Are useful diagnostics preserved?

---

## Step 6 — Review Security

Look for:

- hardcoded credentials
- secret leakage
- unsafe shell construction
- path traversal
- uncontrolled input
- missing validation
- authentication bypass
- authorization mistakes
- insecure defaults

Do not dismiss security concerns simply because the feature works.

---

## Step 7 — Review Data Handling

Check:

- nullability
- validation
- serialization
- parsing
- persistence
- unexpected external responses

Pay particular attention to user-controlled input.

---

## Step 8 — Review Performance

Look for obvious problems such as:

- unnecessary repeated API calls
- repeated expensive computation
- large unbounded loops
- excessive file operations
- accidental duplicate requests
- loading enormous data unnecessarily

Do not perform speculative micro-optimization.

---

## Step 9 — Review Maintainability

Ask:

- Are names clear?
- Is control flow understandable?
- Is duplication introduced?
- Is abstraction justified?
- Does the code match existing project conventions?

Prefer understandable code over clever code.

---

## Step 10 — Check Tests and Build

Confirm that appropriate validation was actually run.

Distinguish:

```text
passed
failed
not run
not applicable
```

Never convert "not run" into "passed" mentally.

---

## Existing Changes

Do not treat pre-existing user changes as your own.

Separate:

```text
before task
```

from:

```text
changes introduced by this task
```

when analyzing the diff.

---

## Incomplete Work Detection

Look for:

```text
TODO
FIXME
placeholder
mock
dummy data
temporary workaround
unreachable branch
console.log
debugging code
```

These are not automatically problems, but verify that they are intentional.

---

## Agent Self-Critique

Ask:

> What assumption could be wrong?

Examples:

- assumed environment variable exists
- assumed endpoint is available
- assumed package supports an API
- assumed a file is unused
- assumed a provider response has a certain shape
- assumed deployment uses a certain command

Verify important assumptions against actual project evidence.

---

## Review Severity

Categorize findings internally as:

### Blocking

Task cannot honestly be considered complete.

Examples:

- build failure
- core feature broken
- security defect introduced
- requested functionality missing

### Important

Should be fixed before completion where feasible.

Examples:

- regression risk
- missing meaningful test
- incorrect edge-case behavior

### Minor

Does not prevent completion but may improve maintainability.

Examples:

- naming improvement
- non-critical refactor opportunity

Do not inflate minor issues into blockers.

---

## Fixing Review Findings

If a blocking or important issue is found:

1. fix it
2. re-run relevant validation
3. inspect the updated diff again

Self-review is iterative.

---

## Completion Criteria

Self-review is complete when:

- requested behavior has been checked
- diff has been inspected
- integration has been checked
- security has been considered
- error handling has been checked
- tests/build have been assessed
- no known blocking defect remains

---

## Final Rule

**Never let "I wrote the code" substitute for "I reviewed the result."**