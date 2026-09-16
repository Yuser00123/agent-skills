# CSV Creation Skill

## Purpose

Create clean, interoperable CSV files for data exchange and machine processing.

Use for:

- Dataset exports
- Data pipelines
- Reports
- API exports
- Import files
- Training datasets
- Spreadsheet-compatible data

---

## Core Principle

CSV is a data interchange format, not a visual document.

Prioritize:

```text
Correctness
→ Consistency
→ Encoding
→ Compatibility
```

---

## Recommended Library

For Python:

```text
pandas
```

Use `csv` from the Python standard library when lightweight control is sufficient.

---

## Before Export

Inspect:

- columns
- data types
- null values
- duplicate records
- special characters
- delimiter requirements
- encoding requirements

---

## Column Rules

Column names should be:

- consistent
- unambiguous
- stable
- machine-friendly

Avoid changing source column names unless required.

---

## Missing Values

Choose a consistent representation.

Examples:

```text
empty
NULL
NaN
```

The correct choice depends on the consuming system.

Never randomly mix representations.

---

## Encoding

Default to UTF-8 unless a consuming application explicitly requires another encoding.

For broad spreadsheet compatibility, UTF-8 with BOM may sometimes be appropriate.

---

## Delimiters

Comma is the default:

```text
,
```

But support other delimiters when required.

Never assume comma-separated data is safe if values themselves contain commas.

Proper quoting is mandatory.

---

## Quoting

Values containing:

- commas
- quotes
- line breaks

must be escaped/quoted according to CSV rules.

Example conceptually:

```text
"New York, USA"
```

Do not manually concatenate strings when robust CSV libraries are available.

---

## Validation

After writing:

1. Reopen the CSV.
2. Parse it again.
3. Check row count.
4. Check column count.
5. Check headers.
6. Check representative values.
7. Verify encoding.

The exported file should round-trip correctly.

---

## Large CSV Files

For very large datasets:

- stream/chunk when possible
- avoid unnecessary copies
- avoid loading the entire dataset into memory unnecessarily

---

## Security

Watch for spreadsheet formula injection.

Cells beginning with characters such as:

```text
=
+
-
@
```

may be interpreted as formulas by spreadsheet software.

If CSV data can contain untrusted user input and will be opened in spreadsheets, sanitize or explicitly handle these values according to the application requirements.

---

## Completion Criteria

A CSV is complete when:

- File exists
- Encoding is correct
- Headers are correct
- Row structure is consistent
- Values round-trip correctly
- Required records are present
- No unintended transformations occurred