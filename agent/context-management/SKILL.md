# Context Management Skill

## Purpose

Maintain relevant knowledge throughout execution while preventing context overflow and confusion.

---

## Core Principle

Important information should persist.

Irrelevant information should not.

---

## Context Types

### Task Context

Current goal.

Examples:

- Fix bug
- Deploy app
- Add feature

---

### Repository Context

- Framework
- Structure
- Dependencies
- Architecture

---

### Execution Context

- Current step
- Completed steps
- Pending steps
- Failures

---

## Context Collection

Gather:

- Requirements
- Constraints
- File locations
- Test results
- Build results

Avoid collecting unnecessary details.

---

## Context Prioritization

Keep:

- Active task
- Current files
- Current errors
- Current plan

Discard:

- Old irrelevant observations
- Superseded assumptions

---

## Context Updates

Update context when:

- File changes
- Tests fail
- Requirements change
- New evidence appears

---

## Assumptions

Track assumptions explicitly.

Examples:

- API likely returns JSON
- Build tool appears to be Vite

Assumptions are not facts.

---

## Completion Criteria

Context management is complete when:

- Relevant information retained
- Outdated information removed
- Assumptions tracked
- Current state known