# 12 SUB QUERIES OR INNER QUERY OR NESTED QUERY IN SQL

## 1. What is a Subquery?

A **Subquery** is a query written inside another SQL query.

It is also called:

* **Inner Query**
* **Nested Query**

The subquery is embedded within the `WHERE` clause and returns data that is used by the main query as a condition to further restrict the data. 

### Simple idea

```text
        MAIN QUERY
            ↓
     needs some value
            ↓
       SUBQUERY
            ↓
      finds the value
            ↓
        MAIN QUERY
            ↓
       final result
```

---

# 2. Main Query and Subquery

Consider this:

```sql
SELECT l_name, f_name, salary
FROM emp
WHERE salary > (SELECT salary
                FROM emp
                WHERE l_name = 'Pandey');
```

There are **two queries**.

### Inner Query / Subquery

```sql
SELECT salary
FROM emp
WHERE l_name = 'Pandey';
```

This finds Pandey's salary.

### Main Query / Outer Query

```sql
SELECT l_name, f_name, salary
FROM emp
WHERE salary > (...);
```

This finds employees whose salary is greater than Pandey's salary.

### Easy memory trick

> **Subquery finds the required information → Main query uses that information.**

---

# 3. Properties of Subqueries

There are **4 important properties** in this section.

### Property 1 — Parentheses

A subquery must be enclosed within parentheses.

```sql
WHERE salary > (SELECT salary FROM emp ...);
```



---

### Property 2 — SELECT columns

A subquery can have only **one column in its `SELECT` clause**, unless multiple columns are being compared by the main query.



---

### Property 3 — ORDER BY

`ORDER BY` cannot be used in a subquery, although the main query can use `ORDER BY`.

The material also states that `GROUP BY` can be used to perform the same function as `ORDER BY` in a subquery. 

---

### Property 4 — Multiple rows

A subquery that returns more than one row can be used with a **multiple-value operator**, such as `IN`.



---

# 4. Subquery Query 1

## Question

**Write a query to display the `l_name`, `f_name` and `salary` of all employees who earn more than Pandey.**

### Answer / Query

```sql
SELECT l_name, f_name, salary
FROM emp
WHERE salary > (SELECT salary
                FROM emp
                WHERE l_name = 'Pandey');
```

### Step-by-step

### Step 1 — Execute the subquery

```sql
SELECT salary
FROM emp
WHERE l_name = 'Pandey';
```

This finds the salary of Pandey.

### Step 2 — Main query uses that salary

The main query asks:

```text
Who earns more than Pandey?
```

So:

```sql
WHERE salary > Pandey's salary
```

### Result

| L_NAME   | F_NAME      | SALARY |
| -------- | ----------- | -----: |
| Ganeshan | Prabhakaran |  45000 |
| Nair     | DEEP        |  55000 |
| K        | Ashwin      |  36000 |
| Raj      | Shashi      |  85000 |
| Sam      | Adam        |  53000 |
| Devraj   | Meghana     |  53000 |
| Bhupathi | Braven      |  45500 |
| T        | Mamatha     |  46000 |
| patel    | Pankaj      |  39500 |



---

# 5. Subquery Query 2

## Question

**Write a query to display the `dept_id` and the `f_name` for all employees who work in the same department in which `Prabhakaran` works.**

### Answer / Query

```sql
SELECT dept_id, f_name
FROM emp
WHERE dept_id = (SELECT dept_id
                 FROM emp
                 WHERE f_name = 'Prabhakaran');
```

### Step 1 — Execute the subquery

```sql
SELECT dept_id
FROM emp
WHERE f_name = 'Prabhakaran';
```

This finds Prabhakaran's department.

The department is:

```text
22
```

### Step 2 — Main query

The main query effectively searches for:

```sql
SELECT dept_id, f_name
FROM emp
WHERE dept_id = 22;
```

### Result

| DEPT_ID | F_NAME      |
| ------: | ----------- |
|      22 | Prabhakaran |
|      22 | Shashi      |
|      22 | Andy        |
|      22 | Braven      |
|      22 | Pankaj      |
|      22 | Janardhan   |



---

# 6. Subquery Query 3 — `IN`

## Question

**Write a query to display the `dept_id`, `f_name` and the `job_id` for all employees who work in administration department.**

### Answer / Query

```sql
SELECT dept_id, f_name, job_id
FROM emp
WHERE dept_id IN
      (SELECT dept_id
       FROM dept
       WHERE dept_name = 'Admin');
```

### Understand the subquery

```sql
SELECT dept_id
FROM dept
WHERE dept_name = 'Admin';
```

The subquery searches the `DEPT` table for the department whose name is `Admin`.

Then:

```sql
WHERE dept_id IN (...)
```

checks employee department IDs against the department IDs returned by the subquery.

### Result shown

```text
no data found
```



---

# 7. Subquery Query 4 — `IN`

## Question

**Write a query to display the `emp_id` of all the employees whose `dept_id` in the employees table is equal to `dept_id` in the department table.**

### Answer / Query

```sql
SELECT emp_id
FROM emp
WHERE dept_id IN
      (SELECT dept_id
       FROM dept);
```

