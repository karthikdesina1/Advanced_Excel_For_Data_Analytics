# 🔎 INDEX & MATCH in Excel

## Overview

`INDEX` and `MATCH` separate lookup logic into two operations:

**MATCH → Find the Position**  
**INDEX → Retrieve the Value**

Together they create flexible formulas for vertical, horizontal, left-side, and two-way lookups.

---

## 1. INDEX Function

INDEX returns a value at a specified position.

### Syntax

```excel id="xgkr1f"
=INDEX(array,row_num,[column_num])
```

### Example

| ID | Name | Department |
|---|---|---|
| 101 | John | Sales |
| 102 | Jane | HR |
| 103 | Mike | Finance |

```excel id="8r7tbs"
=INDEX(B2:B4,2)
```

Result:

```text id="l9dfbr"
Jane
```

INDEX works well when the required position is already known.

---

## 2. MATCH Function

MATCH returns the **relative position** of a value.

### Syntax

```excel id="7v6fhs"
=MATCH(lookup_value,lookup_array,[match_type])
```

Example:

```excel id="og15hj"
=MATCH(103,A2:A4,0)
```

Result:

```text id="xt2ysj"
3
```

ID `103` is the third value in `A2:A4`.

---

## 3. INDEX + MATCH

MATCH can dynamically provide the row number required by INDEX.

```excel id="02fhpr"
=INDEX(C2:C4,MATCH(F2,A2:A4,0))
```

If `F2 = 103`:

```text id="sk0c7a"
MATCH → Position 3
INDEX → Finance
```

### Logic

```text id="8uj3av"
Lookup Value
     ↓
MATCH
Find Position
     ↓
INDEX
Return Value
```

---

## 4. Lookup to the Left

Unlike VLOOKUP, the return range does not need to be to the right of the lookup range.

Example dataset:

| Product | Product ID |
|---|---|
| Laptop | P101 |
| Mouse | P102 |
| Keyboard | P103 |

```excel id="e5dwga"
=INDEX(A2:A4,MATCH(F2,B2:B4,0))
```

If `F2 = P102`, the result is:

```text id="50cwrn"
Mouse
```

---

## 5. Horizontal Lookup

MATCH can also search across columns.

```excel id="a64r9u"
=INDEX(B2:E2,MATCH(F2,B1:E1,0))
```

Example:

```text id="h18ldc"
        Jan   Feb   Mar   Apr
Sales   1000  1500  2000  1800
```

If `F2 = Mar`, the result is `2000`.

---

## 6. Two-Way Lookup

INDEX can use **two MATCH functions** to dynamically identify both row and column.

```excel id="30ue0x"
=INDEX(B2:D4,
 MATCH(G2,A2:A4,0),
 MATCH(G3,B1:D1,0))
```

Example:

```text id="js6sgn"
           Jan   Feb   Mar
Laptop     800   850   900
Mouse       25    28    30
Keyboard    45    50    55
```

If:

```text id="0a7u7g"
Product = Mouse
Month   = Feb
```

Result:

```text id="vq6lym"
28
```

This follows:

**Find Row + Find Column → Return Intersection**

---

## 7. MATCH Types

### Exact Match

```excel id="r6d7th"
=MATCH(A2,B2:B100,0)
```

`0` searches for an exact match.

This is commonly appropriate for:

- Employee IDs
- Product IDs
- Customer IDs
- Names/codes requiring exact matching

### Approximate Match

MATCH also supports approximate matching on appropriately sorted data.

```excel id="40qg03"
=MATCH(F2,A2:A10,1)
```

`1` finds the largest value less than or equal to the lookup value when the lookup array is sorted ascending.

```excel id="nlsdbf"
=MATCH(F2,A2:A10,-1)
```

`-1` finds the smallest value greater than or equal to the lookup value when the lookup array is sorted descending.

Approximate matching can support:

- Commission bands
- Grade thresholds
- Pricing tiers
- Performance ranges

---

## 8. Why Combine INDEX + MATCH?

### Dynamic Positions

MATCH removes the need to manually specify a fixed row position.

### Left-Side Lookup

Lookup and return ranges can be arranged independently.

### Two-Way Analysis

Both rows and columns can be matched dynamically.

### Structural Flexibility

Because the lookup range and return range are referenced directly, formulas can be less dependent on hard-coded column index numbers than VLOOKUP.

---

## 9. INDEX + MATCH vs XLOOKUP

| Feature | INDEX + MATCH | XLOOKUP |
|---|---|---|
| Left lookup | ✅ | ✅ |
| Exact match | ✅ | ✅ |
| Approximate matching | ✅ | ✅ |
| Horizontal lookup | ✅ | ✅ |
| Two-way lookup | ✅ | Possible |
| Separate lookup/return ranges | ✅ | ✅ |
| Syntax | More involved | Usually simpler |
| Older Excel support | Broad | Version dependent |

For modern Excel, XLOOKUP is often simpler for common lookup tasks, while INDEX + MATCH remains useful for understanding and building flexible lookup logic.

---

## 10. Error Handling

INDEX + MATCH can be wrapped with `IFERROR`:

```excel id="i6x1z0"
=IFERROR(
 INDEX(C2:C100,MATCH(F2,A2:A100,0)),
 "Not Found"
)
```

This prevents raw lookup errors from appearing in user-facing reports.

---

## Business Applications

```text id="7g1q4o"
Employee ID → Department
Product ID  → Product Details
Customer ID → Segment
Product + Month → Sales
Score → Performance Band
Sales → Commission Tier
```

---

## Key Takeaway

INDEX + MATCH is easier to understand when viewed as two separate questions:

**MATCH:** Where is the requested record?

**INDEX:** What value exists at that position?

For two-dimensional analysis:

**MATCH Row + MATCH Column → INDEX Intersection**

### Analytical Workflow

**Identify → Match → Retrieve → Validate → Analyze**

---

## Skills Practiced

`INDEX` • `MATCH` • `Two-Way Lookups` • `Left Lookups` • `Horizontal Lookups` • `Approximate Matching` • `Error Handling` • `Dynamic Formulas` • `Data Analysis`
