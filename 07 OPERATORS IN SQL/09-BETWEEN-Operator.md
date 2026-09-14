# 09-BETWEEN-Operator

## 1. What is BETWEEN?

`BETWEEN` is used when we want to find values **within a particular range**.

In very simple words:

> **BETWEEN means: "Is the value from this starting value to this ending value?"**

For example:

```text
20 ----------- 30
      ↑
   BETWEEN
```

If we ask:

```text
Is 25 between 20 and 30?
```

Yes.

If we ask:

```text
Is 35 between 20 and 30?
```

No.

---

# 2. Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name BETWEEN lower_value AND higher_value;
```

### Remember the order

```text
BETWEEN
   ↓
Starting value
   ↓
AND
   ↓
Ending value
```

Example:

```sql
salary BETWEEN 20000 AND 40000
```

means:

```text
salary >= 20000
AND
salary <= 40000
```

**Important:** `BETWEEN` includes the boundary values.

So:

```text
20000 → included
30000 → included
40000 → included
```

---

# 3. Why do we use BETWEEN?

Suppose we want employees whose salary is from:

```text
₹20,000 to ₹40,000
```

Instead of writing:

```sql
WHERE salary >= 20000
AND salary <= 40000
```

we can write:

```sql
WHERE salary BETWEEN 20000 AND 40000
```

It is shorter and easier to understand.

---

# 4. Question 1

### Question

**Write a query to display grade and low_sal where low_sal is between 2000 and 4000.**

### Answer / Query

```sql
SELECT grade, low_sal
FROM j_grade
WHERE low_sal BETWEEN 2000 AND 4000;
```

### What is happening?

```text
J_GRADE
   ↓
Take GRADE and LOW_SAL
   ↓
Check LOW_SAL
   ↓
Is LOW_SAL between 2000 and 4000?
   ↓
Yes → display
No  → don't display
```

So the condition:

```sql
low_sal BETWEEN 2000 AND 4000
```

means:

```sql
low_sal >= 2000
AND
low_sal <= 4000
```

---

# 5. Question 2

### Question

**Write a query to display all the employees where commission_pct is between 1.2 and 1.5.**

### Answer / Query

```sql
SELECT *
FROM emp
WHERE commission_pct BETWEEN 1.2 AND 1.5;
```

### Explanation

`SELECT *` means:

> Display all columns.

Then:

```sql
commission_pct BETWEEN 1.2 AND 1.5
```

means:

```text
commission_pct >= 1.2
       AND
commission_pct <= 1.5
```

Therefore, values such as:

```text
1.2
1.3
1.4
1.5
```

are within the range.

But:

```text
1.1
1.6
```

are outside the range.

---

# 6. Understanding BETWEEN visually

For:

```sql
commission_pct BETWEEN 1.2 AND 1.5
```

think:

```text
1.1    1.2              1.5    1.6
 |------|================|------|
        ↑                ↑
     included         included
