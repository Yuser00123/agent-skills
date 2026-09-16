# Repo Analysis Skill

## Purpose

This skill defines how the agent should understand an existing repository before modifying it.

The objective is to build an accurate mental model of the project before making changes. The agent must understand the repository's structure, technology stack, important entry points, configuration, dependencies, scripts, data flow, and existing conventions before performing substantial implementation work.

Repo analysis should minimize unnecessary exploration while gathering enough information to make safe decisions.

---

## When to Use This Skill

Use this skill when:

- Beginning work on an unfamiliar repository.
- A task requires modifying existing code.
- A bug appears in a project whose architecture is not yet understood.
- The user asks for a feature that may interact with multiple parts of the codebase.
- The project has multiple applications, packages, services, or deployment targets.
- A previous agent/model has already made changes and the current agent needs to understand the resulting state.
- The task involves dependencies, build configuration, deployment configuration, or architectural changes.

Do not perform a full repository analysis for a trivial change when the relevant file and context are already known.

---

## Core Principle

**Understand before changing.**

Never assume a repository follows a standard framework structure.

Determine the actual structure from the repository itself.

Do not invent files, packages, scripts, frameworks, APIs, or conventions that have not been verified.

---

## Initial Analysis Workflow

### Step 1 — Establish Workspace

Determine:

- Current project directory.
- Repository root.
- Whether the directory is a Git repository.
- Whether the project appears to be a monorepo.
- Whether there are nested applications or packages.

Prefer the agent's configured project directory over arbitrary working directories.

---

### Step 2 — Inspect Top-Level Structure

Start with a shallow file listing.

Look for:

- `package.json`
- `pnpm-lock.yaml`
- `package-lock.json`
- `yarn.lock`
- `bun.lockb`
- `requirements.txt`
- `pyproject.toml`
- `go.mod`
- `Cargo.toml`
- `pom.xml`
- `build.gradle`
- `Dockerfile`
- `.gitignore`
- `.env.example`
- `README.md`
- framework configuration files
- deployment configuration
- CI configuration
- workspace configuration
- source directories
- test directories

Do not immediately recursively inspect the entire repository.

---

## Step 3 — Identify Technology Stack

Determine the actual:

- Programming language(s).
- Framework(s).
- Runtime(s).
- Package manager.
- Build system.
- Testing framework.
- Linter/formatter.
- Database or storage system.
- Authentication system.
- Deployment platform.
- External services.

Use repository evidence.

For example, do not assume a React project is Next.js merely because React is installed.

---

## Step 4 — Read Project Metadata

Inspect the most relevant metadata files.

For JavaScript/TypeScript projects, usually inspect:

1. `package.json`
2. lockfile
3. framework configuration
4. TypeScript configuration
5. build configuration
6. environment example files

Pay particular attention to:

- scripts
- dependencies
- dev dependencies
- package manager constraints
- Node version
- build commands
- test commands
- lint commands
- start commands
- deployment scripts

---

## Step 5 — Locate Entry Points

Identify the application's main execution paths.

Examples:

```text
src/main.*
src/index.*
src/App.*
app/
pages/
server.*
index.*
api/
routes/
```

For backend services identify:

- application entry point
- routing
- middleware
- configuration
- services
- storage
- external integrations

For frontend applications identify:

- application entry point
- routing
- major layouts
- state management
- API layer
- component hierarchy

---

## Step 6 — Identify Architecture

Build a concise architecture model.

Determine relationships such as:

```text
UI
 ↓
State
 ↓
API client
 ↓
Backend
 ↓
Database
```

or:

```text
HTTP request
 ↓
Express route
 ↓
Service
 ↓
Repository
 ↓
Database
```

Do not create an architecture document unless requested.

The architecture model can remain internal to task execution.

---

## Step 7 — Trace Relevant Code

Once the user's task is understood, narrow analysis to the relevant subsystem.

For example, for an authentication bug:

```text
login UI
 → authentication handler
 → API route
 → auth service
 → token/session generation
 → persistence
```

Do not modify code based solely on filenames.

Read enough surrounding code to understand dependencies and side effects.

---

## Step 8 — Check Existing Conventions

Look for conventions involving:

- naming
- folder structure
- error handling
- logging
- API responses
- state management
- component style
- testing
- comments
- imports
- asynchronous patterns
- validation
- environment variables

Follow existing good conventions unless the task explicitly requires changing them.

---

## Repository Analysis Output

Before implementation, internally answer:

```text
Project type:
Primary framework:
Runtime:
Package manager:
Entry points:
Relevant subsystem:
Build command:
Test command:
Lint command:
Deployment target:
Important configuration:
Important constraints:
```

Do not report all of this to the user unless useful.

---

## Monorepo Rules

If the repository contains multiple applications/packages:

- Identify workspace configuration.
- Determine which package owns the affected code.
- Determine dependency boundaries.
- Avoid modifying unrelated packages.
- Run validation from the correct package or workspace root.

Examples include:

```text
apps/
packages/
services/
libs/
```

Do not assume every package shares the same scripts.

---

## Configuration Analysis

Treat configuration as code.

Inspect relevant:

- `.env.example`
- config files
- deployment files
- CI files
- framework configuration
- TypeScript configuration
- lint configuration
- test configuration

Never expose actual secret values in output.

---

## Generated and Vendor Files

Do not casually modify:

- `node_modules`
- build output
- generated files
- caches
- coverage output
- lockfiles unrelated to the change
- vendored dependencies

Determine whether a generated file is source-controlled before modifying it.

Prefer modifying the source that generates the artifact.

---

## Git State Awareness

Before significant changes, inspect:

```text
git status
```

Determine:

- existing modified files
- staged files
- untracked files
- current branch
- recent commits when relevant

Do not overwrite or discard pre-existing user changes.

A user's uncommitted work is part of the workspace state.

---

## Existing User Changes

When unrelated modifications already exist:

- Preserve them.
- Do not reset the repository.
- Do not use destructive commands to create a "clean" workspace.
- Avoid broad formatting that touches unrelated files.

Only modify files required for the requested task.

---

## Analysis Depth

Use proportional analysis.

### Small change

Example:

> Change button text.

Inspect only relevant file/context.

### Medium change

Example:

> Add a settings page.

Inspect:

- routes
- application layout
- related components
- styling conventions
- API/state layer if needed
- test setup

### Large change

Example:

> Add authentication.

Inspect the relevant architecture broadly before implementation.

---

## Anti-Patterns

Do not:

- recursively read every file by default
- assume framework conventions without checking
- rewrite architecture unnecessarily
- change dependencies before understanding current dependencies
- inspect unrelated directories indefinitely
- delete files merely because they look unused
- reset user modifications
- fabricate an understanding of undocumented behavior

---

## Handoff to Other Skills

Repo Analysis frequently precedes:

- Code Search
- Coding
- Debugging
- Testing
- Build Verification
- Self Review

After sufficient analysis, use the most task-specific skill instead of continuing to explore.

---

## Completion Criteria

Repo analysis is sufficient when the agent can answer:

1. What kind of project is this?
2. Where does the relevant code live?
3. How does the relevant flow work?
4. What files are likely to change?
5. What existing conventions must be preserved?
6. How can the change be validated?
7. What constraints or risks exist?

If these questions cannot be answered, continue targeted analysis.

---

## Final Rule

**Never make a substantial change to an unfamiliar repository without first understanding the relevant architecture and execution path.**