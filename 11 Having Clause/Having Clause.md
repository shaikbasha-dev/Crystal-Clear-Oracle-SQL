# 11 Having Clause

## 1. What is the HAVING Clause?

The **HAVING clause** is used to **filter groups** after `GROUP BY`.

Very simply:

* `WHERE` → filters **individual rows**
* `GROUP BY` → creates **groups**
* `HAVING` → filters **groups**

### Why was HAVING introduced?

The important point is:

> The `WHERE` keyword cannot be used with aggregate functions such as `MAX()`, `MIN()`, `SUM()`, `AVG()`, and `COUNT()`.

So SQL provides **HAVING** for filtering the result of aggregate functions. 

---

## 2. Simple Example

Suppose we want:

> Display departments whose **maximum salary is greater than 30,000**.

We cannot write:

```sql
WHERE MAX(salary) > 30000
```

Instead, we use:

```sql
HAVING MAX(salary) > 30000
```

Because `MAX(salary)` is calculated **after grouping**.

---

## 3. Syntax

```sql
SELECT column_name, aggregate_function(column_name)
FROM table_name
WHERE condition
GROUP BY column_name
HAVING aggregate_function(column_name) condition;
```

### Execution order to remember

```text
FROM
  ↓
WHERE
  ↓
GROUP BY
  ↓
HAVING
  ↓
SELECT
  ↓
ORDER BY
```

Think:

> **WHERE filters rows → GROUP BY creates groups → HAVING filters groups**

---

# 4. HAVING Queries

## Question 1

**Write a query to display the `dept_id` and the maximum salary of all employees whose maximum salary is greater than 30000.**

### Answer / Query

```sql
SELECT dept_id, MAX(salary)
FROM emp
GROUP BY dept_id
HAVING MAX(salary) > 30000;
```

### Explanation

First:

```sql
GROUP BY dept_id
```

creates one group for each department.

Then:

```sql
MAX(salary)
```

finds the highest salary in each department.

Finally:

```sql
HAVING MAX(salary) > 30000
```

keeps only those departments whose maximum salary is greater than `30000`. 

### Output

| DEPT_ID | MAX(SALARY) |
| ------: | ----------: |
|      22 |       85000 |
|      21 |       34000 |
|      24 |       55000 |
|     110 |       53000 |
|      23 |       46000 |

---

# 5. WHERE + GROUP BY + HAVING + ORDER BY

## Question 2

**Write a query to display the `dept_id` and maximum salary of all employees whose `dept_id` is greater than 10 and whose maximum salary is greater than 30000 for each department. Display the data in descending order with respect to `dept_id`.**

### Query given in the notes

```sql
SELECT dept_id, MIN(salary)
FROM emp
WHERE dept_id > 10
GROUP BY dept_id
HAVING MAX(salary) > 30000
ORDER BY dept_id DESC;
```

### Important correction ⚠️

There is a **mismatch between the question and the query**.

The question asks for:

```text
maximum salary
```

but the query selects:

```sql
MIN(salary)
```

So, if the intention is to answer the question exactly, it should be:

```sql
SELECT dept_id, MAX(salary)
FROM emp
WHERE dept_id > 10
GROUP BY dept_id
HAVING MAX(salary) > 30000
ORDER BY dept_id DESC;
```

The query shown in the notes uses `MIN(salary)` while the `HAVING` condition correctly uses `MAX(salary)`. 

### Understand each clause

```sql
WHERE dept_id > 10
```

First, select employees whose department ID is greater than 10.

```sql
GROUP BY dept_id
```

Then create groups based on department.

```sql
HAVING MAX(salary) > 30000
```

Then keep only departments whose maximum salary is greater than 30000.

```sql
ORDER BY dept_id DESC
```

Finally, display department IDs from highest to lowest.

---

# 6. Another HAVING Example

## Question 3

**Write a query to display the department ID and minimum salary for employees whose job ID is `ST_CLERK` or `IT_PROG`, having the sum of salary less than 25000. Group the result based on each department and display the result in descending order.**

