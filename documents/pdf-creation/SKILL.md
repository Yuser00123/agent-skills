# PDF Creation Skill

## Purpose

Create professional, reliable PDF documents programmatically from structured content, Markdown, HTML, data, or generated material.

This skill covers:

- Creating PDFs from scratch
- Converting structured content into PDF
- Multi-page documents
- Reports
- Resumes
- Invoices
- Certificates
- Study materials
- Technical documentation
- Tables and charts
- Headers, footers, page numbers
- Images and diagrams
- Unicode and multilingual content
- PDF quality verification

---

## Core Principle

A PDF is not considered successfully created merely because a `.pdf` file exists.

The workflow must be:

```text
Understand requirements
→ Plan document structure
→ Generate PDF
→ Verify file
→ Verify content
→ Verify layout
→ Report result
```

Never claim successful PDF creation without verification.

---

## Before Creating

Determine:

1. Document purpose
2. Target audience
3. Page size
4. Orientation
5. Required sections
6. Expected page count if specified
7. Fonts
8. Images
9. Tables
10. Headers/footers
11. Page numbering
12. Language requirements
13. Accessibility requirements
14. Output filename
15. Whether the document should be editable or final-only

Default:

- Page size: A4
- Orientation: portrait
- Professional margins
- Consistent typography
- Clear hierarchy

---

## Content Structure

For reports:

```text
Title
Executive Summary
Introduction
Main Content
Analysis
Results
Conclusion
References / Appendix
```

For educational material:

```text
Title
Learning Objectives
Concepts
Examples
Exercises
Answers / Solutions
Summary
```

For technical documentation:

```text
Title
Overview
Requirements
Installation
Usage
Configuration
Examples
Troubleshooting
Security
Appendix
```

Do not invent missing information.

---

## PDF Generation

Use a suitable PDF-generation approach.

For Python-based document generation, prefer `reportlab.platypus` for text-heavy PDFs.

Use appropriate elements such as:

- Paragraph
- Table
- Image
- Spacer
- PageBreak
- ListFlowable
- KeepTogether
- TableOfContents when appropriate

Use reusable styles rather than formatting every element independently.

---

## Typography

Create a typography hierarchy:

```text
Title
↓
Section heading
↓
Subsection heading
↓
Body text
↓
Caption / metadata
```

Avoid excessive font changes.

Use readable font sizes.

Typical starting points:

- Title: 20–28 pt
- Heading: 14–18 pt
- Body: 9–12 pt
- Caption: 8–10 pt

Adjust according to document type.

---

## Unicode

Before generating multilingual PDFs, verify font support.

Do not assume default PDF fonts support:

- Hindi
- Chinese
- Japanese
- Korean
- Arabic
- Cyrillic
- Emoji

For supported UnicodeCIDFont requirements, use the appropriate registered font.

For example:

```text
Japanese → HeiseiMin-W3 / HeiseiKakuGo-W5
Simplified Chinese → STSong-Light
Traditional Chinese → MSung-Light
Korean → HYSMyeongJo-Medium
```

For other languages, use a suitable embedded Unicode font when available.

---

## Tables

Tables must:

- Fit within page width
- Have readable text
- Have consistent alignment
- Avoid unnecessary borders
- Repeat headers across pages when appropriate
- Avoid splitting important rows when possible

Long tables should be designed for pagination.

---

## Images

Before inserting an image:

1. Verify the file exists.
2. Verify the image can be opened.
3. Determine dimensions.
4. Scale proportionally.
5. Avoid distortion.
6. Keep sufficient resolution.
7. Add captions when useful.

Never stretch images arbitrarily.

---

## Headers and Footers

Use headers/footers when useful.

Possible footer:

```text
Document title | Page 3 of 10
```

Avoid adding decorative elements that reduce usable page space.

---

## Page Layout

Watch for:

- orphan headings
- headings separated from content
- table overflow
- clipped text
- excessive whitespace
- content outside margins
- overlapping elements
- blank pages

Use layout controls such as `KeepTogether` where appropriate.

---

## Verification

After generation:

### File verification

Check:

```text
exists?
size > 0?
valid PDF signature?
```

### Structural verification

Check:

- page count
- text extraction
- metadata when relevant
- expected headings
- expected sections

### Visual verification

Render pages to images when possible and inspect for:

- clipping
- overlapping text
- broken tables
- bad spacing
- missing images
- incorrect page breaks
- unreadable text

---

## Failure Handling

If PDF creation fails:

1. Capture the error.
2. Determine whether the failure is content, dependency, font, image, or layout related.
3. Fix the underlying issue.
4. Regenerate.
5. Validate again.

Do not silently produce an incomplete document.

---

## Completion Criteria

PDF creation is complete only when:

- PDF exists
- PDF opens successfully
- Expected content exists
- Layout is acceptable
- No obvious clipping/overflow exists
- Required assets are present
- Output path is known

Only then report success.