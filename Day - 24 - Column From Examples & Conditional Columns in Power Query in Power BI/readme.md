# 📊 Column From Examples & Conditional Columns in Power BI

## Overview

Power Query provides tools for creating new columns from patterns and business rules.

Two especially useful features are:

- **Column From Examples** - detects transformation patterns from sample outputs
- **Conditional Column** - creates rule-based outputs using IF–THEN–ELSE logic

These tools reduce repetitive transformation work and help prepare cleaner, analysis-ready datasets.

---

## 1. Power Query Data Import & Setup

Power Query can connect to multiple data sources such as:

- Excel
- CSV
- SQL Server
- Web
- Folder
- Text / JSON
- Other supported sources

Typical preparation steps include:

- Setting data types
- Renaming columns
- Removing unnecessary fields
- Previewing and profiling data
- Checking nulls, errors, and duplicates

---

# 2. Column From Examples

**Column From Examples** allows you to type the desired result for a few rows.

Power Query then attempts to identify the transformation pattern automatically.

## Common Uses

### Split Text

Input:

```text
John Smith
Mary Johnson
David Brown
```

Desired result:

```text
John
Mary
David
```

Power Query can infer that the first part of the text should be extracted.

---

### Merge Text

Input columns:

```text
FirstName | LastName
John      | Smith
```

Desired output:

```text
John Smith
```

Equivalent M logic may be:

```powerquery
[FirstName] & " " & [LastName]
```

---

### Date Transformation

Input:

```text
1/5/2026
1/20/2026
2/10/2026
```

Desired output:

```text
Jan 2026
Jan 2026
Feb 2026
```

Possible M logic:

```powerquery
Date.ToText([OrderDate], "MMM yyyy")
```

---

### Alphanumeric Data

Input:

```text
ABC-001
XYZ-002
DEF-003
```

Desired output:

```text
001
002
003
```

Possible M logic:

```powerquery
Text.AfterDelimiter([ProductCode], "-")
```

---

# 3. Conditional Column

Conditional Columns create new fields based on rules.

Conceptually:

```text
IF condition
THEN result
ELSE another result
```

---

## One-Column Condition

Example:

```powerquery
if [Amount] >= 1000 then "High"
else if [Amount] >= 100 then "Medium"
else "Low"
```

Useful for:

- Sales bands
- Customer tiers
- Risk categories
- Performance groups

---

## Two-Column Condition

Example:

```powerquery
if [Country] = "USA" and [Sales] >= 1000
then "High"
else "Standard"
```

This applies multiple business conditions at the same time.

---

## Comparing Two Columns

Example:

```powerquery
if [Actual] > [Target] then "Above"
else if [Actual] < [Target] then "Below"
else "On Target"
```

Useful for:

- KPI status
- Budget variance
- Sales target analysis
- Operational performance

---

## Conditional Logic on Dates

Example:

```powerquery
if Date.IsInCurrentMonth([OrderDate]) then "Current Month"
else if Date.IsInPreviousMonth([OrderDate]) then "Previous Month"
else "Older"
```

Useful for:

- Monthly reporting
- Aging analysis
- Recent activity tracking
- Period-based filtering

---

# 4. Column From Examples vs Conditional Column

| Feature | Column From Examples | Conditional Column |
|---|---|---|
| Main Purpose | Detect patterns | Apply rules |
| Requires formula writing | Usually no | Usually no |
| Best for | Text/date pattern transformations | Business logic |
| Output | Derived values | Categorized values |
| Typical Use | Split, merge, extract | High/Low, status, segments |

---

# 5. Supporting Power Query Features

## Applied Steps

Every transformation appears as a reusable step.

Example:

```text
Source
↓
Changed Type
↓
Removed Duplicates
↓
Added Conditional Column
↓
Filtered Rows
```

These steps are reapplied during refresh.

---

## Data Profiling

Useful tools include:

- Column Quality
- Column Distribution
- Column Profile

They help identify:

- Valid values
- Errors
- Empty records
- Distinct values
- Data distribution

---

## Remove Duplicates & Errors

Duplicate and error handling improves reliability before analysis.

Common checks:

- Duplicate IDs
- Invalid dates
- Missing values
- Incorrect data types
- Transformation errors

---

## Group By

Group By summarizes records using operations such as:

```text
Sum
Count
Average
Min
Max
```

Example use cases:

- Sales by category
- Orders by customer
- Revenue by region

---

## Sort & Filter

Filtering helps isolate relevant records before loading data.

Examples:

```text
Region = East
Status = Active
Sales > 1000
```

---

## Split & Merge Columns

Common transformations include:

```text
Full Name → First Name + Last Name
Email → Username + Domain
Product Code → Prefix + ID
```

Columns can also be recombined when needed.

---

# 6. Practical Analytics Workflow

```text
IMPORT DATA
    ↓
PROFILE DATA
    ↓
CLEAN & SET TYPES
    ↓
COLUMN FROM EXAMPLES
    ↓
CONDITIONAL LOGIC
    ↓
VALIDATE OUTPUT
    ↓
LOAD TO POWER BI
    ↓
ANALYZE
```

---

# 7. Why These Features Matter

They help analysts:

- Reduce manual transformations
- Create reusable business rules
- Standardize categories
- Derive useful attributes
- Improve data preparation
- Build refreshable workflows
- Prepare cleaner datasets for reporting

---

# Key Takeaway

**Column From Examples** is useful when Power Query can infer a transformation pattern from sample outputs.

**Conditional Column** is useful when the output depends on explicit business rules.

Together they support a more efficient transformation process:

**Import → Transform → Derive → Categorize → Validate → Load**

## Skills Focused

`Power Query` • `Column From Examples` • `Conditional Column` • `M Logic` • `Data Profiling` • `Data Transformation` • `Data Cleaning` • `Power BI`
