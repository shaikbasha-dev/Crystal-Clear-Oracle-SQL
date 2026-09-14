# 13-IS-NULL-Operator

## 1. What is IS NULL?

`IS NULL` is used to find records where a column contains **NULL**.

In simple words:

> **IS NULL means: "Does this column have no value?"**

For example, suppose an employee does not have a commission value:

```text
COMMISSION_PCT
--------------
NULL
```

To find such employees, we use:

```sql
WHERE commission_pct IS NULL
```

---

## 2. What is NULL?

`NULL` means that a value is **not available / not stored**.

It is important to understand:

```text
NULL ≠ 0
NULL ≠ ''
NULL ≠ 'NULL'
```

For example:

```text
COMMISSION_PCT
--------------
NULL
0.5
0.75
1.2
```

The first employee has no commission value stored.

---

# 3. Why do we need IS NULL?

Suppose we want to find employees who **do not take any commission**.

We cannot correctly check NULL using:

```sql
WHERE commission_pct = NULL
```

Instead, we use:

```sql
WHERE commission_pct IS NULL
```

`IS NULL` is specifically used to test for NULL.

---

# 4. Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name IS NULL;
```

Example:

```sql
SELECT *
FROM emp
WHERE commission_pct IS NULL;
```

---

# 5. Question 1

### Question

**Write a query to display the details of employees who do not take any commission.**

### Answer / Query

```sql
SELECT *
FROM emp
WHERE commission_pct IS NULL;
```

### Explanation

Oracle checks the `COMMISSION_PCT` column for every employee.

```text
COMMISSION_PCT
      ↓
   Is it NULL?
      ↓
  YES → Display employee
  NO  → Don't display
```

So employees whose `COMMISSION_PCT` has no value are displayed.

---

## 6. Understanding the Query

```sql
SELECT *
FROM emp
WHERE commission_pct IS NULL;
```

### `SELECT *`

```text
Display all columns
```

### `FROM emp`

```text
Take the data from EMP table
```

### `WHERE commission_pct IS NULL`

```text
Only select employees
whose commission_pct is NULL
```

---

# 7. Important: Do NOT use `= NULL`

### ❌ Incorrect

```sql
SELECT *
FROM emp
WHERE commission_pct = NULL;
```

### ✅ Correct

```sql
SELECT *
FROM emp
WHERE commission_pct IS NULL;
```

For NULL checking, use:

```text
IS NULL
```

not:

```text
= NULL
```

---

# 8. NULL vs 0

This is a very common confusion.

Suppose:

```text
COMMISSION_PCT
--------------
NULL
0
```

These two are different.

### NULL

Means:

> No value is stored.

### 0

Means:

> The value stored is zero.

Therefore:

```sql
WHERE commission_pct IS NULL
```

finds NULL values, **not zero values**.

---

# 9. IS NULL vs IS NOT NULL

These are opposites.

### IS NULL

Finds records where the value is NULL:

```sql
WHERE commission_pct IS NULL
```

### IS NOT NULL

Finds records where the value is available:

```sql
WHERE manager_id IS NOT NULL
```

Think:

```text
IS NULL
   ↓
No value

IS NOT NULL
   ↓
Value exists
```

---

# 10. Question 2 — Understanding the Next Operator

The next query in this sequence is:

### Question

**Write a query to display the details of employees who have a manager.**

### Query

```sql
SELECT *
FROM emp
WHERE manager_id IS NOT NULL;
```

This is the **IS NOT NULL** operator, which is the next folder/topic. It is shown here only to make the difference between the two operators clear.

---

# 11. IS NULL vs IS NOT NULL

| Condition            | Meaning             |
| -------------------- | ------------------- |
| `column IS NULL`     | Column has no value |
| `column IS NOT NULL` | Column has a value  |

Example:

```sql
WHERE commission_pct IS NULL
```

→ Find employees without a commission value.

Example:

```sql
WHERE manager_id IS NOT NULL
```

→ Find employees who have a manager.

---

# 12. Common Mistakes

### Mistake 1 — Using `= NULL`

❌

```sql
WHERE commission_pct = NULL;
```

✅

```sql
WHERE commission_pct IS NULL;
```

---

### Mistake 2 — Thinking NULL means zero

❌

```text
NULL = 0
```

They are different.

```text
NULL → no value
0    → value is zero
```

---

### Mistake 3 — Using `IN` for NULL

Do not use:

```sql
WHERE commission_pct IN (NULL);
```

For checking NULL, use:

```sql
WHERE commission_pct IS NULL;
```

---

# 13. Memory Trick

Remember:

```text
IS NULL
   ↓
"Is there NO value?"
```

And:

```text
IS NOT NULL
   ↓
"Is there a value?"
```

Very easy:

```text
NULL     → No value
IS NULL  → Find no-value records
```

---

# 14. Interview Questions

### Q1. What is IS NULL?

`IS NULL` is used to check whether a column contains a NULL value.

### Q2. Can we use `= NULL`?

**No.**

Use:

```sql
IS NULL
```

instead.

### Q3. What is the difference between NULL and 0?

`NULL` represents the absence of a value, whereas `0` is an actual numeric value.

### Q4. What is the syntax of IS NULL?

```sql
column_name IS NULL
```

### Q5. What is the opposite of IS NULL?

```sql
IS NOT NULL
```

---

# 15. Complete Question + Query

### Question

**Write a query to display the details of employees who do not take any commission.**

### Answer / Query

```sql
SELECT *
FROM emp
WHERE commission_pct IS NULL;
```

### Simple meaning

```text
EMP table
   ↓
Check COMMISSION_PCT
   ↓
Is it NULL?
   ↓
Yes → Display employee
```

**Memory line:**

> `IS NULL` → **Find records where the value is missing.**