### Answer / Query

```sql
SELECT dept_id, MIN(salary)
FROM emp
WHERE job_id = 'ST_CLERK' OR job_id = 'IT_PROG'
GROUP BY dept_id
HAVING SUM(salary) < 25000
ORDER BY dept_id DESC;
```

### Explanation

### Step 1 — WHERE

```sql
WHERE job_id = 'ST_CLERK' OR job_id = 'IT_PROG'
```

First, select only employees whose job is:

```text
ST_CLERK
```

or

```text
IT_PROG
```

### Step 2 — GROUP BY

```sql
GROUP BY dept_id
```

Put those employees into groups according to department.

### Step 3 — MIN

```sql
MIN(salary)
```

Find the minimum salary in each department.

### Step 4 — HAVING

```sql
HAVING SUM(salary) < 25000
```

Calculate the total salary of each department group and keep only groups whose total is less than `25000`.

### Step 5 — ORDER BY

```sql
ORDER BY dept_id DESC
```

Display department IDs in descending order.

The result shown is:

| DEPT_ID | MIN(SALARY) |
| ------: | ----------: |
|      25 |       18000 |
|      23 |       12000 |



---

# 7. HAVING vs WHERE

| WHERE                                                           | HAVING                                  |
| --------------------------------------------------------------- | --------------------------------------- |
| Filters rows                                                    | Filters groups                          |
| Used before `GROUP BY`                                          | Used after `GROUP BY`                   |
| Normally used for individual-row conditions                     | Commonly used with aggregate conditions |
| Example: `WHERE dept_id > 10`                                   | Example: `HAVING MAX(salary) > 30000`   |
| Cannot be used to filter an aggregate result like `MAX(salary)` | Can filter aggregate results            |

### Easy memory trick

```text
WHERE  → Which ROWS should I take?
HAVING → Which GROUPS should I keep?
```

---

# 8. Most Important Difference

Suppose we have:

```sql
SELECT dept_id, MAX(salary)
FROM emp
WHERE dept_id > 10
GROUP BY dept_id
HAVING MAX(salary) > 30000;
```

Understand it like this:

```text
EMP table
   ↓
WHERE dept_id > 10
   ↓
Filtered rows
   ↓
GROUP BY dept_id
   ↓
Department groups
   ↓
MAX(salary)
   ↓
HAVING MAX(salary) > 30000
   ↓
Final groups
```

---

# 9. Important Rules

### Rule 1

`HAVING` is mainly used with `GROUP BY`.

### Rule 2

`HAVING` is useful when the condition involves an **aggregate function**.

Examples:

```sql
HAVING MAX(salary) > 30000
```

```sql
HAVING SUM(salary) < 25000
```

### Rule 3

`WHERE` comes before `GROUP BY`.

```sql
WHERE
GROUP BY
HAVING
```

### Rule 4

`HAVING` filters the **groups**, not the original individual rows.

---

# 10. Interview Questions

### Q1. Why do we need HAVING?

**Answer:**
HAVING is used to filter groups created by `GROUP BY`, especially when the condition involves aggregate functions.

### Q2. Can WHERE be used with `MAX()`?

**Answer:**
No. `WHERE` cannot be used to filter aggregate-function results. `HAVING` is used for that purpose.

### Q3. What is the difference between WHERE and HAVING?

**Answer:**
`WHERE` filters individual rows before grouping, whereas `HAVING` filters groups after `GROUP BY`.

### Q4. Can HAVING use aggregate functions?

**Answer:**
Yes.

Example:

```sql
HAVING MAX(salary) > 30000
```

### Q5. Which comes first: WHERE or HAVING?

**Answer:**

```text
WHERE → GROUP BY → HAVING
```

---

## 11. One-Line Memory Trick 🧠

> **WHERE filters ROWS, HAVING filters GROUPS.**

And remember the most important pattern:

```sql
SELECT ...
FROM ...
WHERE ...
GROUP BY ...
HAVING ...
ORDER BY ...;
```
