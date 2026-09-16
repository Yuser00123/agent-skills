# Completion Verification Skill

## Purpose

This skill defines the final verification process that determines whether the agent may truthfully report a task as complete.

This is the final gate between implementation work and a completion claim.

---

## When to Use This Skill

Use this skill:

- Before telling the user a task is complete.
- Before creating a final commit.
- Before deployment completion is reported.
- After tool execution.
- After model fallback/recovery.
- After a long autonomous task.

---

## Core Principle

**Completion must be evidence-based.**

The agent must not say:

- "Done"
- "Fixed"
- "Working"
- "Successfully deployed"
- "Tests pass"

unless the corresponding evidence exists.

---

## Completion Levels

Determine the applicable level.

### Level 1 — File Change Verified

The requested files were successfully modified.

This is insufficient for most software tasks.

### Level 2 — Behavior Verified

The requested behavior was actually tested.

### Level 3 — Integration Verified

Relevant surrounding systems were also validated.

### Level 4 — Build/Deployment Verified

The project successfully passed the relevant build/deployment verification.

Only claim the level actually achieved.

---

## Verification Workflow

Use:

```text
User requirements
 ↓
Changed files
 ↓
Expected behavior
 ↓
Targeted test
 ↓
Related tests
 ↓
Build
 ↓
Deployment check when relevant
 ↓
Final diff review
 ↓
Completion decision
```

Not every task requires every step, but each skipped stage should be intentional.

---

## Requirement Checklist

Convert the user's request into observable outcomes.

Example:

```text
Requirement 1 → verified
Requirement 2 → verified
Requirement 3 → not verified
```

Do not mark a requirement verified merely because code appears related to it.

---

## Verify Actual Behavior

Prefer direct evidence.

For an API:

```text
call endpoint
inspect response
```

For a UI:

```text
run application
perform relevant action
observe result
```

For a script:

```text
execute script
inspect output/status
```

For a build:

```text
run build
inspect exit status
```

---

## Tool Result Verification

Every important tool action should be interpreted according to its actual result.

Examples:

A file-write tool succeeding means:

> The file was written.

It does not mean:

> The feature works.

A deployment command returning a URL does not automatically prove:

> The deployment is healthy.

A test command returning output must be checked for actual status.

---

## Null or Missing Results

If a tool reports:

```text
url: null
```

the agent must not invent a shareable URL.

Instead report that the file or result was created/saved but no shareable URL was provided.

This rule is especially important for generated artifacts.

---

## Fallback/Provider Recovery

When execution changes model/provider during a task, do not treat the previous model's textual progress note as authoritative.

Re-check workspace state.

Verify:

- which files actually exist
- current file contents
- current Git diff
- test/build status

Then continue.

---

## Autonomous Tool Loop Limit

If the agent reaches its tool-call/loop limit before completing verification:

Do not report unconditional success.

Report that work may be incomplete or verification was not completed.

The agent should distinguish:

```text
implementation complete
```

from:

```text
implementation + verification complete
```

---

## Deployment Verification

For deployment tasks, distinguish:

```text
deployment command succeeded
```

from:

```text
deployed application is reachable and functioning
```

Where practical verify:

- URL availability
- expected route
- HTTP response
- basic application health
- relevant feature

Do not perform destructive production checks.

---

## Git Verification

Before claiming a change is complete, inspect:

```text
git diff
git status
```

when relevant.

Ensure:

- expected files changed
- no obvious accidental files were modified
- generated secrets were not added
- intended files are present

---

## Tests and Build

Record actual status:

```text
Tests: PASS
Build: PASS
```

only when actually executed and successful.

Otherwise:

```text
Tests: NOT RUN
Build: NOT RUN
```

or:

```text
Tests: FAIL
```

with explanation.

---

## Verification Failure

If verification fails:

1. Do not claim completion.
2. Diagnose the failure.
3. Fix when within scope.
4. Re-run verification.
5. If unresolved, clearly state what remains unresolved.

---

## Completion Decision

The agent may report full completion when:

- requested requirements are implemented
- relevant behavior is verified
- important tests pass
- relevant build checks pass where applicable
- no known blocking defect remains
- final workspace state is understood

---

## User-Facing Completion Statement

A strong completion report should communicate:

```text
What changed
What was verified
Important validation results
Any remaining limitation
```

Avoid unnecessary internal reasoning.

---

## Final Rule

**Completion is a verified state, not a feeling.**