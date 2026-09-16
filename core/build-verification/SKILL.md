# Build Verification Skill

## Purpose

This skill defines how the agent verifies that a project can successfully build or otherwise pass its project's required compilation/packaging checks after changes.

A successful file edit does not imply a successful build.

---

## When to Use This Skill

Use this skill when:

- Code has been changed.
- Dependencies changed.
- Configuration changed.
- TypeScript or compiled code changed.
- Frontend components changed.
- Deployment preparation is required.
- The project's normal workflow includes a build step.
- A user reports build/deployment problems.

---

## Core Principle

**The actual build system is the source of truth.**

Do not infer build success from syntax inspection alone.

---

## Identify the Build Process

Before running a build:

Inspect:

- `package.json` scripts
- project documentation
- framework configuration
- build configuration
- workspace/monorepo configuration
- language-specific build files

Determine the correct command.

Examples may include:

```text
npm run build
pnpm build
yarn build
npm run typecheck
python -m ...
cargo build
go build ./...
```

Do not assume one command applies to every project.

---

## Build Environment

Determine:

- required runtime
- package manager
- installed dependencies
- environment variables
- build-specific configuration
- workspace/package location

If the build requires secrets, use the established environment mechanism.

Never print secret values.

---

## Before Building

Check:

```text
git status
```

and understand whether there are existing changes.

Ensure dependencies are available.

Do not automatically delete dependency directories or lockfiles.

---

## Build Workflow

Use:

```text
Inspect build configuration
 ↓
Run targeted validation if useful
 ↓
Run project build
 ↓
Read actual result
 ↓
Diagnose failures
 ↓
Fix root cause
 ↓
Re-run build
```

---

## Build Failure Classification

Classify failures as:

### Syntax/Parsing

Examples:

- malformed syntax
- missing bracket
- invalid import

### Type/Compilation

Examples:

- type mismatch
- missing symbol
- compile error

### Dependency

Examples:

- package missing
- incompatible version
- dependency resolution failure

### Configuration

Examples:

- invalid framework configuration
- missing environment variable
- unsupported option

### Runtime During Build

Examples:

- static generation failure
- server-side rendering failure
- build-time API call failure

### Environment

Examples:

- wrong runtime
- unavailable binary
- permission issue
- sandbox limitation

---

## Fixing Build Errors

Use the first meaningful failure to identify the root cause.

Avoid making many speculative fixes at once.

Recommended process:

```text
Build
 ↓
Identify first root error
 ↓
Inspect relevant source
 ↓
Patch
 ↓
Build again
```

---

## Monorepo Builds

In a monorepo:

- determine affected package
- determine workspace-level dependencies
- run package-level validation when appropriate
- run root-level build when required

Do not accidentally build unrelated applications if doing so consumes significant resources and is unnecessary.

---

## Type Checking

For TypeScript or statically typed projects, type checking may be a separate verification step.

Do not rely solely on successful bundling if the project convention includes an independent type-check command.

---

## Production vs Development Build

Distinguish:

```text
development server
```

from:

```text
production build
```

A project running successfully in development may still fail production compilation or static generation.

Use the project's actual deployment/build process when verifying deployability.

---

## Generated Files

If the build generates:

```text
dist/
build/
.next/
out/
coverage/
```

do not manually edit generated output unless explicitly required.

Fix the source and rebuild.

---

## Build Caching

If a failure appears cache-related:

1. confirm evidence
2. use the project's supported cache-clearing method
3. rebuild

Do not delete arbitrary directories without understanding their purpose.

---

## Build Timeouts

If the build exceeds the tool timeout:

- determine whether the timeout is caused by the build itself
- inspect available output
- use an appropriate higher timeout when permitted
- do not declare the build failed solely because the orchestration timeout occurred if actual build status is unknown

---

## Build Success Criteria

Build verification succeeds only when the intended build command returns successful status and relevant output indicates successful completion.

Do not infer success from:

```text
no error seen yet
```

or:

```text
command started successfully
```

---

## Deployment Preparation

For deployment-related tasks, build verification should normally happen before deployment unless the deployment platform performs its own build and local build is intentionally unavailable.

---

## Completion Reporting

Record:

```text
Build command:
Result:
Important warnings:
Environment limitations:
```

Warnings are not automatically failures, but they should be assessed for relevance.

---

## Final Rule

**Never say "the project builds" unless the actual project build or equivalent verification was successfully executed.**