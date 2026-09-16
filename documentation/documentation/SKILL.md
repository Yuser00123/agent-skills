# Documentation Skill

## Purpose

Create and maintain documentation that accurately explains how the project works, how it is used, configured, tested, deployed, and maintained.

Documentation should describe reality rather than intended or imagined behavior.

---

## When to Use

Use this skill when:

- Creating a README
- Adding setup instructions
- Documenting APIs
- Documenting architecture
- Documenting configuration
- Documenting deployment
- Adding code comments
- Writing contribution instructions
- Updating documentation after implementation changes

---

## Documentation Principles

Documentation should be:

- Accurate
- Current
- Concise where possible
- Structured
- Discoverable
- Actionable

Do not document behavior that the code does not actually implement.

---

## Before Writing

Inspect:

- Project structure
- Package configuration
- Environment configuration
- Scripts
- Entry points
- Deployment configuration
- Relevant source code

Use the actual project as the source of truth.

---

## README

A useful README may contain:

- Project purpose
- Key features
- Technology stack
- Prerequisites
- Installation
- Configuration
- Development
- Testing
- Build
- Deployment
- Usage
- Project structure
- Troubleshooting where useful

Do not add sections merely to increase README length.

---

## Installation Instructions

Ensure commands are:

- Correct
- Compatible with the package manager
- In the correct order
- Consistent with the current project

Do not copy stale setup commands from older project versions.

---

## Environment Variables

Document:

- Variable name
- Purpose
- Required/optional status
- Example placeholder where appropriate

Never place real secrets in documentation.

Example:

```text
API_KEY=your_api_key_here
```

---

## Architecture Documentation

When documenting architecture:

Explain:

- Major components
- Data flow
- External integrations
- Important boundaries
- Runtime relationships

Keep diagrams and explanations synchronized with actual architecture.

---

## Code Comments

Comments should explain:

- Why something exists
- Why an unusual approach was chosen
- Important constraints
- Non-obvious behavior

Avoid comments that merely restate obvious code.

Bad:

```js
// Increment counter
counter++;
```

Better:

```js
// Keep the retry count separate from request count because retries are bounded independently.
retryCount++;
```

---

## API Documentation

Document:

- Endpoint or operation
- Inputs
- Outputs
- Authentication requirements
- Errors
- Important constraints

Keep examples consistent with the actual API.

---

## Deployment Documentation

Document:

- Hosting platform
- Required configuration
- Build/deployment commands
- Environment setup
- Verification
- Important limitations

Do not claim that a deployment process is automatic unless it actually is.

---

## Updating Documentation

When implementation changes:

1. Identify affected documentation.
2. Update only what is now incorrect or incomplete.
3. Search for stale references.
4. Check commands/examples.
5. Review for contradictions.

Documentation drift is a maintenance bug.

---

## Accuracy

Never invent:

- Commands
- Configuration variables
- APIs
- URLs
- Features
- Architecture components
- Deployment behavior

When information is unknown, inspect the project or clearly mark the limitation.

---

## Completion Criteria

Documentation is complete when:

- Important user/developer workflows are documented.
- Instructions reflect the current implementation.
- Examples are valid.
- Secrets are not exposed.
- Stale or contradictory information has been addressed.
- A new developer can reasonably follow the documented workflow.