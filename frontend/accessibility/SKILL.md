# Accessibility Skill

## Purpose

Ensure frontend interfaces are usable by people with different abilities, input methods, and assistive technologies.

Accessibility should be considered during implementation rather than added only after development.

---

## When to Use

Use this skill whenever:

- Creating UI
- Modifying components
- Creating forms
- Adding navigation
- Adding interactive controls
- Implementing modals
- Adding animations
- Creating dynamic content
- Working with images or media
- Reviewing frontend code

---

## Core Principle

Do not create barriers unnecessarily.

Prefer native semantic HTML before custom accessibility behavior.

Examples:

- Use `<button>` for actions.
- Use `<a>` for navigation.
- Use headings for document structure.
- Use `<label>` for form controls.
- Use lists for lists.
- Use `<table>` for tabular data.

Do not replace semantic elements with generic `<div>` elements without a reason.

---

## Keyboard Accessibility

All interactive functionality should be usable with a keyboard where applicable.

Check:

- Tab navigation
- Enter/Space activation
- Focus visibility
- Logical focus order
- Escape behavior
- Modal focus handling
- Keyboard traps

Do not remove visible focus indicators without providing an equivalent.

---

## Focus Management

Interactive components should manage focus appropriately.

Especially consider:

- Dialogs
- Menus
- Dropdowns
- Navigation drawers
- Dynamic content
- Form errors

When opening a modal, focus should move appropriately.

When closing it, focus should return appropriately when practical.

---

## Images

Images should have appropriate alternative text.

Determine whether an image is:

- Informational
- Functional
- Decorative

Decorative images should not create unnecessary screen-reader noise.

Do not use meaningless alt text such as `"image"`.

---

## Forms

Ensure:

- Every input has an accessible label.
- Errors are understandable.
- Required fields are communicated.
- Invalid fields can be identified.
- Validation does not depend solely on color.
- Instructions are associated with the relevant field.

---

## Color and Contrast

Do not communicate information through color alone.

Check:

- Text contrast
- Interactive element contrast
- Error states
- Success states
- Focus indicators
- Disabled states

Do not assume that a visually attractive palette is automatically accessible.

---

## Dynamic Content

For dynamically changing content, consider how assistive technologies will perceive updates.

Examples:

- Toast notifications
- Validation messages
- Loading states
- Search results
- Status updates

Use appropriate semantic mechanisms when necessary.

Avoid excessive announcements.

---

## Motion

Respect users who request reduced motion.

Where appropriate:

- Detect reduced-motion preferences.
- Reduce or remove non-essential animation.
- Avoid flashing content.
- Never make essential information dependent on animation.

---

## Semantic Structure

Maintain meaningful document structure:

- One logical page heading where appropriate
- Hierarchical headings
- Landmarks
- Meaningful links
- Semantic controls

Do not use heading elements purely for visual sizing.

---

## Automated Checks

When available, use:

- Accessibility linters
- Automated accessibility scanners
- Browser accessibility inspection
- Framework-specific tooling

Automated checks do not replace manual review.

---

## Manual Review

Check important workflows using:

- Keyboard navigation
- Focus visibility
- Form interaction
- Error states
- Responsive layouts
- Reduced motion where relevant

---

## Completion Criteria

Accessibility work is complete when:

- Semantic HTML is used appropriately.
- Keyboard interaction works for relevant functionality.
- Focus behavior is reasonable.
- Forms are labeled and errors are understandable.
- Images have appropriate alternatives.
- Color is not the sole communication mechanism.
- Motion preferences are respected.
- Automated checks have been run when available.
- Important workflows have been manually considered.