# 📊 Excel Data Tab - Consolidate, Relationships & What-If Analysis

## 📌 Overview

Excel's Data Tab provides tools for consolidating information, connecting related datasets, and analyzing business scenarios.

This module focuses on:
- Consolidate (Data Tools)
- Relationships (Data Model)
- What-If Analysis: Goal Seek
- One-Variable and Two-Variable Data Tables

**Workflow:** Combine → Connect → Analyze → Evaluate → Decide

---

## 1. Consolidate - Data Tools

Consolidate combines and summarizes data from multiple worksheets or workbooks.

### Key Features
- Combine multiple data ranges
- Summarize using SUM, AVERAGE, COUNT, MAX, MIN
- Consolidate by Position
- Consolidate by Category
- Create centralized business summaries

### Consolidate by Position
Use when source ranges share the same layout and cell positions.

### Consolidate by Category
Use when source data contains matching row or column labels, even if the layout differs.

### Business Example

| Product | January | February | March | Total |
|---|---:|---:|---:|---:|
| Laptop | 500 | 600 | 550 | 1650 |
| Mouse | 300 | 250 | 400 | 950 |
| Keyboard | 200 | 300 | 350 | 850 |

**Excel Path:** Data → Data Tools → Consolidate

### Consolidation Steps
1. Select the destination cell.
2. Open Consolidate.
3. Choose SUM, AVERAGE, COUNT, or another function.
4. Add source ranges.
5. Enable Top Row / Left Column labels when appropriate.
6. Click OK and validate the summary.

**Note:** Standard consolidation produces summary results, not a row-by-row merge. Optional source links can support updates.

---

## 2. Relationships - Excel Data Model

Relationships connect multiple tables using common fields.

### Example Tables

**Sales Table (Fact)**

| OrderID | ProductID | CustomerID | Sales |
|---|---|---|---:|
| 101 | P01 | C01 | 500 |
| 102 | P02 | C02 | 800 |

**Product Table (Dimension)**

| ProductID | Product |
|---|---|
| P01 | Laptop |
| P02 | Mouse |

**Customer Table (Dimension)**

| CustomerID | Customer |
|---|---|
| C01 | John |
| C02 | Sara |

### Relationship Model

```text
Product Table (1)
       |
       | ProductID
       ↓
Sales Table (*)
       ↑
       | CustomerID
       |
Customer Table (1)
```

### One-to-Many Relationships
- One product can appear in many sales.
- One customer can have many orders.
- Dimension keys should uniquely identify records.
- Fact tables can contain repeated foreign keys.

### Business Benefits
- Reduce redundant descriptive data
- Connect related business information
- Analyze multiple tables together
- Create PivotTables using the Data Model

**Excel Path:** Data → Relationships

---

## 3. What-If Analysis - Goal Seek

Goal Seek determines the input required to achieve a specified formula result.

### Business Scenario

A company wants to earn $10,000 profit.

Assumptions:
- Selling Price = $20/unit
- Variable Cost = $12/unit
- Fixed Cost = $4,000

### Profit Formula

```excel
=(B2-B3)*B4-B5
```

Where:
- B2 = Selling Price
- B3 = Variable Cost
- B4 = Units Sold
- B5 = Fixed Cost

### Goal Seek Configuration

```text
Set Cell: B6 (Profit Formula)
To Value: 10000
By Changing Cell: B4 (Units Sold)
```

### Mathematical Verification

```text
Profit = (Price - Variable Cost) × Units - Fixed Cost

10000 = (20 - 12) × Units - 4000
14000 = 8 × Units
Units = 1750
```

**Result:** Sell 1,750 units to achieve $10,000 profit.

### Steps
1. Create the profit formula in B6.
2. Select Data → What-If Analysis → Goal Seek.
3. Set the target cell and target value.
4. Select the input cell to change.
5. Run Goal Seek.
6. Validate the result.

**Limitation:** Goal Seek changes one input cell at a time.

---

## 4. One-Variable Data Table

A One-Variable Data Table evaluates how changing one input affects one or more formula outputs.

### Example: Price vs Profit

Assume:
- Units Sold = 500
- Variable Cost = $12/unit
- Fixed Cost = $4,000

Profit = (Price - 12) × 500 - 4000

| Price | Profit |
|---:|---:|
| $15 | -$2,500 |
| $20 | $0 |
| $25 | $2,500 |
| $30 | $5,000 |

### Use Cases
- Price sensitivity
- Sales volume scenarios
- Interest rate comparisons
- Budget assumptions

**Excel Path:** Data → What-If Analysis → Data Table

For a vertical list of input values, specify the Column Input Cell.

---

## 5. Two-Variable Data Table

A Two-Variable Data Table compares outcomes based on two changing inputs.

### Example: Selling Price vs Units Sold

Profit = (Price - 12) × Units - 4000

| Units / Price | $15 | $20 | $25 |
|---|---:|---:|---:|
| 200 | -$3,400 | -$2,400 | -$1,400 |
| 400 | -$2,800 | -$800 | $1,200 |
| 600 | -$2,200 | $800 | $3,800 |
| 800 | -$1,600 | $2,400 | $6,400 |

### Setup
1. Create the profit formula.
2. List selling prices across the top row.
3. List units sold down the first column.
4. Place a reference to the profit formula in the top-left corner.
5. Select the entire scenario range.
6. Open Data → What-If Analysis → Data Table.
7. Row Input Cell = Selling Price cell.
8. Column Input Cell = Units Sold cell.

### Applications
- Pricing strategy
- Profit forecasting
- Break-even analysis
- Sales planning
- Budget scenarios

---

## 6. Goal Seek vs Data Tables

| Feature | Goal Seek | Data Table |
|---|---|---|
| Purpose | Find required input | Compare outcomes |
| Input changes | One | One or two |
| Target output | Specified | Calculated |
| Typical use | Profit target | Scenario analysis |

**Goal Seek:** What input achieves my target?

**Data Table:** What happens when assumptions change?

---

## 7. Real-World Business Workflow

```text
MULTIPLE BUSINESS DATASETS
            ↓
        CONSOLIDATE
            ↓
     BUILD RELATIONSHIPS
            ↓
      CREATE DATA MODEL
            ↓
     ANALYZE PERFORMANCE
            ↓
   GOAL SEEK / DATA TABLES
            ↓
      COMPARE SCENARIOS
            ↓
     BUSINESS DECISIONS
```

### Business Applications
- Regional sales consolidation
- Customer and product analysis
- Profit target planning
- Budget forecasting
- Pricing sensitivity
- Management reporting

---

## 8. Validation Checklist

- [ ] Verify consolidation source ranges
- [ ] Confirm matching category labels
- [ ] Check unique relationship keys
- [ ] Validate missing or unmatched IDs
- [ ] Verify formula references
- [ ] Confirm Goal Seek results
- [ ] Review scenario assumptions
- [ ] Compare Data Table outputs with manual calculations

---

## 💡 Key Takeaway

Excel Data Tools help analysts consolidate information, connect related datasets, and evaluate alternative business outcomes.

**Consolidate → Relate → Model → Simulate → Validate → Decide**

## 🛠️ Skills Focused

`Excel Data Tools` • `Consolidate` • `Data Model` • `Relationships` • `Goal Seek` • `What-If Analysis` • `One-Variable Data Table` • `Two-Variable Data Table` • `Scenario Analysis` • `Business Analytics`
