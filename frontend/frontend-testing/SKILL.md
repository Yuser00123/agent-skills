# Frontend Testing Skill

## Purpose

Verify frontend behavior through appropriate automated and manual testing.

Tests should provide confidence in user-visible behavior rather than merely increasing coverage numbers.

---

## When to Use

Use this skill when:

- Adding frontend functionality
- Fixing UI bugs
- Refactoring components
- Changing routing
- Changing forms
- Modifying API interactions
- Changing state management
- Preparing a release
- Investigating regressions

---

## Testing Strategy

Use the smallest effective test scope first.

Recommended sequence:

1. Targeted test
2. Related component/module tests
3. Integration tests
4. Full test suite when appropriate

Do not immediately run the entire suite for every small change if targeted testing provides faster feedback.

---

## Test Behavior

Prefer testing what users and systems observe.

Test:

- Rendering
- User interaction
- Navigation
- Form submission
- Validation
- Loading
- Error states
- Empty states
- API responses
- State transitions

Avoid over-testing implementation details.

---

## Component Tests

For components, consider:

- Default rendering
- Important props
- User interactions
- Conditional states
- Error states
- Accessibility behavior

Do not create tests for trivial implementation details that provide little protection.

---

## Integration Tests

Use integration tests when behavior depends on multiple pieces working together.

Examples:

- Form + validation + API
- Page + routing
- Component + state management
- Search + API + result rendering

---

## Browser / End-to-End Testing

Use browser-based tests for critical user journeys when the project supports them.

Examples:

- Login
- Checkout
- Main application workflow
- Navigation
- Important forms
- Deployment smoke tests

---

## Mocking

Mock external systems when appropriate.

Good candidates include:

- External APIs
- Payment providers
- Authentication services
- Unstable external dependencies

Do not mock the behavior being tested unnecessarily.

---

## Edge Cases

Consider:

- Empty data
- Very long text
- Invalid input
- Slow responses
- Failed requests
- Duplicate actions
- Missing optional fields
- Unexpected API responses
- Mobile viewport
- Keyboard interaction

---

## Regression Tests

When fixing a reproducible bug:

1. Reproduce the failure.
2. Create a test that captures the failure where practical.
3. Implement the fix.
4. Run the regression test.
5. Run related tests.

The test should fail for the old behavior and pass for the fixed behavior when feasible.

---

## Test Failures

Never hide test failures.

Classify failures as:

- Implementation failure
- Test failure
- Environment failure
- Dependency failure
- External service failure
- Flaky behavior

Investigate before changing tests.

Do not weaken assertions merely to make the suite pass.

---

## Visual Testing

When visual testing is available, inspect:

- Layout
- Responsive behavior
- Typography
- Overflow
- Major visual regressions

Visual correctness should not be inferred solely from unit tests.

---

## Completion Criteria

Frontend testing is complete when:

- Relevant tests have been identified.
- Targeted tests have been run.
- Related tests are run when appropriate.
- Important user flows are covered.
- Regression coverage exists for significant bug fixes where practical.
- Failures are honestly reported.
- Test results are not fabricated or inferred.