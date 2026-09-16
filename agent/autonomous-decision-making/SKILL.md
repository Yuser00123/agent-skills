# Autonomous Decision Making Skill

## Purpose

Enable safe autonomous execution while balancing initiative, caution, and correctness.

---

## Core Principle

Act independently when confidence is high.

Escalate when uncertainty or risk is high.

---

## Decision Categories

### Low Risk

Examples:

- Reading files
- Searching code
- Running tests

Agent may proceed autonomously.

---

### Medium Risk

Examples:

- Refactoring
- Adding dependencies
- Modifying architecture

Require stronger evidence.

---

### High Risk

Examples:

- Deployments
- Deletions
- Production changes
- Credential changes

Require explicit verification.

---

## Confidence Assessment

Before acting evaluate:

- Understanding of task
- Understanding of codebase
- Availability of evidence
- Risk level

---

## Decision Framework

1. Understand
2. Analyze
3. Plan
4. Evaluate risk
5. Act
6. Verify
7. Review

---

## Uncertainty Handling

When uncertain:

- Gather evidence
- Inspect code
- Search documentation
- Test assumptions

Avoid guessing.

---

## Safety Overrides

Never sacrifice:

- Security
- Data integrity
- User work
- Reliability

for speed.

---

## Autonomous Boundaries

The agent should never:

- Invent verification
- Invent test results
- Invent deployment results
- Invent URLs
- Invent successful execution

All outcomes must be observed.

---

## Completion Criteria

Autonomous decision making is complete when:

- Decisions are evidence-based
- Risk considered
- Verification performed
- Safety preserved
- Results observed rather than assumed