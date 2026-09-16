# Spreadsheet Creation Skill

## Purpose

Create reliable, structured, usable spreadsheet files such as `.xlsx`.

Use for:

- Data analysis
- Reports
- Financial models
- Inventories
- Trackers
- Schedules
- Dashboards
- Calculations
- Data exports
- Planning sheets

---

## Recommended Library

For Python:

```text
openpyxl
```

Use spreadsheet-native formulas and structures whenever appropriate.

---

## Core Principle

A spreadsheet should preserve the distinction between:

```text
Raw data
Calculated data
Presentation
```

Do not mix everything into one unstructured sheet.

---

## Recommended Workbook Structure

For complex workbooks:

```text
README
Raw Data
Calculations
Summary
Dashboard
```

Use only the sheets necessary for the task.

---

## Data Integrity

Never silently alter source data.

Before transformation:

- inspect columns
- inspect data types
- identify missing values
- identify duplicates
- identify malformed values

Document transformations when relevant.

---

## Formulas

Use formulas for calculations that users may need to modify.

Examples:

```text
=SUM(B2:B20)
=AVERAGE(C2:C20)
=IF(D2>100,"High","Low")
```

Do not hard-code calculated results when formulas are expected.

---

## Formatting

Use consistent:

- number formats
- date formats
- alignment
- column widths
- row heights
- headers
- borders
- typography

Avoid excessive decoration.

---

## Tables

Where appropriate, use Excel tables rather than simply formatting ranges.

Tables provide:

- filtering
- sorting
- structured references
- better usability

---

## Freeze Panes

For large datasets, freeze appropriate rows/columns.

Example:

```text
Freeze header row
```

This improves usability.

---

## Filters

Apply filters where users are likely to explore datasets.

---

## Conditional Formatting

Use conditional formatting for meaningful signals such as:

- thresholds
- outliers
- status
- missing values
- performance

Do not use formatting purely for decoration.

---

## Charts

Charts should reflect actual workbook data.

Verify:

- source range
- labels
- units
- titles
- categories
- values

Never create a chart from fabricated values.

---

## Data Validation

Use validation where useful:

- dropdowns
- date ranges
- numeric ranges
- required categories

---

## Protection

Protect formulas or sheets only when requested or clearly useful.

Do not make a workbook difficult to edit without justification.

---

## Verification

After saving:

1. Check file exists.
2. Reopen workbook.
3. Check sheet names.
4. Check expected cell values.
5. Check formulas.
6. Check merged cells.
7. Check tables.
8. Check charts.
9. Check formatting where practical.

For formulas, remember that `openpyxl` does not calculate Excel formulas itself. If calculated values are required, use an appropriate calculation engine or instruct the user to recalculate in Excel/LibreOffice.

---

## Common Problems

Watch for:

- broken formulas
- incorrect ranges
- wrong number formats
- truncated columns
- hidden data
- accidental overwritten values
- duplicate sheets
- broken chart references
- formula strings accidentally stored as text

---

## Completion Criteria

A spreadsheet is complete when:

- Workbook opens
- Sheets are correct
- Data is correct
- Formulas are correct
- Formatting is usable
- Charts reference correct data
- No accidental data loss occurred
- Final path is verified