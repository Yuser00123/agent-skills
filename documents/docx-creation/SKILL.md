# DOCX Creation Skill

## Purpose

Create professional Microsoft Word `.docx` documents programmatically.

Use this skill for:

- Reports
- Assignments
- Resumes
- Letters
- Proposals
- Documentation
- Meeting notes
- Educational documents
- Business documents
- Templates
- Editable deliverables

---

## Core Principle

DOCX generation must preserve both:

1. Content correctness
2. Editable document structure

Do not create a document that merely looks correct while having poor Word structure.

---

## Workflow

```text
Understand requirements
→ Design document structure
→ Create styles
→ Add content
→ Add tables/images
→ Configure headers/footers
→ Save
→ Reopen
→ Validate
→ Visually inspect when possible
```

---

## Recommended Library

For Python DOCX generation, use:

```text
python-docx
```

Do not manually construct DOCX XML unless the required feature cannot reasonably be achieved through the library.

---

## Document Structure

Use real Word structure:

- Heading 1
- Heading 2
- Heading 3
- Normal
- Caption
- Quote
- List styles

Do not fake headings by merely increasing font size.

This allows:

- Navigation pane
- Table of contents
- Accessibility
- Easier editing

---

## Styles

Define document-wide styles before adding large amounts of content.

Configure:

- Font
- Font size
- Paragraph spacing
- Line spacing
- Alignment
- Indentation
- Heading hierarchy

Avoid manually formatting every paragraph.

---

## Page Configuration

Configure:

- Page size
- Margins
- Orientation
- Header distance
- Footer distance

Default to A4 when appropriate.

---

## Headers and Footers

Use headers/footers for:

- Document title
- Organization
- Confidentiality notice
- Page number
- Version

Do not clutter every page.

---

## Page Numbers

Use proper Word field-based page numbers when supported.

Avoid manually writing:

```text
Page 1
Page 2
Page 3
```

because page counts can change.

---

## Tables

When creating tables:

- Set appropriate column widths
- Use header rows
- Keep text readable
- Avoid excessively wide tables
- Avoid unnecessary merged cells
- Prevent awkward row splitting when possible

Tables should remain editable.

---

## Images

For every image:

1. Verify file exists.
2. Verify image opens.
3. Preserve aspect ratio.
4. Set appropriate size.
5. Use captions where useful.
6. Add alternative text when supported/required.

Do not insert enormous source images without scaling.

---

## Lists

Use actual Word lists where possible.

Prefer:

```text
• Item
• Item
• Item
```

through Word list structures rather than manually inserting bullet characters.

Same principle applies to numbered lists.

---

## Table of Contents

For long documents, use heading styles so Word can generate a Table of Contents.

Do not manually type a fake TOC unless explicitly requested.

---

## Hyperlinks

Use actual hyperlinks.

Verify:

- URL
- display text
- link target

Do not leave raw URLs unnecessarily if polished document formatting is expected.

---

## Metadata

When appropriate, set:

- Title
- Author
- Subject
- Keywords

Do not insert fake metadata.

---

## Validation

After saving:

1. Verify file exists.
2. Verify file size.
3. Reopen with `python-docx`.
4. Check expected paragraphs.
5. Check expected headings.
6. Check tables.
7. Check images.
8. Check document relationships when necessary.

For visual validation, convert DOCX to PDF or render it through an available office renderer and inspect pages.

---

## Common Problems

Watch for:

- unexpected blank pages
- broken tables
- images outside page boundaries
- inconsistent spacing
- headings at bottom of pages
- incorrect page breaks
- missing fonts
- malformed hyperlinks
- missing images
- corrupted DOCX files

---

## Completion Criteria

A DOCX task is complete only when:

- File opens successfully
- Required content exists
- Styles are applied consistently
- Tables/images are present
- Document remains editable
- No obvious layout problems exist
- Final file path is known

Never report success solely because `save()` completed.