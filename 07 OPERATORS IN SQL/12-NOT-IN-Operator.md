# 12-NOT-IN-Operator

## 1. What is NOT IN?

`NOT IN` is used when we want to select records where a column value **does not match any value from a specified list**.

In simple words:

> **NOT IN means: "Is this value NOT present in this list?"**

For example:

```sql
WHERE grade NOT IN ('A', 'B', 'C')
```

means:

```text
grade is NOT A
AND
grade is NOT B
AND
grade is NOT C
```

---

## 2. Why do we use NOT IN?

Suppose we want to find records where the grade is **not A, B, or C**.

Instead of writing several conditions, we can use:

```sql
WHERE grade NOT IN ('A', 'B', 'C')
```

It makes the condition easier to read.

---

## 3. Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name NOT IN (value1, value2, value3);
```

Remember:

```text
NOT IN
  ↓
(value1, value2, value3)
```

---

# 4. Question

**Write a query to display `low_sal` and `high_sal` from `J_GRADE` where the grade is NOT IN A, B and C.**

### Answer / Query

```sql
SELECT low_sal, high_sal
FROM j_grade
WHERE grade NOT IN ('A', 'B', 'C');
```

### Explanation

Oracle checks the `GRADE` of each record.

The condition:

```sql
grade NOT IN ('A', 'B', 'C')
```

means:

```text
Grade should NOT be A
AND
Grade should NOT be B
AND
Grade should NOT be C
```

Therefore, records having:

```text
A → ❌
B → ❌
C → ❌
```

are excluded.

Other grade values can be selected.

---

# 5. NOT IN vs IN

These are opposites.

### IN

```sql
WHERE grade IN ('A', 'B', 'C')
```

Means:

```text
A OR B OR C
```

### NOT IN

```sql
WHERE grade NOT IN ('A', 'B', 'C')
```

Means:

```text
Not A
AND Not B
AND Not C
```

### Easy memory

```text
IN      → SELECT FROM THE LIST
NOT IN  → REJECT THE LIST
```

---

# 6. NOT IN vs NOT BETWEEN

Do not confuse these two.

### NOT IN

Checks against **specific values**:

```sql
salary NOT IN (12000, 18000, 19000)
```

It excludes exactly those listed values.

### NOT BETWEEN

Checks against a **range**:

```sql
salary NOT BETWEEN 12000 AND 19000
```

It excludes the entire range from `12000` through `19000`.

### Memory

```text
IN / NOT IN
     ↓
Specific values

BETWEEN / NOT BETWEEN
     ↓
Range
```

---

# 7. Common Mistake

### Character values need single quotes

Correct:

```sql
WHERE grade NOT IN ('A', 'B', 'C');
```

The values `A`, `B`, and `C` are character values.

---

# 8. Important Rule

`NOT IN` means the column value must **not match any value in the list**.

For:

```sql
grade NOT IN ('A', 'B', 'C')
```

think:

```text
          GRADE
            ↓
     ┌──────┼──────┐
     A      B      C
     ❌     ❌     ❌
```

Only values outside that list satisfy the condition.

---

# 9. Interview Questions

### Q1. What is NOT IN?

`NOT IN` is used to select records whose column value does not match any value in a specified list.

### Q2. What is the syntax?

```sql
column_name NOT IN (value1, value2, value3);
```

### Q3. What is the difference between IN and NOT IN?

`IN` selects values that are present in the list, whereas `NOT IN` excludes the listed values.

### Q4. Is NOT IN used for a range?

No. `NOT IN` is used for **specific values**. For a range, we use `NOT BETWEEN`.

---

# 10. Complete Query

### Question

**Write a query to display `low_sal` and `high_sal` from `J_GRADE` where the grade is NOT IN A, B and C.**

```sql
SELECT low_sal, high_sal
FROM j_grade
WHERE grade NOT IN ('A', 'B', 'C');
```

### One-line memory

```text
IN      → value is in the list
NOT IN  → value is not in the list
```

**Important:** The notes' wording around this question may describe the excluded grades differently in one place; the actual query uses `NOT IN ('A','B','C')`, so those are the values excluded by the query.
