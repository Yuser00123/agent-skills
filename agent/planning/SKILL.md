# Planning Skill

## Purpose

Create structured execution plans before making significant changes.

The objective is to avoid random tool usage, premature coding, and unnecessary modifications.

The agent should understand the task before acting.

---

## When To Use

Use this skill when:

- Starting a new task
- Implementing features
- Fixing bugs
- Refactoring
- Deploying applications
- Investigating failures
- Working across multiple files
- Performing autonomous work

---

## Core Principle

Think before acting.

A good plan reduces:

- Rework
- Mistakes
- Tool calls
- Context waste
- Risk

---

## Planning Workflow

### Phase 1: Understand

Identify:

- User objective
- Constraints
- Technologies involved
- Success criteria
- Unknowns

Do not assume requirements.

---

### Phase 2: Analyze

Determine:

- Files involved
- Components involved
- Dependencies involved
- Potential risks
- Testing requirements

---

### Phase 3: Create Plan

Break work into steps.

Example:

1. Analyze repository
2. Locate authentication flow
3. Implement feature
4. Add tests
5. Run verification
6. Self-review

---

### Phase 4: Execute

Execute one step at a time.

Re-evaluate after each major step.

---

### Phase 5: Verify

Confirm:

- Goal achieved
- Tests passed
- Build passes
- No regressions

---

## Plan Quality

Good plans are:

- Specific
- Ordered
- Testable
- Minimal

Bad plans are:

- Vague
- Huge
- Unverifiable

---

## Replanning

Replan whenever:

- New information appears
- A step fails
- Requirements change
- Context changes

Never continue blindly after a major assumption fails.

---

## Completion Criteria

Planning is complete when:

- Goal is understood
- Risks identified
- Execution path exists
- Verification strategy exists
- Plan remains relevant