### Understand it

The inner query:

```sql
SELECT dept_id
FROM dept;
```

gets the department IDs from the `DEPT` table.

The outer query:

```sql
SELECT emp_id
FROM emp
WHERE dept_id IN (...);
```

finds employees whose department ID exists in the `DEPT` table.

### Result

The notes show the employee IDs:

```text
1
2
3
4
5
7
8
9
10
11
12
13
14
15
16
17
18
19
20
```



---

# 8. Subquery Query 5 — Two Subqueries

This query is especially important because it contains **two subqueries**.

## Question

**Write a query to display the `l_name` and `job_id` whose `job_id` is similar to `King` and whose salary is greater than Singh's salary.**

### Answer / Query

```sql
SELECT l_name, job_id
FROM emp
WHERE (job_id = (SELECT job_id
                 FROM emp
                 WHERE l_name = 'King')
       AND
       (salary > (SELECT salary
                  FROM emp
                  WHERE l_name = 'singh')));
```

### Understand the first subquery

```sql
SELECT job_id
FROM emp
WHERE l_name = 'King';
```

This finds **King's job ID**.

The main query then checks:

```text
job_id = King's job_id
```

### Understand the second subquery

```sql
SELECT salary
FROM emp
WHERE l_name = 'singh';
```

This finds **Singh's salary**.

The main query then checks:

```text
salary > Singh's salary
```

### Both conditions must be true

```text
King's job_id
     +
salary greater than Singh's salary
     ↓
AND
     ↓
final employees
```

### Result shown

```text
no data found
```



---

# 9. All Subquery Queries at One Place

There are **5 queries** in this Subquery section:

### 1. Employees earning more than Pandey

```sql
SELECT l_name, f_name, salary
FROM emp
WHERE salary > (SELECT salary
                FROM emp
                WHERE l_name = 'Pandey');
```

### 2. Employees in Prabhakaran's department

```sql
SELECT dept_id, f_name
FROM emp
WHERE dept_id = (SELECT dept_id
                 FROM emp
                 WHERE f_name = 'Prabhakaran');
```

### 3. Employees working in Administration department

```sql
SELECT dept_id, f_name, job_id
FROM emp
WHERE dept_id IN
      (SELECT dept_id
       FROM dept
       WHERE dept_name = 'Admin');
```

### 4. Employees whose department exists in DEPT

```sql
SELECT emp_id
FROM emp
WHERE dept_id IN
      (SELECT dept_id
       FROM dept);
```

### 5. Employees matching King's job and earning more than Singh

```sql
SELECT l_name, job_id
FROM emp
WHERE (job_id = (SELECT job_id
                 FROM emp
                 WHERE l_name = 'King')
       AND
       (salary > (SELECT salary
                  FROM emp
                  WHERE l_name = 'singh')));
```

---

# 10. `=` vs `IN` in Subqueries

This is important for understanding the queries.

### `=`

Use when the subquery returns **one value**.

Example:

```sql
WHERE salary > (SELECT salary ...)
```

or:

```sql
WHERE dept_id = (SELECT dept_id ...)
```

### `IN`

Used when the subquery can return **multiple values**.

Example:

```sql
WHERE dept_id IN (SELECT dept_id FROM dept);
```

This matches the rule that multiple-row subqueries can be used with multiple-value operators such as `IN`. 

---

# 11. One Complete Execution Example

Take:

```sql
SELECT dept_id, f_name
FROM emp
WHERE dept_id = (SELECT dept_id
                 FROM emp
                 WHERE f_name = 'Prabhakaran');
```

Think of it as two separate questions.

### Inner question

> **Which department does Prabhakaran work in?**

```sql
SELECT dept_id
FROM emp
WHERE f_name = 'Prabhakaran';
```

Answer:

```text
22
```

### Outer question

> **Who works in department 22?**

```sql
SELECT dept_id, f_name
FROM emp
WHERE dept_id = 22;
```

Answer:

```text
Prabhakaran
Shashi
Andy
Braven
Pankaj
Janardhan
```

This is exactly why we use a subquery: **the main query needs information that another query can find first.**

---

# 12. Common Interview Questions

### Q1. What is a subquery?

A subquery is a query within another SQL query. It is also called an inner query or nested query.

### Q2. What is the outer query?

The query containing the subquery is called the **main query or outer query**.

### Q3. What is the inner query?

The query written inside the main query is called the **subquery or inner query**.

### Q4. Where is the subquery embedded in these notes?

The subquery is embedded within the `WHERE` clause.

### Q5. Should a subquery be enclosed in parentheses?

Yes.

```sql
(SELECT ...)
```

### Q6. Can a subquery return multiple rows?

Yes. When it returns multiple rows, a multiple-value operator such as `IN` can be used.

### Q7. Why do we use a subquery?

To obtain data that can be used by the main query as a condition to further restrict the data retrieved.

---

# 13. Final Memory Trick 🧠

Remember this:

```text
SUBQUERY
   ↓
"Find the information first"

MAIN QUERY
   ↓
"Use that information"

FINAL RESULT
```

Or simply:

> **Inner Query → Finds the value → Outer Query → Uses the value**
