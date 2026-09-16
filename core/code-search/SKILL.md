# Code Search Skill

## Purpose

This skill defines how the agent should find relevant code efficiently and accurately.

The purpose of code search is not simply to locate matching text. It is to discover the implementation, callers, dependencies, definitions, side effects, and execution paths relevant to a task.

The agent should search progressively rather than scanning the entire repository unnecessarily.

---

## When to Use This Skill

Use this skill when:

- Locating functionality in an unfamiliar codebase.
- Finding where a feature is implemented.
- Debugging an issue.
- Tracing an API request.
- Finding references to a component/function/class.
- Determining where configuration is consumed.
- Understanding dependencies between files.
- Performing impact analysis before a change.

---

## Core Principle

**Search broadly first, then narrow through references.**

A search result is evidence that something exists.

It is not automatically evidence that the matching code is the code that executes.

Always inspect surrounding context and trace relevant references.

---

## Search Strategy

Use a layered strategy.

### Layer 1 — Concept Search

Search for task-specific terms.

For example:

```text
authentication
login
session
token
payment
checkout
dashboard
```

This identifies candidate locations.

---

### Layer 2 — Symbol Search

Search for likely:

- function names
- class names
- component names
- route names
- constants
- hooks
- services

Example:

```text
createSession
AuthProvider
/api/login
getUser
```

---

### Layer 3 — Reference Search

Find where the discovered symbol is:

- imported
- called
- rendered
- registered
- exported
- configured

This is especially important before changing shared functions.

---

### Layer 4 — Configuration Search

Search for:

- environment variables
- route registration
- feature flags
- package scripts
- configuration names

Example:

```text
DATABASE_URL
API_URL
ENABLE_AUTH
```

---

### Layer 5 — Test Search

Search for related tests.

Look for:

```text
*.test.*
*.spec.*
__tests__/
test/
tests/
```

Tests can reveal intended behavior.

---

## Search by Semantic Meaning

Do not depend solely on exact filenames.

A feature called "authentication" could be implemented under:

```text
auth/
security/
session/
middleware/
users/
services/
```

Search concepts and symbols rather than guessing paths.

---

## Read Context After Searching

Never modify a single matching line without understanding its surrounding code.

When a relevant match is found:

1. Read the containing function/component/class.
2. Read important imports.
3. Inspect callers when behavior is non-local.
4. Inspect error handling.
5. Inspect related tests.
6. Inspect configuration when relevant.

---

## Trace Execution

For important functionality, construct the execution path.

Example:

```text
Button
 → submit handler
 → API client
 → HTTP route
 → controller
 → service
 → database
```

or:

```text
CLI input
 → command parser
 → orchestrator
 → tool dispatcher
 → tool implementation
```

Use actual code evidence.

---

## Search for Side Effects

Before changing shared code, search for:

- mutations
- database writes
- filesystem writes
- network requests
- event emission
- caching
- global state changes
- logging
- retries

Shared functions may affect multiple features.

---

## Search for Duplicates

If a feature seems missing or broken, search for duplicate implementations.

Examples:

```text
login handler
two API clients
multiple config files
duplicate utility functions
old components
legacy routes
```

Do not automatically choose the first match.

Determine which implementation is actually active.

---

## Search for Dead Code

Search results may include:

- unused files
- deprecated implementations
- backup files
- generated artifacts
- examples
- documentation
- tests for old behavior

Do not assume a result is active code.

Check import/reference relationships.

---

## Search Tool Failure

If preferred search mechanisms are unavailable:

- Use available file listing/search tools.
- Narrow by directory.
- Use command-line search when appropriate.
- Avoid brute-force reading every file.

A search failure must not cause the agent to fabricate results.

---

## Handling Large Repositories

Large repositories require scoped search.

Prefer:

```text
src/
server/
app/
packages/relevant-package/
```

over repository-wide recursive inspection whenever enough context is known.

Search:

1. filenames
2. exact symbols
3. related concepts
4. references
5. tests

---

## Dependency Search

When modifying a shared function, search for all consumers.

For example:

```text
validateUser()
```

Search:

```text
validateUser(
```

and imports/re-exports.

Determine whether the function has:

- one caller
- multiple callers
- public API usage
- test-only usage
- backward compatibility requirements

---

## API Search

For API-related tasks, search for:

- route declarations
- controller/handler
- request validation
- response construction
- API client usage
- error handling
- tests

Do not modify only the frontend or only the backend without checking the contract when the task crosses both layers.

---

## Search Results Are Not Enough

A valid search workflow is:

```text
Search
 ↓
Identify candidates
 ↓
Read implementation
 ↓
Trace references
 ↓
Understand behavior
 ↓
Modify relevant location
```

Not:

```text
Search
 ↓
Edit first result
```

---

## Avoid Search Loops

Stop searching when enough evidence exists.

Continue searching when:

- behavior is ambiguous
- multiple implementations exist
- a shared symbol has many consumers
- the execution path is unclear
- tests contradict the implementation
- configuration changes behavior

---

## Completion Criteria

Code search is complete when the agent knows:

- where the relevant implementation is
- how it is reached
- what depends on it
- what tests cover it
- what configuration affects it
- which files should change

---

## Final Rule

**Search to understand relationships, not merely to find strings.**