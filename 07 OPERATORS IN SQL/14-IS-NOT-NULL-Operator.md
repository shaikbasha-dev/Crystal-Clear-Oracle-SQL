# 14-IS-NOT-NULL-Operator

## 1. What is IS NOT NULL?

`IS NOT NULL` is used to find records where a column **contains a value** and is **not NULL**.

In simple words:

> **IS NOT NULL means: "Does this column have a value?"**

For example:

```text id="j6x5q1"
MANAGER_ID
----------
NULL
100
101
110
```

If we use:

```sql id="x6z8q2"
WHERE manager_id IS NOT NULL
```

Oracle selects the employees whose `MANAGER_ID` contains a value.

---

## 2. Why do we use IS NOT NULL?

Suppose we want to find:

> Employees who **have a manager**.

Some employees may have a `MANAGER_ID`, while others may not.

We can find employees having a manager using:

```sql id="w5z6j7"
WHERE manager_id IS NOT NULL
```

---

## 3. Syntax

```sql id="n7k2p4"
SELECT column_name
FROM table_name
WHERE column_name IS NOT NULL;
```

Example:

```sql id="d3q8m1"
SELECT *
FROM emp
WHERE manager_id IS NOT NULL;
```

---

# 4. Question

### Question

**Write a query to display the details of employees who have a manager.**

### Answer / Query

```sql id="a9c4e2"
SELECT *
FROM emp
WHERE manager_id IS NOT NULL;
```

### Explanation

Oracle checks the `MANAGER_ID` of every employee.

```text id="p2k7v5"
MANAGER_ID
    ↓
Is it NOT NULL?
    ↓
 YES → Display employee
 NO  → Don't display
```

So employees whose `MANAGER_ID` contains a value are displayed.

---

# 5. Understanding the Query

```sql id="r5u8y3"
SELECT *
FROM emp
WHERE manager_id IS NOT NULL;
```

### `SELECT *`

Means:

```text id="a4j9x2"
Display all columns
```

### `FROM emp`

Means:

```text id="m8d2k6"
Take data from EMP table
```

### `WHERE manager_id IS NOT NULL`

Means:

```text id="q3f7n1"
Select only employees
whose MANAGER_ID has a value
```

---

# 6. Example

Suppose the data looks like this:

| EMP_ID | F_NAME      | MANAGER_ID |
| -----: | ----------- | ---------: |
|      1 | Akash       |       NULL |
|      2 | Prabhakaran |        100 |
|      3 | DEEP        |        101 |
|      5 | John        |        110 |
|     17 | Pankaj      |       NULL |

Query:

```sql id="c8m4v2"
SELECT *
FROM emp
WHERE manager_id IS NOT NULL;
```

Oracle checks each row:

```text id="b7n5k9"
Akash        → NULL  → ❌
Prabhakaran  → 100   → ✅
DEEP         → 101   → ✅
John         → 110   → ✅
Pankaj       → NULL  → ❌
```

Therefore, only employees with a manager ID are displayed.

---

# 7. IS NULL vs IS NOT NULL

These are opposite conditions.

### IS NULL

```sql id="v4k8s2"
WHERE manager_id IS NULL
```

Means:

> Find employees who **do not have a manager value**.

### IS NOT NULL

```sql id="z9m3q7"
WHERE manager_id IS NOT NULL
```

Means:

> Find employees who **have a manager value**.

### Easy memory

```text id="u2p6r5"
IS NULL
   ↓
No value

IS NOT NULL
   ↓
Value exists
```

---

# 8. Do NOT use `= NULL`

This is an important rule.

### ❌ Incorrect

```sql id="q6w3e8"
WHERE manager_id = NULL;
```

### ✅ Correct for NULL

```sql id="h2k7m4"
WHERE manager_id IS NULL;
```

### ✅ Correct for NOT NULL

```sql id="s8v1n5"
WHERE manager_id IS NOT NULL;
```

For NULL checking, use the `IS` operators.

---

# 9. NULL vs 0

Remember that:

```text id="f5t2j9"
NULL
```

and:

```text id="k8p4m6"
0
```

are different.

| Value  | Meaning                   |
| ------ | ------------------------- |
| `NULL` | No value is stored        |
| `0`    | Actual numeric value zero |

Therefore:

```sql id="e3r7v1"
manager_id IS NOT NULL
```

checks whether `MANAGER_ID` contains a value.

---

# 10. IS NOT NULL vs NOT IN

Do not confuse these.

### IS NOT NULL

Checks whether a value exists:

```sql id="n4c8x2"
WHERE manager_id IS NOT NULL
```

### NOT IN

Checks whether a value is not one of the specified values:

```sql id="j7p3m9"
WHERE grade NOT IN ('A', 'B', 'C')
```

So:

```text id="r2v6k8"
IS NOT NULL → Check existence of a value

NOT IN      → Check against a list
```

---

# 11. Common Mistakes

### Mistake 1

❌

```sql id="b8m2q5"
WHERE manager_id != NULL;
```

Use:

```sql id="c6k9t3"
WHERE manager_id IS NOT NULL;
```

---

### Mistake 2

Thinking `IS NOT NULL` means the value must be non-zero.

It does not.

For example:

```text id="y4r7p1"
0 → NOT NULL
```

because `0` is an actual value.

---

# 12. Important Rules

1. `IS NOT NULL` checks whether a column contains a value.
2. It is commonly used with the `WHERE` clause.
3. Use `IS NOT NULL`, not `= NULL` or `!= NULL`.
4. `IS NOT NULL` is the opposite of `IS NULL`.
5. `NULL` and `0` are different.

---

# 13. Interview Questions

### Q1. What is IS NOT NULL?

`IS NOT NULL` is used to select records where a column contains a non-NULL value.

### Q2. What is the syntax?

```sql id="s5x8c3"
column_name IS NOT NULL
```

### Q3. What is the opposite of IS NOT NULL?

```sql id="n9k4w6"
IS NULL
```

### Q4. Can we use `!= NULL`?

**No.**

Use:

```sql id="h7p2m5"
IS NOT NULL
```

### Q5. What does `manager_id IS NOT NULL` mean?

It means:

> Select employees whose `MANAGER_ID` has a value.

---

# 14. Complete Question + Query

### Question

**Write a query to display the details of employees who have a manager.**

### Answer / Query

```sql id="q2v8m4"
SELECT *
FROM emp
WHERE manager_id IS NOT NULL;
```

### Simple meaning

```text id="w6k3p9"
EMP table
    ↓
Check MANAGER_ID
    ↓
Does it contain a value?
    ↓
YES → Display employee
NO  → Don't display
```

### Memory line

> **IS NULL → Find missing values**

> **IS NOT NULL → Find available values**
