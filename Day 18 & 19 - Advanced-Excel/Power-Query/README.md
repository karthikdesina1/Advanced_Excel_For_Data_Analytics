# 📊 Power Query in Excel - Data Cleaning & Transformation

## 📌 Overview

Power Query is a data preparation and transformation tool available in Excel and Power BI.

It enables analysts to connect to different data sources, clean messy datasets, transform information, and build repeatable workflows.

**Workflow: Import → Clean → Transform → Validate → Load → Refresh**

Unlike repetitive manual cleaning, Power Query records transformation steps that can be reused when source data changes.

---

## 🎯 Concepts Focused

- Introduction to Power Query
- Importing data from multiple sources
- Power Query Editor
- Removing duplicates and errors
- Handling NULL and missing values
- Filtering and sorting
- Changing data types
- Splitting and merging columns
- Combining datasets
- Loading and refreshing queries
- Automating repetitive data preparation

---

## 1. What Is Power Query?

Power Query is Microsoft's data transformation and preparation technology.

It follows an ETL-style workflow:

**Extract → Transform → Load**

### Why Use Power Query?

- Reduce repetitive manual cleaning
- Combine multiple data sources
- Standardize inconsistent information
- Improve data preparation efficiency
- Create refreshable transformations
- Prepare structured datasets for analysis

---

## 2. Supported Data Sources

Power Query can connect to:

| Source | Example |
|---|---|
| Excel | Sales.xlsx |
| CSV | Orders.csv |
| Web | Online tables or supported APIs |
| Folder | Multiple monthly reports |
| Database | SQL Server |
| Text | TXT files |
| JSON | Structured JSON records |
| SharePoint | Shared organizational files |

Available connectors depend on the Excel version and environment.

---

## 3. Power Query Editor

Power Query Editor provides an interface for building transformation workflows.

### Important Components

- Queries Pane
- Data Preview
- Applied Steps
- Query Settings
- Formula Bar
- Home Tab
- Transform Tab
- Add Column Tab

### Applied Steps

Each transformation is recorded as a step.

Example:

```text
Source
  ↓
Promoted Headers
  ↓
Changed Type
  ↓
Removed Duplicates
  ↓
Filtered Rows
  ↓
Replaced Values
  ↓
Final Dataset
```

These steps can run again during refresh.

---

## 4. Data Cleaning Operations

### Remove Duplicates

Remove repeated records based on selected columns.

**Important:** Identify the correct business key before removing duplicates.

### Remove Errors

Identify and investigate invalid values before deciding whether to remove or replace them.

### Handle Missing Values

Common approaches:

- Replace NULL values
- Remove incomplete rows when appropriate
- Fill Down / Fill Up
- Preserve missing values when meaningful

### Filter & Sort

Filter records based on business requirements and sort values for inspection.

### Change Data Types

Examples:

- Text
- Whole Number
- Decimal Number
- Date
- Date/Time
- True/False

Correct data types are essential for reliable calculations.

---

## 5. Data Transformation

### Split Columns

Example:

```text
Before:
John,Smith

After:
First Name | Last Name
John       | Smith
```

### Merge Columns

Combine multiple fields into one.

Example:

```text
First Name + Last Name
         ↓
      Full Name
```

### Rename Columns

Standardize column names across datasets.

### Custom Columns

Create calculated fields using Power Query's M language.

Example:

```powerquery
[Quantity] * [UnitPrice]
```

This calculates revenue for each row when both fields contain valid numeric values.

---

## 6. Merge vs Append Queries

### Merge Queries

Combines related tables using matching keys, similar to a database join.

Example:

```text
Sales Table + Product Master
              ↓
        Merge by Product ID
              ↓
       Enriched Sales Data
```

### Append Queries

Stacks rows from multiple tables.

Example:

```text
January Sales
February Sales
March Sales
      ↓
Append Queries
      ↓
Combined Sales Dataset
```

---

## 7. Power Query M Language

Power Query uses the M language to define transformations.

### Remove Duplicates

```powerquery
Table.Distinct(Source, {"OrderID"})
```

### Remove Blank IDs

```powerquery
Table.SelectRows(Source,
 each [OrderID] <> null and [OrderID] <> "")
```

### Change Data Type

```powerquery
Table.TransformColumnTypes(
 Source,
 {{"Revenue", type number}}
)
```

### Add Revenue Column

```powerquery
Table.AddColumn(
 Source,
 "Revenue",
 each [Quantity] * [UnitPrice],
 type number
)
```

### Filter Rows

```powerquery
Table.SelectRows(
 Source,
 each [Region] = "East"
)
```

These examples assume the referenced columns exist.

---

## 8. Load & Refresh

After transforming data, Power Query can load results to:

- Excel Worksheet Tables
- Excel Data Model
- Connection Only

### Refresh Process

```text
Source Data Updated
        ↓
Refresh Query
        ↓
Reapply Transformation Steps
        ↓
Updated Output
        ↓
Validate Results
```

Refresh requires the source to remain accessible and compatible with the query steps.

---

## 9. Real-World Business Case

### Scenario: Monthly Sales Consolidation

A company receives monthly sales files from multiple regional offices.

### Challenges

- Duplicate transactions
- Missing customer information
- Inconsistent date formats
- Different column names
- Multiple source files

### Solution

**Step 1:** Connect to the folder containing sales files.

**Step 2:** Combine compatible files.

**Step 3:** Standardize headers and data types.

**Step 4:** Investigate missing values and duplicates.

**Step 5:** Create calculated revenue fields.

**Step 6:** Validate row counts and financial totals.

**Step 7:** Load the prepared dataset.

**Step 8:** Refresh when new reports arrive.

### Business Outcome

- Reduced manual preparation
- More consistent reporting
- Reusable transformation steps
- Faster monthly analysis
- Better data quality checks

---

## 10. Data Quality Checklist

- [ ] Verify source files
- [ ] Confirm column names
- [ ] Check data types
- [ ] Investigate duplicate records
- [ ] Review NULL values
- [ ] Validate date formats
- [ ] Check transformation errors
- [ ] Compare row counts
- [ ] Reconcile important totals
- [ ] Refresh and validate output

---

## 💡 Key Takeaway

Power Query helps transform raw business data into structured, reusable, analysis-ready datasets.

It is especially valuable when the same cleaning and transformation process must be repeated regularly.

**Import → Clean → Transform → Validate → Load → Refresh → Analyze**

## 🛠️ Skills Focused

`Power Query` • `ETL` • `Data Cleaning` • `Data Transformation` • `Data Preparation` • `M Language` • `Merge Queries` • `Append Queries` • `Data Validation` • `Business Analytics`
