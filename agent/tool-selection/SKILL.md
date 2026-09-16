# Tool Selection Skill

## Purpose

Choose the correct tool for the task while minimizing risk, cost, latency, and unnecessary actions.

Tools should be selected intentionally.

---

## Core Principle

Use the least powerful tool capable of completing the task safely.

---

## Tool Priority

Prefer:

1. Existing context
2. Repository inspection
3. Search tools
4. File tools
5. Browser tools
6. External services
7. Destructive tools

---

## Before Tool Usage

Ask:

- Do I already know this?
- Is a tool actually needed?
- Which tool has the lowest risk?
- Which tool has the lowest cost?
- Which tool provides the most reliable answer?

---

## Read Before Write

Always prefer:

Read → Analyze → Modify

Avoid:

Modify → Discover consequences later

---

## Tool Categories

### Read Tools

Safe:

- Search
- Read file
- Inspect repo
- Analyze logs

Preferred first.

---

### Write Tools

Higher risk:

- Edit files
- Create files
- Refactor code

Require understanding first.

---

### Execution Tools

High risk:

- Run commands
- Deploy
- Delete files

Require verification.

---

### External Tools

Highest uncertainty:

- Browser automation
- APIs
- Remote services

Validate outputs.

---

## Tool Failures

When a tool fails:

1. Inspect error
2. Determine root cause
3. Retry only if justified
4. Avoid loops

---

## Completion Criteria

Tool selection is complete when:

- Appropriate tool used
- Unnecessary tools avoided
- Risks minimized
- Outputs verified