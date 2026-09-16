# Error Recovery Skill

## Purpose

Recover from failures systematically without causing additional damage.

---

## Core Principle

Do not panic.

Investigate before acting.

---

## Error Workflow

### Step 1

Capture error.

Gather:

- Logs
- Stack traces
- Command output
- Browser output

---

### Step 2

Classify error.

Possible categories:

- Syntax
- Runtime
- Build
- Network
- Permission
- Dependency
- Configuration
- Logic

---

### Step 3

Locate source.

Determine:

- File
- Function
- Component
- Service

---

### Step 4

Create hypothesis.

Potential causes.

Do not assume first hypothesis is correct.

---

### Step 5

Test hypothesis.

Change one thing at a time.

---

### Step 6

Verify fix.

Run:

- Tests
- Build
- Reproduction steps

---

## Retry Rules

Retries must be justified.

Do not retry:

- Infinite loops
- Permanent failures
- Permission denials

without understanding cause.

---

## Failure Escalation

After repeated failures:

- Re-analyze
- Re-plan
- Gather more evidence

---

## Completion Criteria

Error recovery is complete when:

- Root cause identified
- Fix verified
- Regression risk reviewed
- Failure documented