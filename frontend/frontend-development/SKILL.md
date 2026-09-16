# Frontend Development Skill

## Purpose

Build, modify, and maintain frontend applications safely, consistently, and production-ready.

This skill governs how the agent works with frontend code, including React, Next.js, Vue, Angular, Svelte, vanilla JavaScript, TypeScript, HTML, CSS, and related frameworks.

The goal is not merely to make a page render. The goal is to produce a correct, maintainable, responsive, accessible, testable, and integrated frontend.

---

## When to Use

Use this skill when:

- Creating a new frontend application
- Adding or modifying pages
- Creating components
- Changing layouts
- Implementing responsive behavior
- Adding forms or interactive UI
- Connecting frontend components to APIs
- Fixing frontend bugs
- Refactoring frontend code
- Adding frontend dependencies
- Modifying routing
- Working with state management
- Implementing loading, error, or empty states

---

## Core Workflow

Follow this general workflow:

1. Understand the request.
2. Analyze the existing frontend.
3. Identify the framework and architecture.
4. Inspect relevant components, routes, styles, and dependencies.
5. Identify existing design conventions.
6. Plan the smallest appropriate change.
7. Implement the change.
8. Test the affected behavior.
9. Run the relevant build/lint/type checks.
10. Review the implementation.
11. Verify the final behavior.
12. Report what was actually verified.

Do not start rewriting the frontend before understanding the existing architecture.

---

## Before Coding

Determine:

- Framework
- Language
- Package manager
- Entry points
- Routing system
- Component structure
- Styling approach
- State management
- API/data layer
- Existing UI component library
- Testing framework
- Build system

Inspect the relevant files before making changes.

Prefer existing project patterns over introducing a new architecture.

---

## Component Design

Create components around meaningful responsibilities.

Avoid:

- Giant components
- Excessive prop drilling
- Repeated markup
- Unnecessary abstraction
- Components that combine unrelated responsibilities

Prefer:

- Clear component boundaries
- Reusable primitives where repetition exists
- Predictable props
- Local state when appropriate
- Shared state only when genuinely required

Do not abstract code merely because it can theoretically be reused.

---

## Responsive Design

Frontend implementations should work across relevant viewport sizes.

Consider:

- Mobile
- Tablet
- Desktop
- Large screens

Check:

- Text wrapping
- Navigation
- Buttons
- Forms
- Images
- Cards
- Tables
- Modals
- Overflow
- Touch targets
- Spacing

Do not solve responsive problems by hiding important functionality.

---

## State Handling

Explicitly consider:

- Initial state
- Loading state
- Success state
- Error state
- Empty state
- Partial data
- Retry behavior
- Disabled states

Do not assume asynchronous operations always succeed.

---

## Data and API Integration

Keep API interaction separate from presentation when practical.

Handle:

- Request failures
- Invalid responses
- Loading
- Timeouts
- Authentication failures
- Empty responses
- Unexpected data
- Retries where appropriate

Do not expose secrets or private credentials in client-side code.

---

## Performance

Avoid unnecessary:

- Re-renders
- Large dependencies
- Network requests
- Duplicate requests
- Large client bundles
- Unoptimized images
- Expensive computations during rendering

Use framework-specific optimization only when it provides a meaningful benefit.

Do not prematurely optimize simple code.

---

## Existing User Changes

Before editing:

- Check Git status.
- Inspect relevant diffs.
- Preserve unrelated user work.
- Do not overwrite modifications merely to simplify implementation.

---

## Verification

After implementation:

- Run relevant tests.
- Run lint/type checks when available.
- Run the production build when appropriate.
- Inspect affected routes/components.
- Verify important interactive states.

A successful compilation alone does not prove frontend correctness.

---

## Completion Criteria

Frontend work is complete only when:

- Requested functionality exists.
- Existing functionality remains intact.
- Relevant states are handled.
- Responsive behavior has been considered.
- Accessibility has been considered.
- Tests/checks have been run where available.
- Build status is known.
- No obvious placeholder implementation remains.

Never claim visual or behavioral verification that was not actually performed.