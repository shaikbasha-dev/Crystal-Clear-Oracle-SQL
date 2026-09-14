# 11-IN-Operator

## 1. What is IN Operator?

The `IN` operator is used when we want to check whether a column value **matches any one value from a list of values**.

In simple words:

> **IN means: "Is this value present in this list?"**

For example:

```sql
salary IN (12000, 18000, 19000)
```

means:

```text
Is salary = 12000?
OR
Is salary = 18000?
OR
Is salary = 19000?
```

If any one condition is true, the record is selected.

---

## 2. Why do we need IN?

Suppose we want employees whose salary is:

```text
12000
18000
19000
```

We could write:

```sql
WHERE salary = 12000
OR salary = 18000
OR salary = 19000
```

Instead, we can simply write:

```sql
WHERE salary IN (12000, 18000, 19000)
```

This is easier to read and write.

---

## 3. Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name IN (value1, value2, value3);
```

### Remember:

```text
IN
 ↓
(value1, value2, value3, ...)
```

The values are written inside **parentheses `()`** and separated by commas.

---

# 4. Question 1

### Question

**Write a query to display all employees whose salary is 12000, 18000 or 19000.**

### Answer / Query

```sql
SELECT *
FROM emp
WHERE salary IN (12000, 18000, 19000);
```

### Explanation

Oracle checks the `SALARY` of each employee.

It asks:

```text
Is salary = 12000?
        OR
Is salary = 18000?
        OR
Is salary = 19000?
```

If the answer to any one of them is `YES`, that employee is displayed.

### Example

Suppose salaries are:

```text
12000  → ✅
18000  → ✅
19000  → ✅
25000  → ❌
34000  → ❌
```

---

# 5. Question 2

### Question

**Write a query to display department id and department name where loc_id is 2500, 2700 or 2900.**

### Answer / Query

```sql
SELECT dept_id, dept_name
FROM dept
WHERE loc_id IN (2500, 2700, 2900);
```

### Explanation

Oracle checks each `LOC_ID`:

```text
Is LOC_ID = 2500?
       OR
Is LOC_ID = 2700?
       OR
Is LOC_ID = 2900?
```

If any one is true, Oracle displays:

```text
DEPT_ID
DEPT_NAME
```

for that department.

---

# 6. IN is like multiple OR conditions

This is a very important point.

The query:

```sql
SELECT *
FROM emp
WHERE salary IN (12000, 18000, 19000);
```

is logically equivalent to:

```sql
SELECT *
FROM emp
WHERE salary = 12000
   OR salary = 18000
   OR salary = 19000;
```

So:

> **IN is a convenient way to compare one column with multiple possible values.**

---

# 7. IN with Character Values

`IN` can also be used with character values.

For example, if we have:

```sql
job_id IN ('IT_PROG', 'ST_CLERK')
```

the values are written inside single quotes because they are character values.

The notes also use `IN` with character values in the next operator, `NOT IN`.

---

# 8. IN vs BETWEEN

These two operators are different.

### IN

Used for **specific values**.

```sql
salary IN (12000, 18000, 19000)
```

Means:

```text
Only 12000
OR 18000
OR 19000
```

### BETWEEN

Used for a **range of values**.

```sql
salary BETWEEN 12000 AND 19000
```

Means:

```text
12000 through 19000
```

### Easy memory

```text
IN       → Specific values
BETWEEN  → Range
```

---

# 9. IN vs OR

### Using OR

```sql
WHERE salary = 12000
OR salary = 18000
OR salary = 19000
```

### Using IN

```sql
WHERE salary IN (12000, 18000, 19000)
```

Both represent the same type of condition.

`IN` makes the query shorter and easier to understand.

---

# 10. Common Mistakes

### ❌ Mistake 1: Forgetting parentheses

Wrong:

```sql
WHERE salary IN 12000, 18000, 19000;
```

Correct:

```sql
WHERE salary IN (12000, 18000, 19000);
```

---

### ❌ Mistake 2: Forgetting quotes for character values

For character values:

```sql
WHERE job_id IN ('IT_PROG', 'ST_CLERK');
```

not:

```sql
WHERE job_id IN (IT_PROG, ST_CLERK);
```

---

### ❌ Mistake 3: Thinking IN means a range

```sql
salary IN (12000, 18000, 19000)
```

does **not** mean every salary from 12000 to 19000.

It means only these listed values:

```text
12000
18000
19000
```

---

# 11. Important Rules

1. `IN` checks a column against **multiple specified values**.
2. Values are written inside parentheses.
3. Values are separated by commas.
4. Character values are written inside single quotes.
5. `IN` can be understood as multiple `OR` conditions.
6. `IN` is different from `BETWEEN`.

---

# 12. Memory Trick

Remember:

> **IN = Is it IN this list?**

Example:

```sql
salary IN (12000, 18000, 19000)
```

Think:

```text
          Is salary
             ↓
     ┌───────┼────────┐
   12000   18000    19000
     ↓        ↓        ↓
    YES      YES      YES
```

If the value is one of the listed values → **selected**.

---

# 13. Interview Questions

### Q1. What is the IN operator?

`IN` is used to check whether a column value matches any one value from a specified list.

### Q2. What is the syntax of IN?

```sql
column_name IN (value1, value2, value3);
```

### Q3. What is the equivalent of IN?

```sql
salary IN (12000, 18000, 19000)
```

can be understood as:

```sql
salary = 12000
OR salary = 18000
OR salary = 19000
```

### Q4. What is the difference between IN and BETWEEN?

`IN` checks specific listed values, while `BETWEEN` checks a continuous range of values.

### Q5. Where are the values written in an IN operator?

Inside parentheses:

```sql
IN (value1, value2, value3)
```

---

# 14. Complete Questions + Queries

### Question 1

**Write a query to display all employees whose salary is 12000, 18000 or 19000.**

```sql
SELECT *
FROM emp
WHERE salary IN (12000, 18000, 19000);
```

### Question 2

**Write a query to display department id and department name where loc_id is 2500, 2700 or 2900.**

```sql
SELECT dept_id, dept_name
FROM dept
WHERE loc_id IN (2500, 2700, 2900);
```

### Final memory

```text
IN       → Specific values
BETWEEN  → Range
NOT BETWEEN → Outside range
```
