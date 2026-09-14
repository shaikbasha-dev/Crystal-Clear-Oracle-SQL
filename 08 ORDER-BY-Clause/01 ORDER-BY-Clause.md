# 08-ORDER-BY-Clause

## 1. What is the ORDER BY Clause?

The `ORDER BY` clause is used when we want to display the **result of a SQL query in a specific order**.

Without `ORDER BY`, we should not assume that rows will be displayed in any particular order.

### Syntax

```sql
ORDER BY column_name [ASC | DESC];
```

* `ASC` → Ascending order
* `DESC` → Descending order

The notes also show that `ORDER BY` comes after `GROUP BY` and `HAVING` when those clauses are present. 

---

# 2. ASC — Ascending Order

`ASC` means arranging values from **lower to higher**.

Examples:

```text
10 → 20 → 30 → 40
A → B → C → D
Old date → New date
```

---

# 3. Query 1 — Employee Names in Ascending Order

### Question

**Write a query to display all the `f_name` of employees in the order of attendance.**

### Answer / Query

```sql
SELECT f_name
FROM emp
ORDER BY f_name ASC;
```

### Explanation

```sql
ORDER BY f_name ASC
```

arranges the employee first names in ascending/alphabetical order.

The output starts:

```text
Adam
Akash
Andy
Ashwin
Braven
DEEP
Daniel
Janardhan
...
```



---

# 4. Query 2 — Hire Date from Oldest to Newest

### Question

**Write a query to display the hire date from the oldest date to the newest date.**

### Answer / Query

```sql
SELECT hire_date
FROM emp
ORDER BY hire_date ASC;
```

### Explanation

Because `ASC` is used, the dates are displayed from the **oldest date to the newest date**.

The result begins:

```text
16-APR-07
27-SEP-08
25-OCT-08
30-DEC-08
...
28-AUG-12
```



---

# 5. Query 3 — Salary in Descending Order

### Question

**Write a query to display salaries of employees in descending order.**

### Answer / Query

```sql
SELECT salary
FROM emp
ORDER BY salary DESC;
```

### Explanation

`DESC` arranges the salaries from **highest to lowest**.

For example:

```text
85000
55000
53000
53000
46000
...
9500
```



### Memory

```text
DESC → Highest → Lowest
```

---

# 6. Query 4 — Commission Percentage in Ascending Order

### Question

**Write a query to display `commission_pct` in ascending order.**

### Answer / Query

```sql
SELECT commission_pct
FROM emp
ORDER BY commission_pct ASC;
```

### Explanation

The values are arranged from **lowest to highest**:

```text
0.15
0.20
0.20
0.30
0.50
0.75
0.90
1.20
...
1.50
```



---

# 7. Query 5 — Commission Percentage in Descending Order

### Question

**Write a query to display `commission_pct` in descending order.**

### Answer / Query

```sql
SELECT commission_pct
FROM emp
ORDER BY commission_pct DESC;
```

### Explanation

`DESC` arranges the commission percentages from **highest to lowest**.



---

# 8. ORDER BY with GROUP BY and HAVING

`ORDER BY` can also be used together with `WHERE`, `GROUP BY`, and `HAVING`.

The basic order is:

```text
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY
```

---

# 9. Query 6 — GROUP BY + HAVING + ORDER BY

### Question

**Write a query to display the department id and minimum salary for departments whose `dept_id` is greater than 10 and whose maximum salary is greater than 30000, and display the result in descending order with respect to `dept_id`.**

### Answer / Query

```sql
SELECT dept_id, min(salary)
FROM emp
WHERE dept_id > 10
GROUP BY dept_id
HAVING max(salary) > 30000
ORDER BY dept_id DESC;
```

### Explanation

The query works in stages:

```text
WHERE
  ↓
Keep departments having dept_id > 10

GROUP BY
  ↓
Create groups based on dept_id

HAVING
  ↓
Keep groups whose maximum salary > 30000

ORDER BY
  ↓
Display dept_id from highest to lowest
```

The result shown in the notes is:

```text
110
24
23
22
21
```

 

---

# 10. Query 7 — WHERE + GROUP BY + HAVING + ORDER BY

### Question

**Write a query to display department id and minimum salary for employees whose job id is `ST_CLERK` or `IT_PROG`, having the sum of salary less than 25000, group the result based on each department, and display the result in descending order.**

### Answer / Query

```sql
SELECT dept_id, min(salary)
FROM emp
WHERE job_id = 'ST_CLERK'
   OR job_id = 'IT_PROG'
GROUP BY dept_id
HAVING sum(salary) < 25000
ORDER BY dept_id DESC;
```

### Explanation

Here:

```sql
WHERE job_id = 'ST_CLERK'
   OR job_id = 'IT_PROG'
```

first selects employees having either of those job IDs.

Then:

```sql
GROUP BY dept_id
```

groups the employees department-wise.

Then:

```sql
HAVING sum(salary) < 25000
```

keeps only departments whose total salary is less than `25000`.

Finally:

```sql
ORDER BY dept_id DESC
```

displays the department IDs in **descending order**.

The result shown is:

```text
DEPT_ID   MIN(SALARY)
25        18000
23        12000
```



---

# 11. ASC vs DESC

| `ASC`                 | `DESC`                 |
| --------------------- | ---------------------- |
| Ascending             | Descending             |
| Low → High            | High → Low             |
| A → Z                 | Z → A                  |
| Old → New             | New → Old              |
| `ORDER BY column ASC` | `ORDER BY column DESC` |

### Easy memory trick

> **ASC = Ascending = going up**
> **DESC = Descending = going down**

---

# 12. Is ASC compulsory?

No.

If `ASC` or `DESC` is not specified, `ASC` is the default ordering.

For example:

```sql
ORDER BY salary;
```

is equivalent to:

```sql
ORDER BY salary ASC;
```

---

# 13. Important Rules

### Rule 1

`ORDER BY` controls the **display order of the result**.

### Rule 2

`ASC` means ascending.

### Rule 3

`DESC` means descending.

### Rule 4

When using `GROUP BY` and `HAVING`, `ORDER BY` comes after them.

```text
WHERE
 ↓
GROUP BY
 ↓
HAVING
 ↓
ORDER BY
```

### Rule 5

`ORDER BY` does not permanently rearrange the data stored in the table.

---

# 14. Interview Questions

### Q1. What is ORDER BY?

**Answer:**
`ORDER BY` is used to display the result of a SQL query in a specific order.

### Q2. What is ASC?

**Answer:**
`ASC` means ascending order.

### Q3. What is DESC?

**Answer:**
`DESC` means descending order.

### Q4. How do you display the highest salary first?

**Answer:**

```sql
SELECT salary
FROM emp
ORDER BY salary DESC;
```

### Q5. How do you display the oldest hire date first?

**Answer:**

```sql
SELECT hire_date
FROM emp
ORDER BY hire_date ASC;
```

### Q6. Where does ORDER BY come when GROUP BY and HAVING are used?

**Answer:**

```text
GROUP BY
   ↓
HAVING
   ↓
ORDER BY
```

### Q7. Does ORDER BY change the actual table data?

**Answer:**
No. It only controls the order in which the query result is displayed.

---

## Quick Revision

```text
ORDER BY → arrange result

ASC  → low to high
DESC → high to low

Without ASC/DESC → ASC is default

With GROUP BY/HAVING:

WHERE
 ↓
GROUP BY
 ↓
HAVING
 ↓
ORDER BY
```
