# LEETCODE-Arrays-757
---

# ✅ **Dry Run Explanation (Concept + Flow)**

### **Variables used**

* `first` and `second` represent the **two largest chosen points so far**.
* Both start at **-1**.
* `result` counts how many points we have selected.

---

# ✅ **Step 1: Sort the intervals**

The sorting logic:

```
1. Sort by increasing r (right endpoint)
2. If r is same, sort by decreasing l (left endpoint)
```

This ensures we always handle the interval that ends earliest first, which maximizes future flexibility.

---

# 📌 **Understanding the Greedy Logic**

For each interval `[l, r]`:

### **Case 1: interval already satisfied**

```
if (l <= first) continue;
```

Already has at least two points.

---

### **Case 2: interval has 0 chosen points inside**

```
if (l > second):
    add 2 points → r-1 and r
```

Update:

```
first = r-1
second = r
```

---

### **Case 3: interval has exactly 1 point inside**

```
else:
    add 1 point → r
```

Update:

```
first = second
second = r
```

---

# 🚀 **Now Let’s Do a Complete Dry Run With an Example**

Use sample intervals:

```
intervals = [[1,3], [1,4], [2,5], [3,5]]
```

---

# **STEP 1 — SORT**

Sorted by ending times:

```
[1,3]
[1,4]
[3,5]
[2,5]   (4th because for same r=5, larger l comes first)
```

---

# **STEP 2 — DRY RUN**

### Initialize:

```
first = -1
second = -1
result = 0
```

---

## ▶️ **i = 0 → [1,3]**

```
l = 1
r = 3
l > second  → 1 > -1 → TRUE
```

→ No selected points inside → **add 2 points (2,3)**

```
result = 2
first = 2
second = 3
```

---

## ▶️ **i = 1 → [1,4]**

```
l = 1 ≤ first (=2) → continue
```

→ This interval already contains points {2,3}.
So **no new points needed**.

```
result = 2   (unchanged)
```

---

## ▶️ **i = 2 → [3,5]**

```
l = 3 ≰ first (=2)
l ≤ second (=3) ✓  (interval has exactly 1 point (3))
```

→ add **1 point: r = 5**

```
result = 3
first = 3
second = 5
```

---

## ▶️ **i = 3 → [2,5]**

```
l = 2 ≤ first (=3) → continue
```

→ Already satisfied since interval has points {3,5}.

```
result = 3
```

---

# 🎉 Final Answer

```
result = 3
```

---
