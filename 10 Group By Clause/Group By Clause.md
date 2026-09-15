# 10 Group By Clause

## 1. What is GROUP BY?

`GROUP BY` is used to **arrange rows having identical values into groups**.

It is mainly used with multirow/aggregate functions such as:

* `SUM()`
* `MIN()`
* `MAX()`
* `COUNT()`
* `AVG()`

The basic idea is:

```text
EMP table
   ↓
GROUP BY DEPT_ID
   ↓
Employees are separated department-wise
   ↓
Apply SUM / MIN / MAX / COUNT / AVG
```

The `GROUP BY` clause comes **after `WHERE`** and **before `ORDER BY`**. 

---

# 2. Basic Syntax

```sql
SELECT column_name, aggregate_function(column_name)
FROM table_name
GROUP BY column_name;
```

Example:

```sql
SELECT dept_id, SUM(salary)
FROM emp
GROUP BY dept_id;
```

---

# 3. GROUP BY with SUM()

### Question

**Write a query to display the department_id and the sum of the salary for all the employees in each department.**

### Answer / Query

```sql
SELECT dept_id, SUM(salary)
FROM emp
GROUP BY dept_id;
```

### Explanation

`GROUP BY dept_id` creates one group for every department.

Then `SUM(salary)` calculates the total salary of each department.

### Output

```text
DEPT_ID    SUM(SALARY)
22         273000
25         18000
21         34000
24         120000
110        128000
23         102500
```



---

# 4. GROUP BY with MIN()

### Question

**Write a query to display the dept_id and the least salary of each department.**

### Answer / Query

```sql
SELECT dept_id, MIN(salary)
FROM emp
GROUP BY dept_id;
```

### Explanation

The employees are first divided into department-wise groups.

Then `MIN(salary)` finds the **lowest salary in each department**.

### Output

```text
DEPT_ID    MIN(SALARY)
22         28500
25         18000
21         34000
24         12000
110        9500
23         12000
```



---

# 5. GROUP BY with WHERE and MAX()

### Question

**Display the dept_id and highest salary of each department for all departments whose department_id is greater than 50.**

### Answer / Query

```sql
SELECT dept_id, MAX(salary)
FROM emp
WHERE dept_id > 50
GROUP BY dept_id;
```

### Step-by-step

```text
WHERE dept_id > 50
        ↓
Select required employees
        ↓
GROUP BY dept_id
        ↓
Create department groups
        ↓
MAX(salary)
        ↓
Find highest salary in each group
```

### Output

```text
DEPT_ID    MAX(SALARY)
110        53000
```



---

# 6. GROUP BY with WHERE and COUNT()

### Question

**Write a query to display the dept_id and count of the dept_id for all the employees whose department ID is equal to 90.**

### Answer / Query

```sql
SELECT dept_id, COUNT(dept_id)
FROM emp
WHERE dept_id = 90
GROUP BY dept_id;
```

### Explanation

First, `WHERE` searches for employees whose department is `90`.

Then `GROUP BY` groups them.

Then `COUNT()` counts the department IDs.

### Output shown

```text
no data found
```



---

# 7. GROUP BY with HAVING

## What is HAVING?

`HAVING` is used to **filter groups**.

Remember:

```text
WHERE
  ↓
Filters rows

HAVING
  ↓
Filters groups
```

The notes explain that `HAVING` was introduced because `WHERE` cannot be used with aggregate functions. 

---

### Question

**Write a query to display the dept_id and the maximum salary of all the employees whose maximum salary is greater than 30000.**

### Answer / Query

```sql
SELECT dept_id, MAX(salary)
FROM emp
GROUP BY dept_id
HAVING MAX(salary) > 30000;
```

### Step-by-step

First:

```sql
GROUP BY dept_id
```

creates department-wise groups.

Then:

```sql
MAX(salary)
```

finds the maximum salary in every department.

Finally:

```sql
HAVING MAX(salary) > 30000
```

