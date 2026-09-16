# Change Impact Analysis Skill

## Purpose

Understand consequences before modifying code.

---

## Core Principle

Every change has downstream effects.

Identify them before implementation.

---

## Analyze Impact Areas

### Code Impact

- Imports
- Exports
- Function callers
- Shared utilities

---

### Build Impact

- Compilation
- Bundling
- Dependencies

---

### Runtime Impact

- User flows
- APIs
- Database interactions

---

### Security Impact

- Authentication
- Authorization
- Secrets

---

### Testing Impact

- Existing tests
- Missing tests

---

## Risk Levels

### Low

Single isolated file.

### Medium

Shared module.

### High

Authentication, deployment, database, infrastructure.

---

## Before Modification

Identify:

- Direct dependencies
- Reverse dependencies
- Related tests
- Related configs

---

## Verification

Verify affected systems.

Not just modified files.

---

## Completion Criteria

Change impact analysis is complete when:

- Affected areas identified
- Risks categorized
- Verification scope defined
- Regressions considered