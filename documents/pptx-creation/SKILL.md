# PPTX Creation Skill

## Purpose

Create professional PowerPoint presentations programmatically.

Use this skill for:

- Pitch decks
- School presentations
- Project demos
- Business presentations
- Technical presentations
- Research presentations
- Hackathon presentations
- Educational slides
- Investor-style decks

---

## Core Principle

A presentation is a visual communication artifact, not a document placed onto slides.

Prioritize:

```text
Narrative
→ Visual hierarchy
→ Clarity
→ Evidence
→ Design
→ Technical correctness
```

---

## Workflow

```text
Understand audience
→ Define objective
→ Build story
→ Create slide outline
→ Establish design system
→ Generate slides
→ Add visuals
→ Validate
→ Render and inspect
```

---

## Recommended Library

For Python:

```text
python-pptx
```

Use PowerPoint-native elements whenever possible.

---

## Story Before Slides

Define the presentation narrative before generating slides.

Example:

```text
1. Problem
2. Why it matters
3. Current limitations
4. Proposed solution
5. How it works
6. Architecture
7. Demo / workflow
8. Results
9. Future scope
10. Conclusion
```

Do not generate random slides independently.

---

## Slide Density

Avoid putting an entire report onto slides.

A slide should communicate one main idea.

Prefer:

```text
Short headline
+
Supporting visual
+
Small amount of supporting text
```

Avoid:

- giant paragraphs
- tiny fonts
- excessive bullet lists
- unnecessary decorative elements

---

## Design System

Establish:

- Background treatment
- Primary typography
- Heading typography
- Body typography
- Spacing
- Alignment
- Card style
- Icon treatment
- Image treatment

Use a consistent system throughout the deck.

---

## Slide Types

Common reusable layouts:

### Title

```text
Title
Subtitle
Presenter / organization
```

### Problem

```text
Problem statement
Evidence
Visual
```

### Feature

```text
Feature title
Short explanation
Screenshot / diagram
```

### Architecture

```text
User
↓
Frontend
↓
Backend
↓
AI / APIs
↓
Database / Services
```

### Comparison

```text
Current approach | Proposed approach
```

### Results

Use:

- charts
- metrics
- screenshots
- concise evidence

---

## Visual Hierarchy

Use size and position to establish importance.

Typical order:

```text
Headline
↓
Key visual / metric
↓
Supporting explanation
↓
Secondary metadata
```

Everything should not have equal visual weight.

---

## Images

Verify every image before insertion.

Check:

- existence
- readability
- aspect ratio
- resolution
- relevance

Crop rather than distort.

---

## Charts

Charts should answer a question.

Before creating a chart ask:

```text
What should the audience understand from this chart?
```

Avoid decorative charts with no analytical purpose.

Label axes and units.

Never invent data.

---

## Speaker Notes

When useful, add speaker notes containing:

- talking points
- demo instructions
- explanations
- transitions
- references

Do not place every explanation directly on the slide.

---

## Accessibility

Consider:

- sufficient contrast
- readable font sizes
- meaningful slide titles
- alternative text
- logical reading order
- avoiding information conveyed only through color

---

## Validation

After generating:

### Structural

Check:

- slide count
- slide titles
- text
- images
- shapes
- charts where applicable

### File

Check:

```text
exists?
non-zero?
opens?
```

### Visual

Render slides to images/PDF when possible.

Inspect for:

- overflow
- clipping
- overlapping elements
- inconsistent alignment
- unreadable text
- excessive whitespace
- broken images
- accidental blank slides

---

## Presentation-Specific Rule

Never optimize for maximum information per slide.

Optimize for:

```text
maximum understanding per slide
```

---

## Completion Criteria

A PPTX is complete only when:

- File opens
- Slide sequence is correct
- Narrative is coherent
- Text is readable
- Visuals are present
- No elements overflow
- Design is consistent
- Required data is accurate
- Output path is verified