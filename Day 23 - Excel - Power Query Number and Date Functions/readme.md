# 📊 Power Query Number & Date Functions

## Overview

Power Query provides built-in **Number and Date functions** for transforming raw columns into analysis-ready metrics.

These transformations are stored as query steps, allowing the same logic to run automatically whenever the source data is refreshed.

**Source Data → Transform → Calculate → Validate → Load → Analyze**

---

## 🔢 1. Number Functions

### Basic Arithmetic

Custom columns can perform standard calculations.

```powerquery
[Sales] + [Tax]
```

```powerquery
[Revenue] - [Cost]
```

```powerquery
[Quantity] * [UnitPrice]
```

### Percentage

Example: calculate margin percentage.

```powerquery
([Revenue] - [Cost]) / [Revenue] * 100
```

### Modulo

Returns the remainder after division.

```powerquery
Number.Mod([Value], 2)
```

Useful for identifying even/odd patterns.

### Sign

```powerquery
Number.Sign([Profit])
```

Returns:

```text
1  = Positive
0  = Zero
-1 = Negative
```

### Rounding

```powerquery
Number.Round([Amount], 2)
```

```powerquery
Number.RoundUp([Amount], 0)
```

```powerquery
Number.RoundDown([Amount], 0)
```

### Advanced Math

```powerquery
Number.Power([Value], 2)
```

```powerquery
Number.Exp([Value])
```

```powerquery
Number.Log([Value])
```

```powerquery
Number.Sqrt([Value])
```

### Trigonometry

```powerquery
Number.Sin([Angle])
```

```powerquery
Number.Cos([Angle])
```

```powerquery
Number.Tan([Angle])
```

Trigonometric functions use radians.

---

# 📅 2. Date Functions

## Extract Date Parts

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

### Day

```powerquery
Date.Day([OrderDate])
```

---

## Month & Day Names

```powerquery
Date.MonthName([OrderDate])
```

```powerquery
Date.DayOfWeekName([OrderDate])
```

These are useful for reporting dimensions such as:

```text
January
February
Monday
Tuesday
```

---

## Additional Date Information

### Day of Week

```powerquery
Date.DayOfWeek([OrderDate])
```

### Day of Year

```powerquery
Date.DayOfYear([OrderDate])
```

### Week of Year

```powerquery
Date.WeekOfYear([OrderDate])
```

### Week of Month

```powerquery
Date.WeekOfMonth([OrderDate])
```

---

# ⏱️ 3. Difference Between Dates

Subtracting two dates creates a **Duration** value.

```powerquery
[EndDate] - [StartDate]
```

### Difference in Days

```powerquery
Duration.Days([EndDate] - [StartDate])
```

Example:

```text
Start Date: 01-Jan-2026
End Date:   31-Jan-2026

Difference = 30 Days
```

### Total Hours

```powerquery
Duration.TotalHours([EndDateTime] - [StartDateTime])
```

### Total Minutes

```powerquery
Duration.TotalMinutes([EndDateTime] - [StartDateTime])
```

### Total Seconds

```powerquery
Duration.TotalSeconds([EndDateTime] - [StartDateTime])
```

---

# 🕒 4. Extract Date from DateTime

A DateTime value may contain:

```text
2026-10-19 14:30:00
```

Extract only the date using:

```powerquery
Date.From([DateTime])
```

Result:

```text
2026-10-19
```

---

# 📆 5. Earliest & Latest Dates

For a date list:

```powerquery
List.Min(#"Previous Step"[OrderDate])
```

returns the earliest date.

```powerquery
List.Max(#"Previous Step"[OrderDate])
```

returns the latest date.

Useful for:

- First transaction date
- Latest order
- Dataset coverage
- Customer activity periods

---

# 💼 6. Business Applications

## Sales Analysis

Create:

```text
Year
Quarter
Month
Month Name
Week
```

from one transaction date.

This makes monthly, quarterly, and yearly reporting easier.

## Turnaround-Time Analysis

```powerquery
Duration.Days([DeliveryDate] - [OrderDate])
```

Useful for:

- Delivery performance
- Service turnaround time
- SLA analysis

## Financial Analysis

Number functions can support:

- Margin calculations
- Growth percentages
- Rounded financial values
- Pricing calculations
- Interest-related transformations

## Customer Analysis

Date functions can support:

- Customer tenure
- Time since last transaction
- Customer activity periods
- Cohort preparation

---

# 🔄 7. Why Power Query Is Useful

The transformation logic is repeatable.

```text
RAW DATA
   ↓
NUMBER / DATE TRANSFORMATIONS
   ↓
CLEAN DATASET
   ↓
REFRESH
   ↓
SAME STEPS REAPPLIED
   ↓
UPDATED REPORT
```

This reduces repeated manual calculations.

---

# ✅ 8. Validation Checklist

Before loading transformed data:

- Confirm numeric data types
- Check null values
- Validate date formats
- Verify duration calculations
- Check percentage logic
- Review rounding requirements
- Compare sample calculations manually
- Confirm business definitions

---

# 💡 Key Takeaway

Power Query Number and Date functions help convert raw fields into meaningful analytical dimensions and measures.

The value is not only the calculation itself.

The value comes from creating a **consistent transformation process that can be refreshed and reused.**

### Workflow

**Import → Clean → Transform → Calculate → Validate → Load → Analyze**

---

## 🛠 Skills Focused

`Power Query` • `Number Functions` • `Date Functions` • `Duration` • `Data Transformation` • `Date Analysis` • `Business Analytics` • `Data Preparation`
