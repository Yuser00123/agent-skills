# Browser Automation Skill

## Purpose

Safely interact with websites through browser automation when a task requires actual webpage interaction.

Automation should be deterministic where possible and should verify outcomes instead of assuming actions succeeded.

---

## When to Use

Use this skill when:

- Opening webpages
- Navigating websites
- Testing web applications
- Filling forms
- Clicking UI controls
- Capturing screenshots
- Verifying deployed applications
- Testing user workflows
- Extracting information from interactive pages

---

## Core Workflow

Follow:

1. Identify the target website.
2. Navigate to the correct page.
3. Inspect the page state.
4. Identify the intended element.
5. Perform the action.
6. Observe the resulting state.
7. Verify the expected outcome.
8. Continue only when the state is correct.

Do not blindly execute a predetermined sequence if the webpage state differs.

---

## Element Identification

Prefer stable selectors or semantic identifiers.

Prefer:

- Accessible roles
- Labels
- Stable IDs
- Stable attributes
- Text when appropriate

Avoid fragile selectors based on:

- Deep DOM hierarchy
- Automatically generated class names
- Position alone

---

## Page State

Before important actions, verify:

- Correct URL
- Correct page
- Correct authentication state
- Required elements exist
- Page has finished loading sufficiently

---

## Forms

Before submitting forms:

- Confirm field values.
- Confirm required fields.
- Confirm intended destination.
- Avoid accidental duplicate submissions.

After submission, verify:

- Success message
- URL change
- Result element
- Server response
- Other reliable evidence

---

## Authentication

Do not attempt to bypass authentication, CAPTCHAs, access controls, or security mechanisms.

Never expose credentials in logs, screenshots, or generated output.

Use credentials only through approved secure mechanisms.

---

## Destructive Actions

Treat actions such as:

- Delete
- Cancel
- Publish
- Deploy
- Send
- Purchase
- Change permissions

as high-impact actions.

Verify intent and target before executing.

When the workflow requires explicit user confirmation, do not bypass it.

---

## Screenshots

Use screenshots when visual verification is useful.

Check:

- Layout
- Errors
- Broken elements
- Responsive behavior
- Unexpected overlays
- Loading states

Do not claim a visual issue was verified without actually inspecting the relevant result.

---

## Dynamic Websites

Expect:

- Loading delays
- Lazy-loaded content
- Popups
- Redirects
- Dynamic IDs
- Client-side rendering

Wait for meaningful state conditions rather than arbitrary delays whenever possible.

---

## Failure Recovery

If an automation step fails:

1. Inspect current page state.
2. Determine whether navigation changed.
3. Check whether the action partially succeeded.
4. Retry only when safe.
5. Avoid duplicate side effects.
6. Report unresolved failures honestly.

---

## Completion Criteria

Browser automation is complete only when:

- The intended page/workflow was reached.
- Actions were performed on the correct elements.
- Important side effects were verified.
- Errors were handled.
- No unauthorized bypass occurred.
- Final state was actually observed.