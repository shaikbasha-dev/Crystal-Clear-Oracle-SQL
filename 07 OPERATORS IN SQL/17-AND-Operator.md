# 17-AND-Operator

## 1. What is the AND Operator?

The **AND operator** is used in SQL when we want **all given conditions to be true**.

In simple words:

> **AND = Condition 1 must be TRUE AND Condition 2 must also be TRUE.**

If even **one condition is false**, the complete `AND` condition becomes false.

### Simple example

Suppose we ask:

> Find employees whose salary is `12000` **AND** whose job is `ST_CLERK`.

Both conditions must be satisfied by the same employee.

---

## 2. Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2;
```

Here:

* `condition1` → first condition
* `AND` → connects the conditions
* `condition2` → second condition

### Easy way to remember

```text
Condition 1  AND  Condition 2
     ↓              ↓
   TRUE           TRUE
        ↓
      RESULT
```

Both must be TRUE.

---

# 3. AND Operator — Query 1

### Question

**Write a query to display the details of employees whose salary is 12000 and whose job_id is `ST_CLERK`.**

### Answer / Query

```sql
SELECT *
FROM emp
WHERE salary = 12000
AND job_id = 'ST_CLERK';
```

### Explanation

There are two conditions:

```sql
salary = 12000
```

AND

```sql
job_id = 'ST_CLERK'
```

The employee must satisfy **both**.

For example:

| Employee   | Salary | JOB_ID   | Result         |
| ---------- | -----: | -------- | -------------- |
| Employee A |  12000 | ST_CLERK | ✅ Selected     |
| Employee B |  12000 | SA_REP   | ❌ Not selected |
| Employee C |  18000 | ST_CLERK | ❌ Not selected |

Why?

Because:

```text
12000 AND ST_CLERK
     ↓
Both conditions must match
     ↓
Only then employee is displayed
```

---

# 4. AND Operator — Query 2

### Question

**Write a query to display the details of employees whose department id is 22 and whose manager id is 100.**

### Answer / Query

```sql
SELECT *
FROM emp
WHERE dept_id = 22
AND manager_id = 100;
```

### Explanation

The query checks two conditions:

```sql
dept_id = 22
```

AND

```sql
manager_id = 100
```

Only employees satisfying **both conditions** are displayed.

### Think like this:

```text
Employee
   ↓
Is DEPT_ID 22?
   ↓ YES
Is MANAGER_ID 100?
   ↓ YES
Display employee
```

If either answer is `NO`, that employee is not displayed.

---

# 5. AND Truth Table

The basic idea can be remembered using this table:

| Condition 1 | Condition 2 | AND Result |
| ----------- | ----------- | ---------- |
| TRUE        | TRUE        | **TRUE**   |
| TRUE        | FALSE       | FALSE      |
| FALSE       | TRUE        | FALSE      |
| FALSE       | FALSE       | FALSE      |

### Memory Trick

> **AND means ALL conditions must be satisfied.**

---

# 6. Important Point

`AND` is normally used inside the `WHERE` clause when we want to apply **multiple conditions at the same time**.

For example:

```sql
WHERE condition1
AND condition2
```

means:

> Find rows where **condition1 AND condition2 are both true**.

---

# 7. Common Confusion

### `AND` vs `OR`

**AND**

```sql
WHERE salary = 12000
AND job_id = 'ST_CLERK'
```

Means:

> Salary must be 12000 **and** job must be ST_CLERK.

**OR**

```sql
WHERE salary = 12000
OR job_id = 'ST_CLERK'
```

Means:

> Salary can be 12000 **or** job can be ST_CLERK.

So:

```text
AND → ALL conditions
OR  → ANY condition
```

---

# 8. Interview Questions

### Q1. What is the AND operator in SQL?

**Answer:**
The `AND` operator is used to combine multiple conditions, and all the conditions must be true for a row to be selected.

### Q2. Where is AND commonly used?

**Answer:**
It is commonly used in the `WHERE` clause to apply multiple conditions.

### Q3. If one condition connected by AND is false, will the row be displayed?

**Answer:**
No. All conditions connected using `AND` must be true.

### Q4. What is the easiest way to remember AND?

**Answer:**

> **AND = ALL conditions must be TRUE.**
