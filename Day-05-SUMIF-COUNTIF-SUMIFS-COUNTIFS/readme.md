# 📊 SUMIF, COUNTIF, SUMIFS & COUNTIFS for Data Analytics

## 📌 Overview

This module focuses on four important **conditional analytical formulas**:

* `SUMIF`
* `COUNTIF`
* `SUMIFS`
* `COUNTIFS`

These formulas help answer business questions by calculating or counting records that satisfy specific conditions.

The objective is not simply to memorize syntax, but to understand how to convert:

**Business Question → Conditions → Calculation → Insight → Decision**

---

## 🎯 Concepts Covered

* What are analytical formulas?
* SUMIF with practical scenarios
* COUNTIF with practical scenarios
* SUMIFS with multiple criteria
* COUNTIFS with multiple criteria
* SUMIF vs SUMIFS
* COUNTIF vs COUNTIFS
* Criteria and logical operators
* Business applications
* Hands-on analytical practice

---

# 1️⃣ SUMIF — Sum Based on One Condition

`SUMIF` adds values when a **single condition** is satisfied.

### Syntax

```excel
=SUMIF(range, criteria, sum_range)
```

### Example Dataset

| Product | Sales |
| ------- | ----: |
| Laptop  | 12000 |
| Phone   |  8500 |
| Tablet  |  6000 |
| Laptop  | 15000 |

### Business Question

**What are the total Laptop sales?**

```excel
=SUMIF(A2:A5,"Laptop",B2:B5)
```

### Result

`27,000`

### Analytics Use

Useful for:

* Sales by product
* Revenue by region
* Expenses by category
* Orders by customer segment

---

# 2️⃣ COUNTIF — Count Based on One Condition

`COUNTIF` counts records satisfying **one condition**.

### Syntax

```excel
=COUNTIF(range, criteria)
```

### Example

| Student | Marks |
| ------- | ----: |
| Aditi   |    85 |
| Rohan   |    45 |
| Kavya   |    78 |
| Arjun   |    92 |
| Meera   |    38 |

### Business Question

**How many students scored 50 or above?**

```excel
=COUNTIF(B2:B6,">=50")
```

### Result

`3`

This same logic can be applied to employee targets, order statuses, customer categories, inventory levels, and other datasets.

---

# 3️⃣ SUMIFS — Sum Using Multiple Conditions

`SUMIFS` adds values when **multiple conditions** are satisfied.

### Syntax

```excel
=SUMIFS(sum_range, criteria_range1, criteria1,
        criteria_range2, criteria2)
```

### Example

| Product | Region | Sales |
| ------- | ------ | ----: |
| Laptop  | East   | 12000 |
| Laptop  | West   |  9000 |
| Phone   | East   |  8500 |
| Laptop  | East   | 15000 |

### Business Question

**What are total Laptop sales in the East region?**

```excel
=SUMIFS(C2:C5,A2:A5,"Laptop",B2:B5,"East")
```

### Result

`27,000`

This is useful when analysis requires combinations such as:

`Product + Region`
`Department + Month`
`Category + Customer Type`
`Region + Year + Status`

---

# 4️⃣ COUNTIFS — Count Using Multiple Conditions

`COUNTIFS` counts records that satisfy **multiple criteria**.

### Syntax

```excel
=COUNTIFS(criteria_range1,criteria1,
          criteria_range2,criteria2)
```

### Example

| Employee | Department | Status   |
| -------- | ---------- | -------- |
| John     | IT         | Active   |
| Sneha    | HR         | Active   |
| Rohan    | IT         | Inactive |
| Meera    | IT         | Active   |
| Karthik  | HR         | Inactive |

### Business Question

**How many IT employees are Active?**

```excel
=COUNTIFS(B2:B6,"IT",C2:C6,"Active")
```

### Result

`2`

---

# 🔄 SUMIF vs SUMIFS

| Feature                    | SUMIF   | SUMIFS   |
| -------------------------- | ------- | -------- |
| Operation                  | Sum     | Sum      |
| Conditions                 | One     | Multiple |
| Simple Analysis            | ✅       | ✅        |
| Multi-dimensional Analysis | Limited | ✅        |

**One condition → SUMIF**

**Multiple conditions → SUMIFS**

---

# 🔄 COUNTIF vs COUNTIFS

| Feature                 | COUNTIF | COUNTIFS |
| ----------------------- | ------- | -------- |
| Operation               | Count   | Count    |
| Conditions              | One     | Multiple |
| Simple Counting         | ✅       | ✅        |
| Multi-criteria Counting | Limited | ✅        |

**One condition → COUNTIF**

**Multiple conditions → COUNTIFS**

---

# 💼 Real-World Analytics Applications

### 📈 Sales Analysis

* Sales by product
* Revenue by region
* Sales above a threshold
* Monthly/category performance

### 👥 Employee Analysis

* Active employees
* Employees meeting targets
* Department-level headcount
* Performance categories

### 📦 Product Analysis

* Revenue by category
* Products below stock thresholds
* Orders by product type

### 👤 Customer Analysis

* Customers by region
* Premium customers
* Active customers within specific segments

### 📅 Performance Tracking

* Monthly target achievement
* Completed transactions
* Department performance
* KPI-based counts

---

# 🧠 Analyst Thinking

Before selecting a formula, ask:

### What calculation do I need?

**Add values? → SUM**

**Count records? → COUNT**

Then ask:

### How many conditions?

**One → IF**

**Multiple → IFS**

This creates a simple decision framework:

```text
                 Business Question
                        ↓
                What do I need?
                  ↙           ↘
                SUM          COUNT
                 ↓             ↓
         How many conditions?
              ↙       ↘
            ONE       MULTIPLE
             ↓           ↓
          SUMIF        SUMIFS

          COUNTIF      COUNTIFS
```

---

# 📊 Why These Formulas Matter

Conditional formulas help analysts:

* Filter calculations logically
* Analyze subsets of larger datasets
* Answer business questions quickly
* Reduce manual calculations
* Build repeatable reports
* Track KPIs
* Compare segments
* Identify trends and exceptions

Most importantly, they develop the ability to translate a **business requirement into analytical conditions**.

---

# 🔑 Key Takeaway

The real skill is not remembering:

`SUMIF`, `COUNTIF`, `SUMIFS`, or `COUNTIFS`.

The real skill is knowing **which question to ask, which conditions matter, and which calculation produces the answer.**

> **Raw Data → Business Question → Analytical Logic → Result → Insight**

---

## 🚀 Learning Journey

`IF & Nested IF` ✅
↓
`SUMIF & COUNTIF` ✅
↓
`SUMIFS & COUNTIFS` ✅
↓
`Lookup & Reference Functions` 🔄
↓
`Data Cleaning`
↓
`PivotTables`
↓
`Power Query`
↓
`Dashboards & Business Projects`

### Learning Approach

**Understand → Practice → Apply → Analyze → Communicate 🚀**
