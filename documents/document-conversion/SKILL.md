# Document Conversion Skill

## Purpose

Convert documents between formats while preserving content, structure, and usability as much as reasonably possible.

Examples:

```text
DOCX → PDF
PDF → text
Markdown → PDF
Markdown → DOCX
PPTX → PDF
XLSX → CSV
CSV → XLSX
HTML → PDF
```

---

## Core Principle

Conversion is not simply changing a file extension.

Always consider:

```text
Source semantics
→ Target capabilities
→ Conversion method
→ Content verification
→ Layout verification
```

---

## Before Conversion

Identify:

1. Source format
2. Target format
3. Required content preservation
4. Required editability
5. Layout sensitivity
6. Images
7. Tables
8. Fonts
9. Hyperlinks
10. Metadata
11. Expected output location

---

## Choose Appropriate Conversion Method

Use the conversion tool appropriate to the formats.

Examples:

```text
DOCX ↔ PDF
```

may require an office rendering engine.

```text
Markdown → PDF
```

can use a PDF generation pipeline.

```text
XLSX → CSV
```

should preserve tabular data rather than visual formatting.

---

## Lossy Conversion

Some conversions inherently lose information.

Examples:

```text
XLSX → CSV
```

can lose:

- formulas
- formatting
- charts
- multiple worksheets

```text
PDF → DOCX
```

can lose:

- exact positioning
- fonts
- complex layouts
- editable structure

The agent must recognize and communicate meaningful losses.

---

## Content Verification

After conversion:

- reopen output
- extract text where applicable
- compare important headings
- compare record counts
- verify images
- verify tables
- verify links when relevant

---

## Layout Verification

For visually sensitive conversions:

```text
Convert
→ Render
→ Inspect
```

Check:

- page breaks
- clipping
- font substitution
- table overflow
- image placement
- blank pages
- spacing

---

## Batch Conversion

For multiple files:

1. Enumerate inputs.
2. Validate each input.
3. Convert independently.
4. Record success/failure per file.
5. Validate each output.
6. Produce a summary.

One failed file should not automatically hide successful conversions.

---

## Naming

Use deterministic filenames.

Example:

```text
report.docx
→ report.pdf
```

Avoid random names unless required.

Never overwrite source files unless explicitly instructed.

---

## Error Recovery

If conversion fails:

1. Identify converter failure.
2. Check source validity.
3. Check dependencies.
4. Try a compatible conversion route.
5. Validate output.
6. Report limitations.

Do not repeatedly run the same failed command without changing anything.

---

## Completion Criteria

Conversion is complete when:

- Target file exists
- Target can be opened
- Content is sufficiently preserved
- Known losses are understood
- Layout is acceptable where relevant
- Source remains intact unless overwrite was explicitly requested