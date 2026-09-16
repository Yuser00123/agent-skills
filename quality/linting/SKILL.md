# Linting Skill

## Purpose

Use linters, formatters, type checks, and static-analysis tools to detect consistency, correctness, and maintainability problems.

Linting is a verification mechanism, not a replacement for tests.

---

## When to Use

Use this skill when:

- Modifying code
- Adding files
- Refactoring
- Preparing commits
- Preparing deployments
- Debugging static-analysis failures

---

## Before Running Tools

Identify the project's existing:

- Linter
- Formatter
- Type checker
- Static-analysis configuration
- Package manager
- Scripts

Prefer project-provided commands over installing alternative tools.

---

## Configuration

Respect existing configuration.

Do not rewrite lint configuration merely to make the current change pass.

Before modifying a rule, determine:

- Why the rule exists.
- Whether existing code depends on it.
- Whether the violation represents a real problem.

---

## Fixing Lint Errors

Prefer fixing the underlying code.

Examples:

- Remove unused variables.
- Correct invalid dependencies.
- Fix unsafe patterns.
- Simplify unreachable code.
- Correct type mismatches.
- Improve naming where appropriate.

Do not disable rules without justification.

---

## Formatting

Use the project's formatter when available.

Avoid manual formatting that conflicts with repository conventions.

Do not create massive formatting diffs unrelated to the requested change.

---

## Type Checking

When TypeScript or another type system is used:

- Run the existing type checker.
- Do not suppress errors casually.
- Avoid broad `any` or equivalent escapes solely to silence errors.
- Fix underlying type mismatches when practical.

---

## Validation Sequence

A useful sequence is:

1. Format affected files if required.
2. Run linting.
3. Run type checks.
4. Run targeted tests.
5. Run broader checks where appropriate.

---

## Tool Failures

Distinguish:

- Actual lint errors
- Configuration errors
- Missing dependencies
- Environment failures
- Incorrect commands

Do not report a lint failure as a code failure without checking the cause.

---

## Completion Criteria

Linting is complete when:

- Relevant static checks have been run.
- Genuine violations have been fixed or explicitly documented.
- No unjustified lint suppression was introduced.
- Formatting follows project conventions.
- Type-check status is known where applicable.