```

Everything from `1.2` through `1.5` is included.

---

# 7. BETWEEN is inclusive

This is one of the most important interview points.

Consider:

```sql
salary BETWEEN 10000 AND 20000
```

It means:

```sql
salary >= 10000
AND
salary <= 20000
```

Therefore:

| Salary | Result         |
| -----: | -------------- |
|  9,999 | ❌ Not included |
| 10,000 | ✅ Included     |
| 15,000 | ✅ Included     |
| 20,000 | ✅ Included     |
| 20,001 | ❌ Not included |

So **both boundary values are included**.

---

# 8. BETWEEN with numbers

The examples in this topic use numeric values.

### Example

```sql
SELECT grade, low_sal
FROM j_grade
WHERE low_sal BETWEEN 2000 AND 4000;
```

Here:

```text
2000 = lower limit
4000 = upper limit
```

---

# 9. BETWEEN with commission percentage

The second question uses:

```sql
commission_pct BETWEEN 1.2 AND 1.5
```

Here:

```text
1.2 = lower limit
1.5 = upper limit
```

So Oracle checks every employee's `COMMISSION_PCT`.

---

# 10. BETWEEN vs Relational Operators

These two are logically equivalent:

### Using BETWEEN

```sql
WHERE salary BETWEEN 20000 AND 40000;
```

### Using relational operators

```sql
WHERE salary >= 20000
AND salary <= 40000;
```

The first one is simply a convenient way of expressing the range.

---

# 11. Common Mistake

### ❌ Incorrect order

```sql
WHERE salary BETWEEN 40000 AND 20000;
```

For normal numeric ranges, write the lower value first and higher value second:

```sql
WHERE salary BETWEEN 20000 AND 40000;
```

Remember:

```text
BETWEEN LOW AND HIGH
```

---

# 12. Common Confusion: BETWEEN does not mean only middle values

Some beginners think:

```sql
BETWEEN 2000 AND 4000
```

means:

```text
more than 2000
and
less than 4000
```

But that would exclude the boundaries.

The actual meaning is:

```text
>= 2000
AND
<= 4000
```

So `2000` and `4000` are included.

---

# 13. Question → Query → Meaning

### Question 1

**Write a query to display grade and low_sal where low_sal is between 2000 and 4000.**

```sql
SELECT grade, low_sal
FROM j_grade
WHERE low_sal BETWEEN 2000 AND 4000;
```

**Meaning:**
Display `GRADE` and `LOW_SAL` when `LOW_SAL` falls from `2000` through `4000`.

---

### Question 2

**Write a query to display all the employees where commission_pct is between 1.2 and 1.5.**

```sql
SELECT *
FROM emp
WHERE commission_pct BETWEEN 1.2 AND 1.5;
```

**Meaning:**
Display all employee information when `COMMISSION_PCT` falls from `1.2` through `1.5`.

---

# 14. Important Rules

### Rule 1

`BETWEEN` is normally used with `WHERE`.

```sql
WHERE column BETWEEN value1 AND value2
```

### Rule 2

The lower and upper boundaries are included.

```text
BETWEEN 10 AND 20
```

means:

```text
10 <= value <= 20
```

### Rule 3

`BETWEEN` checks a range.

```text
LOW → HIGH
```

### Rule 4

The two values are connected using `AND`.

```sql
BETWEEN 2000 AND 4000
```

---

# 15. Interview Questions

### Q1. What is BETWEEN?

`BETWEEN` is used to check whether a value falls within a specified range.

### Q2. Does BETWEEN include the boundary values?

**Yes.**

For example:

```sql
salary BETWEEN 10000 AND 20000
```

includes both `10000` and `20000`.

### Q3. What is the syntax?

```sql
column_name BETWEEN lower_value AND higher_value
```

### Q4. What is the equivalent condition for BETWEEN?

```sql
column_name BETWEEN 10000 AND 20000
```

is equivalent to:

```sql
column_name >= 10000
AND column_name <= 20000
```

### Q5. What is the difference between BETWEEN and `>` / `<`?

`BETWEEN` checks an entire range and includes both boundaries, while `>` and `<` individually compare a value with another value.

---

# 16. Memory Trick

Remember:

> **BETWEEN = RANGE**

And:

```text
BETWEEN LOW AND HIGH
       ↓      ↓
     Start    End
```

The easiest way to remember:

```text
BETWEEN 10 AND 20
```

means:

```text
10 ≤ value ≤ 20
```

---

# 17. Complete Questions + Queries from this Topic

### Question 1

**Write a query to display grade, low_sal from j_grade where low_sal between 2000 and 4000.**

```sql
SELECT grade, low_sal
FROM j_grade
WHERE low_sal BETWEEN 2000 AND 4000;
```

### Question 2

**Write a query to display all the employees where commission_pct between 1.2 and 1.5.**

```sql
SELECT *
FROM emp
WHERE commission_pct BETWEEN 1.2 AND 1.5;
```

These are the **BETWEEN-related queries in this Operators section**.
