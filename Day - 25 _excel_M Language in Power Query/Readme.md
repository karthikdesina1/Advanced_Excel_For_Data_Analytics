# 💻 M Language in Power Query

## Overview

**M Language** is the formula language behind Power Query.

Every transformation performed through the Power Query interface is translated into M code.

Understanding M helps with:

- Custom transformations
- Editing generated steps
- Troubleshooting queries
- Reusing logic
- Building more flexible data workflows

Typical structure:

```powerquery
let
    Source = ...,
    Transformed = ...
in
    Transformed
```

---

## 1. M Language Basics

Power Query uses a sequence of named steps.

Example:

```powerquery
let
    Source = Excel.CurrentWorkbook(){[Name="SalesData"]}[Content],
    ChangedType = Table.TransformColumnTypes(
        Source,
        {{"OrderDate", type date}, {"Sales", type number}}
    )
in
    ChangedType
```

Each step usually references the previous step.

---

## 2. Date.IsIn Functions

These functions help identify whether a date belongs to a specific relative period.

### Current Month

```powerquery
Date.IsInCurrentMonth([OrderDate])
```

### Previous Month

```powerquery
Date.IsInPreviousMonth([OrderDate])
```

### Current Year

```powerquery
Date.IsInCurrentYear([OrderDate])
```

### Example Custom Column

```powerquery
if Date.IsInCurrentMonth([OrderDate])
then "Current Month"
else "Other"
```

Useful for:

- Monthly reporting
- Period filtering
- Current-vs-prior analysis

---

## 3. Date Add / Subtract

### Add Days

```powerquery
Date.AddDays([OrderDate], 7)
```

### Add Months

```powerquery
Date.AddMonths([OrderDate], 1)
```

### Add Years

```powerquery
Date.AddYears([OrderDate], 1)
```

### Subtract Time

Use negative values:

```powerquery
Date.AddDays([OrderDate], -7)
```

```powerquery
Date.AddMonths([OrderDate], -1)
```

Applications include:

- Due dates
- Renewal dates
- Previous-period comparisons
- Scheduling logic

---

## 4. Date Components

### Year

```powerquery
Date.Year([OrderDate])
```

### Quarter

```powerquery
Date.QuarterOfYear([OrderDate])
```

### Month

```powerquery
Date.Month([OrderDate])
```

### Month Name

```powerquery
Date.MonthName([OrderDate])
```

### Week of Year

```powerquery
Date.WeekOfYear([OrderDate])
```

### Day

```powerquery
Date.Day([OrderDate])
```

### Day Name

```powerquery
Date.DayOfWeekName([OrderDate])
```

These transformations help create reporting fields for time-based analysis.

---

## 5. Basic Text Functions

M includes useful functions for cleaning and standardizing text.

### Uppercase

```powerquery
Text.Upper([Name])
```

### Lowercase

```powerquery
Text.Lower([Email])
```

### Remove Extra Spaces

```powerquery
Text.Trim([Region])
```

### Text Length

```powerquery
Text.Length([Code])
```

### Extract Beginning Characters

```powerquery
Text.Start([ProductCode], 3)
```

### Extract Ending Characters

```powerquery
Text.End([ProductCode], 2)
```

### Replace Text

```powerquery
Text.Replace([Status], "Pending", "Open")
```

---

## 6. Writing M Code in Advanced Editor

The **Advanced Editor** allows direct editing of the entire query.

Example:

```powerquery
let
    Source = Excel.CurrentWorkbook(){[Name="SalesData"]}[Content],

    ChangedType =
        Table.TransformColumnTypes(
            Source,
            {
                {"OrderDate", type date},
                {"Region", type text},
                {"Sales", type number}
            }
        ),

    CleanRegion =
        Table.TransformColumns(
            ChangedType,
            {{"Region", Text.Trim}}
        ),

    AddedYear =
        Table.AddColumn(
            CleanRegion,
            "Year",
            each Date.Year([OrderDate]),
            Int64.Type
        )
in
    AddedYear
```

This sequence:

1. Loads data
2. Sets data types
3. Cleans Region text
4. Creates a Year column
5. Returns the final table

---

## 7. Exploring M Functions with `#shared`

In a blank query, enter:

```powerquery
#shared
```

This returns a record containing functions and other values available in the M environment.

It can be converted to a table for easier exploration.

This is useful when discovering functions for:

- Dates
- Text
- Numbers
- Tables
- Lists
- Records
- Files
- Web data

---

## 8. Why M Matters

Using only the Power Query interface is enough for many tasks.

M becomes especially useful when:

- A transformation needs custom logic
- Generated steps need modification
- Repetitive logic should be reused
- Complex conditions are required
- Queries need troubleshooting
- Standard transformations are not enough

---

## 9. Practical Workflow

```text
SOURCE DATA
    ↓
POWER QUERY
    ↓
GENERATED M STEPS
    ↓
CUSTOM M LOGIC
    ↓
VALIDATION
    ↓
REFRESHABLE OUTPUT
    ↓
ANALYSIS
```

---

## Key Takeaway

M Language helps move Power Query from a point-and-click transformation tool into a more customizable data-preparation environment.

The goal is not to memorize every function.

The goal is to understand:

**Source → Step → Transformation → Result**

and know when custom M logic is useful.

### Skills Focused

`M Language` • `Power Query` • `Date Functions` • `Text Functions` • `Advanced Editor` • `Custom Columns` • `Data Transformation` • `#shared`