keeps only departments whose maximum salary is greater than `30000`.

### Output

```text
DEPT_ID    MAX(SALARY)
22         85000
21         34000
24         55000
110        53000
23         46000
```



---

# 8. GROUP BY + WHERE + HAVING + ORDER BY

This is the complete combination:

```text
SELECT
   ↓
FROM
   ↓
WHERE
   ↓
GROUP BY
   ↓
HAVING
   ↓
ORDER BY
```

---

### Question

**Write a query to display the dept_id and maximum salary of all employees whose dept_id is greater than 10 and whose maximum salary is greater than 30000 for each department, and display the data in descending order with respect to dept_id.**

### Answer / Query from the notes

```sql
SELECT dept_id, MIN(salary)
FROM emp
WHERE dept_id > 10
GROUP BY dept_id
HAVING MAX(salary) > 30000
ORDER BY dept_id DESC;
```

### Important correction

There is a **question/query mismatch** here.

The question asks for:

```text
maximum salary
```

but the query selects:

```sql
MIN(salary)
```

So the query actually displays the **minimum salary** of qualifying departments, while `HAVING MAX(salary) > 30000` is used to decide which groups qualify.

### Output shown

```text
DEPT_ID    MIN(SALARY)
110        9500
24         12000
23         12000
22         28500
21         34000
```



---

# 9. GROUP BY with WHERE, HAVING and ORDER BY

### Question

**Write a query to display department id and minimum salary whose job id is ST_CLERK or IT_PROG, having the sum of salary less than 25000, group the result based on each department and display the result in descending order.**

### Answer / Query

```sql
SELECT dept_id, MIN(salary)
FROM emp
WHERE job_id = 'ST_CLERK'
   OR job_id = 'IT_PROG'
GROUP BY dept_id
HAVING SUM(salary) < 25000
ORDER BY dept_id DESC;
```

### Step-by-step

### Step 1 — WHERE

```sql
WHERE job_id = 'ST_CLERK'
   OR job_id = 'IT_PROG'
```

Selects employees whose job is either:

```text
ST_CLERK
OR
IT_PROG
```

### Step 2 — GROUP BY

```sql
GROUP BY dept_id
```

Groups the selected employees department-wise.

### Step 3 — HAVING

```sql
HAVING SUM(salary) < 25000
```

Keeps only departments whose **total salary is less than 25000**.

### Step 4 — ORDER BY

```sql
ORDER BY dept_id DESC
```

Displays department IDs in descending order.

### Output

```text
DEPT_ID    MIN(SALARY)
25         18000
23         12000
```



---

# 10. Very Important Difference

| Clause     | Works on        | Purpose        |
| ---------- | --------------- | -------------- |
| `WHERE`    | Individual rows | Filters rows   |
| `GROUP BY` | Rows            | Creates groups |
| `HAVING`   | Groups          | Filters groups |
| `ORDER BY` | Final result    | Sorts result   |

### Easy memory trick

```text
WHERE
↓
WHO should enter?

GROUP BY
↓
HOW should they be grouped?

HAVING
↓
WHICH groups should remain?

ORDER BY
↓
HOW should the final result be arranged?
```

---

# 11. Complete GROUP BY Flow

For a query like:

```sql
SELECT dept_id, MIN(salary)
FROM emp
WHERE dept_id > 10
GROUP BY dept_id
HAVING MAX(salary) > 30000
ORDER BY dept_id DESC;
```

Think like this:

```text
EMP
 │
 ▼
WHERE
Filter rows
 │
 ▼
GROUP BY
Create department groups
 │
 ▼
Aggregate Function
MIN / MAX / SUM / COUNT / AVG
 │
 ▼
HAVING
Filter groups
 │
 ▼
ORDER BY
Sort final result
```

### One-line interview answer

> **GROUP BY is used to arrange rows having identical values into groups, usually so aggregate functions can produce a result for each group.** 
