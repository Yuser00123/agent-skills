# File Validation Skill

## Purpose

Verify that generated or modified files are actually valid, complete, readable, and suitable for delivery.

This skill is especially important for autonomous agents.

---

## Core Principle

Never equate:

```text
Command succeeded
```

with:

```text
Artifact succeeded
```

A process can exit with code `0` while producing:

- empty files
- corrupted files
- incomplete output
- malformed documents
- visually broken documents

---

## Universal Validation Pipeline

```text
Existence
→ File size
→ File type
→ Structural validity
→ Content validity
→ Visual validity
→ Requirement validation
```

---

## Step 1 — Existence

Check:

```text
Does the expected file exist?
```

---

## Step 2 — File Size

Reject obviously invalid outputs:

```text
size == 0
```

Very small files should also be investigated when the format normally requires substantial content.

---

## Step 3 — File Type

Verify the actual file type rather than trusting the extension.

Examples:

```text
.pdf → valid PDF
.docx → valid DOCX/ZIP structure
.xlsx → valid XLSX/ZIP structure
.pptx → valid PPTX/ZIP structure
.csv → parseable text data
```

---

## Step 4 — Structural Validation

### PDF

Check:

- page count
- readable structure
- text extraction
- expected sections

### DOCX

Check:

- paragraphs
- headings
- tables
- relationships
- images

### PPTX

Check:

- slide count
- slide titles
- text
- images
- shapes

### XLSX

Check:

- worksheet names
- cell values
- formulas
- tables
- charts

### CSV

Check:

- headers
- row counts
- column counts
- parseability

---

## Step 5 — Content Validation

Compare the output against requirements.

For example:

```text
Requirement:
"Create a 10-page report with 5 sections."

Validation:
page_count >= expected
all 5 sections present
```

Do not assume content is correct merely because the file opens.

---

## Step 6 — Visual Validation

For visual formats, render the artifact and inspect it.

Look for:

- clipping
- overflow
- overlap
- missing assets
- blank pages
- unreadable text
- broken tables
- inconsistent spacing
- incorrect page breaks

This is critical for:

- PDF
- DOCX
- PPTX
- XLSX dashboards

---

## Step 7 — Requirement Validation

Create a checklist:

```text
[✓] File exists
[✓] Opens successfully
[✓] Correct format
[✓] Required sections present
[✓] Required assets present
[✓] Layout acceptable
[✓] Output path verified
```

---

## Programmatic Validation

Prefer deterministic checks.

Example:

```text
assert file_exists
assert file_size > 0
assert expected_extension
assert parser_can_open
assert required_content_exists
```

Use format-specific validators where possible.

---

## Visual Validation Threshold

Not every generated file requires manual visual inspection.

Use stronger visual validation when:

- design matters
- the file is user-facing
- layout is complex
- tables are large
- images are included
- conversion was performed
- presentation quality matters

---

## Failure Classification

Classify failures:

```text
FILE_NOT_FOUND
EMPTY_FILE
INVALID_FORMAT
CORRUPTED_FILE
MISSING_CONTENT
CONTENT_MISMATCH
LAYOUT_ERROR
MISSING_ASSET
CONVERSION_ERROR
```

This makes autonomous recovery easier.

---

## Recovery

When validation fails:

```text
Identify failure
→ Determine cause
→ Modify generation/conversion
→ Regenerate
→ Validate again
```

Do not simply retry indefinitely.

Use a retry limit.

---

## Reporting

When successful, report:

```text
Artifact created and validated.
Path: /home/user/project/output/report.pdf
```

When unsuccessful, report the actual failure.

Never fabricate:

- URLs
- file paths
- page counts
- successful validation
- deployment status

---

## Completion Criteria

Validation is complete only when:

- Artifact exists
- Correct format confirmed
- File opens
- Required content verified
- Important layout verified
- Known limitations documented
- Final path confirmed