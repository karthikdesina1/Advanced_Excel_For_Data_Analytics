# 🧹 Data Validation & Data Cleaning for Analytics

## 📌 Overview

Before asking **“What does the data tell us?”**, an analyst should first ask:

> **“Can I trust this data?”**

This module focuses on **Data Validation and Data Cleaning**—the process of identifying quality issues, correcting inconsistencies, structuring information, applying business rules, and preparing reliable data for analysis.

Depending on the organization, detailed data preparation may be performed by Data Analysts, Data Engineers, Business Analysts, or shared across the data team.

From a **Business Analyst perspective**, even when I do not own the complete cleaning pipeline, I should understand and validate the quality of the data supporting my analysis, requirements, KPIs, and recommendations.

---

## 🔄 Data Quality Workflow

```text
RAW DATA
   ↓
INSPECT
   ↓
IDENTIFY ISSUES
   ↓
CLEAN
   ↓
TRANSFORM
   ↓
VALIDATE
   ↓
VERIFY
   ↓
ANALYSIS-READY DATA
   ↓
BUSINESS INSIGHTS
```

---

## 🎯 Concepts Focused

* Identify duplicates using single & multiple columns
* Remove exact and partial duplicates
* Apply Data Validation rules
* Use Stop, Warning & Information alerts
* Filter records for investigation
* Split fields using Text to Columns
* Standardize date formats
* Use text functions
* Split email addresses
* Split full names
* Verify data before analysis

---

# 1️⃣ Duplicate Detection

Duplicate records can distort:

* Customer counts
* Revenue calculations
* Transaction volumes
* KPI results
* Reporting accuracy

Duplicates should therefore be investigated before analysis.

### Example

```text
Before

101 | John Doe | john@gmail.com
102 | Jane     | jane@outlook.com
101 | John Doe | john@gmail.com
```

After validation:

```text
101 | John Doe | john@gmail.com
102 | Jane     | jane@outlook.com
```

Duplicates can be identified using either a **single field** or a combination of fields depending on the business definition of a unique record.

---

# 2️⃣ Data Validation

Data Validation helps control what users are allowed to enter.

Common validation types include:

```text
Any Value
List
Date
Custom
```

### Example — Region

Instead of allowing inconsistent entries:

```text
East
east
EAST
Eest
```

a controlled list can restrict entries to:

```text
East
West
North
South
```

This improves consistency at the **point of data entry**.

---

# 3️⃣ Validation Alerts

Validation rules can produce different responses.

### 🛑 Stop

Blocks invalid input.

### ⚠️ Warning

Warns the user but can allow the entry.

### ℹ️ Information

Provides information about the entered value.

The appropriate option depends on the underlying **business rule and severity of the error**.

---

# 4️⃣ Text to Columns

Combined information can be separated into structured fields.

### Before

```text
John,Doe
Jane,Smith
Mike,Brown
```

### After

| First Name | Last Name |
| ---------- | --------- |
| John       | Doe       |
| Jane       | Smith     |
| Mike       | Brown     |

Structured fields make filtering, grouping, reporting, and analysis easier.

---

# 5️⃣ Standardizing Dates

Real datasets may contain dates such as:

```text
1/5/2026
05-01-2026
Jan 5, 2026
```

Inconsistent date handling can affect:

* Sorting
* Filtering
* Monthly analysis
* Time-series reporting
* PivotTables

Dates should be validated and standardized before time-based analysis.

---

# 6️⃣ Text Functions

Functions explored include:

```text
TEXTJOIN
CONCAT
LEFT
MID
RIGHT
```

These functions can help restructure text and create cleaner analytical fields.

---

# 7️⃣ Splitting Emails

### Before

```text
john@gmail.com
```

### After

```text
Username → john
Domain   → gmail.com
```

This can support analysis such as customer/domain classification and data-quality checks.

---

# 8️⃣ Splitting Names

### Before

```text
John Doe
```

### After

```text
First Name → John
Last Name  → Doe
```

Separating attributes creates a more structured dataset for downstream analysis.

---

# 🧪 Data Quality Inspection Mindset

I visualize data preparation like a **quality inspection process**:

```text
               RAW DATA
                   ↓
            🔍 INSPECTION
                   ↓
        ┌──────────┴──────────┐
        ↓                     ↓
   ❌ Issues Found       ✅ Valid Records
        ↓                     ↓
   Clean / Correct          Approve
        ↓                     ↓
        └──────────┬──────────┘
                   ↓
            VALIDATE AGAIN
                   ↓
           ANALYSIS READY
```

The goal isn't simply to make data look cleaner.

The goal is to determine whether it is **reliable enough to support analysis**.

---

# 💼 Business Analyst Perspective

A Business Analyst may not always be responsible for engineering or cleaning the entire enterprise dataset.

However, when using data to support:

* Requirements
* KPIs
* Process analysis
* Business cases
* Recommendations
* Stakeholder presentations
* Decision-making

data quality becomes part of analytical responsibility.

Important questions include:

```text
Are records duplicated?

Are important fields missing?

Are formats consistent?

Are values within expected ranges?

Do categories follow business rules?

Does the dataset represent the intended population?

Has the data been refreshed?

Can important results be validated?
```

---

# 📊 Why This Matters

Consider:

```text
Duplicate Customer Records
          ↓
Incorrect Customer Count
          ↓
Incorrect KPI
          ↓
Misleading Analysis
          ↓
Poor Business Decision
```

Compare that with:

```text
Clean + Validated Data
          ↓
Reliable Metrics
          ↓
Accurate Analysis
          ↓
Meaningful Insights
          ↓
Better-Informed Decisions
```

---

# 💡 Key Takeaway

Data cleaning should not be treated as an invisible step before analysis.

**Data quality directly affects the quality of the insight produced from it.**

As a Business Analyst, my takeaway is:

> I may not always own the complete data-cleaning pipeline, but I should understand, question, and validate the data before relying on it for business conclusions.

### Analytical Mindset

**Inspect → Clean → Transform → Validate → Analyze → Communicate → Decide**

---

## 🛠️ Skills Practiced

`Data Cleaning` • `Data Validation` • `Duplicate Handling` • `Text Transformation` • `Date Standardization` • `Data Quality` • `Business Rules` • `Data Analysis` • `Business Analytics`

---

## 🚀 Learning Principle

**Cleaner Data → More Reliable Analysis → Stronger Insights → Better-Informed Decisions**
