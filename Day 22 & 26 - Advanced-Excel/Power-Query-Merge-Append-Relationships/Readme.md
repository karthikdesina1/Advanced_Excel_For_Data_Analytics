# 🔗 Power Query - Merge, Append & Relationships

## 📌 Overview
Power Query in Excel enables analysts to connect, clean, transform, and combine business datasets from multiple sources.

**Workflow:** Connect → Transform → Append/Merge → Validate → Load → Refresh

## 1. Power Query Basics
**Excel Path:** Data → Get Data → Power Query Editor

### Supported Sources
- Excel and CSV
- Web and databases
- Folders
- Text and JSON
- SharePoint and other supported connectors

### Home Tab Tools
- New Source / Recent Sources
- Data Source Settings
- Choose / Remove Columns
- Keep / Remove Rows
- Replace Values
- Merge Queries
- Append Queries
- Close & Load

## 2. Append vs Merge

| Feature | Append | Merge |
|---|---|---|
| Operation | Stack rows | Join related tables |
| Direction | Vertical | Adds related columns |
| Matching key | Not required | Required |
| Example | Monthly sales | Sales + Customers |
| Result | Combined records | Enriched records |

### Append Example

January:
| ID | Sales |
|---|---:|
| 101 | 500 |

February:
| ID | Sales |
|---|---:|
| 102 | 800 |

**Appended Result:**
| ID | Sales |
|---|---:|
| 101 | 500 |
| 102 | 800 |

Append matches columns by name. Missing columns produce null values.

## 3. Append vs Append as New

**Append Queries:** Adds the append operation to the selected existing query.

**Append Queries as New:** Creates a separate combined query while keeping source queries unchanged.

### Interview Question
**Q: What is the difference?**

Both combine rows. The difference is whether the operation modifies an existing query or creates a new query.

## 4. Merge Queries — Join Types

Consider:

**Customers:** IDs 1, 2, 3

**Orders:** IDs 2, 3, 4

| Join | Returned IDs |
|---|---|
| Left Outer | 1, 2, 3 |
| Right Outer | 2, 3, 4 |
| Inner | 2, 3 |
| Full Outer | 1, 2, 3, 4 |

- **Left Outer:** Keep every left row.
- **Right Outer:** Keep every right row.
- **Inner:** Keep matching rows only.
- **Full Outer:** Keep matched and unmatched rows from both sources.

**Note:** Duplicate matching keys can produce multiple matching rows.

## 5. Merge Using Multiple Columns

Corporate datasets may require composite keys.

Example:
`ProductID + TransactionDate`

### Steps
1. Open Merge Queries.
2. Select the first table.
3. Select ProductID and TransactionDate.
4. Select the corresponding columns in the second table in the same order.
5. Choose the join kind.
6. Expand the required columns.
7. Validate matching results.

Ensure matching columns use compatible data types.

## 6. Expand vs Aggregate

### Expand
Retrieves columns from the nested table created by Merge.

Example:
`Sales + ProductMaster → Sales + ProductName + Category`

**Column Prefix:** Power Query can prefix expanded column names with the source query/column name to prevent naming conflicts.

### Aggregate
Summarizes related records without expanding every matching row.

Examples:
- Count related orders
- Sum sales amounts
- Find minimum or maximum values

## 7. Power Query M Examples

### Append Two Tables
```powerquery
Table.Combine({JanuarySales, FebruarySales})
```

### Left Outer Merge
```powerquery
Table.NestedJoin(
 Sales, {"CustomerID"},
 Customers, {"CustomerID"},
 "CustomerData", JoinKind.LeftOuter
)
```

### Inner Join
```powerquery
Table.NestedJoin(
 Sales, {"CustomerID"},
 Customers, {"CustomerID"},
 "CustomerData", JoinKind.Inner
)
```

### Multi-Column Merge
```powerquery
Table.NestedJoin(
 Sales, {"ProductID","Date"},
 Products, {"ProductID","Date"},
 "ProductData", JoinKind.LeftOuter
)
```

### Expand Merged Columns
```powerquery
Table.ExpandTableColumn(
 MergedQuery,
 "CustomerData",
 {"CustomerName","Region"},
 {"CustomerName","Region"}
)
```

These examples assume the referenced queries and columns exist.

## 8. Folder Integration

**Business Case:** Combine monthly corporate sales files.

### Steps
1. Data → Get Data → From Folder
2. Select the source folder.
3. Choose Combine & Transform.
4. Inspect the sample-file transformation.
5. Standardize data types and headers.
6. Remove unwanted columns.
7. Validate the combined data.
8. Load the output into Excel.
9. Refresh when new compatible files arrive.

### Workflow
```text
Jan.xlsx + Feb.xlsx + Mar.xlsx
              ↓
         Folder Source
              ↓
       Combine & Transform
              ↓
        Clean / Validate
              ↓
        Consolidated Sales
              ↓
          Refreshable Report
```

## 9. Relationships — Data Model

Power Query Merge physically enriches query results with related data.

Data Model Relationships connect separate tables using common fields without necessarily merging them into one table.

Example:
```text
Customers (1)
     |
     | CustomerID
     ↓
Sales (*)
     ↑
     | ProductID
     |
Products (1)
```

Use relationships for multi-table PivotTables and structured analytical models.

## 10. Corporate Data Quality Checklist

- [ ] Verify source connections
- [ ] Standardize column names
- [ ] Confirm matching data types
- [ ] Check duplicate keys
- [ ] Validate join selection
- [ ] Inspect unmatched records
- [ ] Check row counts after Merge
- [ ] Verify totals after Append
- [ ] Review expanded columns
- [ ] Refresh and validate results

## 11. Interview Questions

**Q1: Append vs Merge?**
Append stacks rows; Merge joins related tables using matching keys.

**Q2: Append vs Append as New?**
Existing query modification vs separate new query.

**Q3: What is Left Outer Join?**
All left rows with matching right-side information.

**Q4: Can Merge use multiple columns?**
Yes, by selecting matching columns in the same order.

**Q5: Expand vs Aggregate?**
Expand retrieves detailed columns; Aggregate summarizes related records.

**Q6: Merge vs Relationship?**
Merge combines data within a query; relationships connect tables in the Data Model.

**Q7: Can folder queries update automatically?**
Queries can include newly added compatible files when refreshed. Scheduled refresh requires additional configuration or supported services.

## 💡 Key Takeaway

**Append = Combine Rows**

**Merge = Connect Related Data**

**Relationships = Link Tables in a Data Model**

Together, these techniques support reusable, scalable, and reliable corporate data preparation.

### Skills Focused
`Power Query` • `Append` • `Merge` • `Join Types` • `Composite Keys` • `Expand` • `Aggregate` • `Folder Integration` • `Data Model` • `ETL`
