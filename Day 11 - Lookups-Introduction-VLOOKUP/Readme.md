# 🔍 Lookups in Excel - Introduction & VLOOKUP

## 📌 Overview

Business data is often distributed across different tables, worksheets, and files.

**Lookup functions** help find a value in one location and retrieve related information from another.

The fundamental idea is:

**Search → Match → Retrieve → Connect → Analyze**

This module introduces lookup concepts with a primary focus on **VLOOKUP**.

---

## 🎯 Concepts Focused

- What are Lookups?
- Why are Lookups useful?
- Workbook-to-workbook lookup
- Worksheet-to-worksheet lookup
- Same-sheet lookup
- VLOOKUP
- HLOOKUP
- XLOOKUP
- VLOOKUP syntax
- Exact vs Approximate Match
- Multiple-criteria lookup concepts
- VLOOKUP limitations
- Common lookup errors
- Useful selection shortcut

---

# 1️⃣ What is a Lookup?

A Lookup searches for a specific value and retrieves related information.

### Example

Suppose we know:

```text
Employee ID = 103
```

Another table contains:

| ID | Name | Department |
|---|---|---|
| 101 | John | Sales |
| 102 | Jane | HR |
| 103 | Mike | Finance |

A lookup can search for `103` and return:

```text
Finance
```

Conceptually:

```text
Employee ID
     ↓
Find Matching Record
     ↓
Return Department
```

---

# 2️⃣ Why Use Lookups?

Lookups help analysts:

- Connect related datasets
- Reduce manual searching
- Retrieve information automatically
- Maintain consistent reporting
- Enrich transactional datasets
- Support data cleaning
- Build reports and dashboards

### Business Examples

```text
Employee ID → Department
Product ID  → Category
Customer ID → Segment
Order ID    → Status
Product SKU → Price
```

---

# 3️⃣ Common Lookup Scenarios

### 📁 Workbook → Workbook

Retrieve information stored in another workbook.

### 📄 Worksheet → Worksheet

Use a value from one worksheet to retrieve information from another sheet.

### 📊 Same Sheet → Same Sheet

Search another table within the same worksheet.

These scenarios are common in reporting and data preparation.

---

# 4️⃣ Types of Lookups

## VLOOKUP

Searches vertically through the first column of a table.

## HLOOKUP

Searches horizontally across the first row.

## XLOOKUP

Provides a more flexible approach and can search in different directions.

This module primarily focuses on **VLOOKUP fundamentals**.

---

# 5️⃣ VLOOKUP Syntax

```excel
=VLOOKUP(lookup_value, table_array, col_index_num, [range_lookup])
```

### Arguments

| Argument | Purpose |
|---|---|
| `lookup_value` | Value being searched |
| `table_array` | Table containing the lookup data |
| `col_index_num` | Column containing the result |
| `range_lookup` | Exact or approximate matching |

---

# 6️⃣ VLOOKUP Example

Consider:

| ID | Name | Department | City |
|---|---|---|---|
| 101 | John Doe | Sales | New York |
| 102 | Jane Smith | HR | Chicago |
| 103 | Mike Brown | Finance | Dallas |
| 104 | Sara Lee | IT | Seattle |

To retrieve the **Department** for the ID stored in `A2`:

```excel
=VLOOKUP(A2,$A$2:$D$5,3,FALSE)
```

### Logic

```text
A2
 ↓
Find ID in first column
 ↓
Move to column 3
 ↓
Return Department
```

---

# 7️⃣ Exact vs Approximate Match

## 🎯 Exact Match — FALSE / 0

```excel
=VLOOKUP(A2,$A$2:$D$5,3,FALSE)
```

Returns a result only when an exact match exists.

Useful for:

- Employee IDs
- Product IDs
- Customer IDs
- Order numbers
- Unique codes

---

## 📈 Approximate Match — TRUE / 1

```excel
=VLOOKUP(A2,$A$2:$B$6,2,TRUE)
```

Returns an approximate match based on the lookup range.

Common scenarios include:

- Grade ranges
- Commission bands
- Pricing tiers
- Tax brackets

⚠️ Approximate matching requires careful setup, including properly ordered lookup values.

---

# 8️⃣ VLOOKUP Limitation

VLOOKUP searches in the **first column of the selected table** and retrieves information from columns to its right.

Example:

```text
ID → Name → Department → City
↑                    →
Lookup              Return
```

It cannot natively retrieve a value located to the **left** of the lookup column.

This is one reason modern alternatives such as **XLOOKUP** can be useful.

---

# 9️⃣ Multiple-Criteria Concept

Sometimes one field is not enough to uniquely identify a record.

Example:

```text
Employee ID + Product
```

A helper column can combine values:

```excel
=A2&"-"&B2
```

Example result:

```text
101-Laptop
101-Mouse
102-Laptop
```

The combined key can then be used for lookup operations.

---

# 🔟 Common VLOOKUP Errors

### `#N/A`

The lookup value could not be found.

Check:

- Spelling
- Extra spaces
- Exact-match setting
- Data type consistency

### `#VALUE!`

Often indicates an invalid argument or incompatible value.

### `#REF!`

Often occurs when the requested column index is outside the selected lookup table.

---

# ⌨️ Useful Shortcut

To quickly select cells downward in a contiguous data region:

```text
Ctrl + Shift + ↓
```

This is useful when working with larger lookup tables.

---

# 💼 Analytics Perspective

Lookups become especially valuable when information needs to be combined from different sources.

Example:

```text
SALES DATA
Product ID | Quantity | Revenue
             +
PRODUCT MASTER
Product ID | Product | Category
             ↓
           LOOKUP
             ↓
ENRICHED SALES DATA
Product ID | Product | Category | Quantity | Revenue
             ↓
           ANALYSIS
```

This allows analysts to add meaningful business context to transactional data.

---

# 💡 Key Takeaway

The important skill isn't simply memorizing:

```excel
=VLOOKUP(...)
```

It is understanding:

**What value am I looking for?**

**Where does the matching data exist?**

**What information should be returned?**

**Do I need an exact or approximate match?**

Once those questions are clear, the formula becomes much easier to build.

> **Lookups connect scattered data and turn individual records into more complete information.**

---

## 🛠️ Skills Practiced

VLOOKUP • Lookup Logic • Exact Match • Approximate Match • Cross-Sheet Lookups • Cross-Workbook Lookups • Error Troubleshooting • Data Preparation • Data Analysis

### Learning Approach

**Find → Match → Retrieve → Validate → Analyze 🚀**
