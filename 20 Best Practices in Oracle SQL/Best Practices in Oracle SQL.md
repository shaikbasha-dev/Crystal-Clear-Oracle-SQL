# 20 Best Practices in Oracle SQL

This is the **final practical layer** of your Oracle SQL preparation.

The goal here is not just to remember SQL syntax. You should be able to:

1. **Understand the concept**
2. **Write the query**
3. **Predict the output**
4. **Explain the query in an interview**
5. **Solve an unfamiliar/difficult query**
6. **Debug a wrong query**
7. **Improve a query**
8. **Design tables properly**
9. **Choose the correct SQL technique**
10. **Think like a SQL developer**

The important areas for practice include fundamentals, functions, grouping, subqueries, joins, database design, optimization, and interview-style problems. 

---

# 1. Use Meaningful Table Names and Column Names

A database should be understandable just by looking at it.

### ❌ Poor naming

```sql
CREATE TABLE T1 (
    C1 NUMBER,
    C2 VARCHAR2(50),
    C3 NUMBER
);
```

We don't know what `C1`, `C2`, and `C3` represent.

### ✅ Better naming

```sql
CREATE TABLE EMPLOYEE (
    EMPLOYEE_ID NUMBER,
    EMPLOYEE_NAME VARCHAR2(50),
    SALARY NUMBER
);
```

### Why?

A developer immediately understands:

```text
EMPLOYEE
   |
   ├── EMPLOYEE_ID
   ├── EMPLOYEE_NAME
   └── SALARY
```

Meaningful table and column names are one of the recommended SQL practices. 

### Interview representation

> "I prefer meaningful and descriptive table and column names because they improve readability, maintainability, and reduce confusion when writing joins and complex queries."

---

# 2. Write Readable SQL

SQL should be formatted so another developer can understand it.

### Question

Display employees whose salary is greater than 30000 and sort them by salary descending.

### Answer / Query

```sql
SELECT EMPLOYEE_ID,
       EMPLOYEE_NAME,
       SALARY
FROM EMPLOYEE
WHERE SALARY > 30000
ORDER BY SALARY DESC;
```

### Explanation

```text
SELECT       → what columns?
FROM         → from which table?
WHERE        → which rows?
ORDER BY     → how should result be sorted?
```

### Output

```text
EMPLOYEE_ID | EMPLOYEE_NAME | SALARY
-------------------------------------
104         | Ravi          | 60000
102         | Basha         | 50000
101         | Kumar         | 40000
```

Readable formatting is specifically recommended for maintainable SQL. 

---

# 3. Use Uppercase SQL Keywords

A common professional convention is:

```sql
SELECT
FROM
WHERE
GROUP BY
HAVING
ORDER BY
```

while table and column names remain descriptive.

### Example

```sql
SELECT EMPLOYEE_NAME, SALARY
FROM EMPLOYEE
WHERE SALARY > 30000
ORDER BY SALARY DESC;
```

This makes SQL easier to scan.

---

# 4. Avoid Unnecessary `SELECT *`

`SELECT *` means:

> Select every column.

### Question

Display only employee name and salary.

### ❌ Unnecessary

```sql
SELECT *
FROM EMPLOYEE;
```

### ✅ Better

```sql
SELECT EMPLOYEE_NAME,
       SALARY
FROM EMPLOYEE;
```

### Why?

Because you only need two columns.

It:

* Makes the query clearer
* Returns only required data
* Avoids depending on every column in the table
* Is preferable in production code

Avoiding unnecessary `SELECT *` is explicitly recommended. 

---

# 5. Understand the Purpose of Every Clause

Do not memorize:

```text
SELECT → FROM → WHERE → GROUP BY → HAVING → ORDER BY
```

Understand **why** each exists.

### Question

Find departments whose average salary is greater than 50000.

### Answer / Query

```sql
SELECT DEPTNO,
       AVG(SALARY) AS AVG_SALARY
FROM EMPLOYEE
GROUP BY DEPTNO
HAVING AVG(SALARY) > 50000;
```

### Explanation

```text
FROM
 ↓
Take rows from EMPLOYEE

GROUP BY
 ↓
Create groups department-wise

AVG()
 ↓
Calculate average for each group

HAVING
 ↓
Keep only groups whose average > 50000
```

### Important distinction

```text
WHERE  → filters individual rows
HAVING → filters groups
```

Understanding why `WHERE`, `GROUP BY`, `HAVING`, and `JOIN` exist is more valuable than simply memorizing their syntax. 

---

# 6. Always Think About NULL

`NULL` means:

> Missing / unknown / unavailable value.

Do **not** write:

```sql
WHERE COMMISSION = NULL
```

### Correct

```sql
SELECT EMPLOYEE_NAME,
       COMMISSION
FROM EMPLOYEE
WHERE COMMISSION IS NULL;
```

### Question

Find employees who do not receive commission.

### Answer / Query

```sql
SELECT EMPLOYEE_NAME
FROM EMPLOYEE
WHERE COMMISSION IS NULL;
```

### Output

```text
EMPLOYEE_NAME
-------------
KUMAR
RAVI
```

### Remember

```text
NULL = NULL       ❌
IS NULL           ✅
IS NOT NULL       ✅
```

NULL behavior should always be checked when analyzing query results. 

---

# 7. Choose the Correct Operator

Before writing a long query, ask:

> "Which operator naturally solves this?"

Examples:

```sql
=
<>
>
<
>=
<=
BETWEEN
IN
LIKE
IS NULL
IS NOT NULL
```

### Question

Find employees whose salary is between 30000 and 50000.

### Answer / Query

```sql
SELECT EMPLOYEE_NAME,
       SALARY
FROM EMPLOYEE
WHERE SALARY BETWEEN 30000 AND 50000;
```

### Output

```text
EMPLOYEE_NAME | SALARY
----------------------
KUMAR         | 30000
BASHA         | 40000
RAVI          | 50000
```

### Important

`BETWEEN` is inclusive.

```text
30000 ≤ SALARY ≤ 50000
```

---

# 8. Master Aggregate Functions

The important aggregate functions are:

```text
COUNT()
SUM()
AVG()
MAX()
MIN()
```

### Question

Find the maximum, minimum, average, and total salary.

### Answer / Query

```sql
SELECT MAX(SALARY) AS MAX_SALARY,
       MIN(SALARY) AS MIN_SALARY,
       AVG(SALARY) AS AVG_SALARY,
       SUM(SALARY) AS TOTAL_SALARY,
       COUNT(SALARY) AS SALARY_COUNT
FROM EMPLOYEE;
```

### Explanation

| Function  | Purpose |
| --------- | ------- |
| `MAX()`   | Highest |
| `MIN()`   | Lowest  |
| `AVG()`   | Average |
| `SUM()`   | Total   |
| `COUNT()` | Count   |

### Interview representation

> "Aggregate functions operate on multiple rows and return a single result for the group or entire result set."

---

# 9. Use GROUP BY Correctly

Whenever the question contains:

```text
department-wise
job-wise
location-wise
course-wise
category-wise
```

immediately think:

> **GROUP BY**

### Question

Count employees department-wise.

### Answer / Query

```sql
SELECT DEPTNO,
       COUNT(*) AS EMPLOYEE_COUNT
FROM EMPLOYEE
GROUP BY DEPTNO;
```

### Output

```text
DEPTNO | EMPLOYEE_COUNT
-----------------------
10     | 3
20     | 5
30     | 2
```

### Memory

```text
"wise" → GROUP BY
```

This is one of the intermediate practice areas emphasized for SQL mastery. 

---

# 10. Know WHERE vs HAVING

This is a **very common interview question**.

## WHERE

Filters rows **before grouping**.

## HAVING

Filters groups **after grouping**.

### Question

Find departments having more than 3 employees.

### Answer / Query

```sql
SELECT DEPTNO,
       COUNT(*) AS EMPLOYEE_COUNT
FROM EMPLOYEE
GROUP BY DEPTNO
HAVING COUNT(*) > 3;
```

### Why not WHERE?

This is incorrect:

```sql
SELECT DEPTNO,
       COUNT(*)
FROM EMPLOYEE
WHERE COUNT(*) > 3
GROUP BY DEPTNO;
```

Because `COUNT(*)` is an aggregate calculation and group filtering belongs in `HAVING`.

### Interview answer

> "`WHERE` filters individual rows, whereas `HAVING` filters grouped results."

---

# 11. Use Functions According to the Problem

Do not memorize functions randomly.

Think about what the question asks.

### Character problem

```text
Convert employee name to uppercase
```

### Query

```sql
SELECT UPPER(EMPLOYEE_NAME)
FROM EMPLOYEE;
```

### Number problem

```text
Round salary
```

### Query

```sql
SELECT ROUND(SALARY)
FROM EMPLOYEE;
```

### Date problem

```text
Display joining year
```

### Query

```sql
SELECT EMPLOYEE_NAME,
       EXTRACT(YEAR FROM JOIN_DATE) AS JOIN_YEAR
FROM EMPLOYEE;
```

### Conversion problem

```sql
SELECT TO_CHAR(JOIN_DATE, 'DD-MM-YYYY')
FROM EMPLOYEE;
```

### Thinking pattern

```text
Character → Character Function
Number    → Number Function
Date      → Date Function
Datatype conversion → Conversion Function
```

---

# 12. Master Joins

Joins are one of the most important Oracle SQL interview areas.

You should be comfortable with:

```text
INNER JOIN
LEFT OUTER JOIN
RIGHT OUTER JOIN
FULL OUTER JOIN
SELF JOIN
CROSS JOIN
Multiple-table JOIN
```

These are specifically identified as advanced practice areas. 

---

## INNER JOIN

### Question

Display employee name and department name.

### Answer / Query

```sql
SELECT E.EMPLOYEE_NAME,
       D.DEPARTMENT_NAME
FROM EMPLOYEE E
INNER JOIN DEPARTMENT D
    ON E.DEPTNO = D.DEPTNO;
```

### Explanation

Only employees having a matching department are returned.

---

## LEFT JOIN

### Question

Display all employees, including employees who do not belong to a department.

### Answer / Query

```sql
SELECT E.EMPLOYEE_NAME,
       D.DEPARTMENT_NAME
FROM EMPLOYEE E
LEFT JOIN DEPARTMENT D
    ON E.DEPTNO = D.DEPTNO;
```

### Memory

```text
LEFT JOIN
   ↓
Keep everything from LEFT table
```

---

# 13. Learn SELF JOIN

A self join means:

> A table is joined with itself.

The classic example is employee-manager relationship.

Suppose:

```text
EMPLOYEE
----------------------------
EMPLOYEE_ID
EMPLOYEE_NAME
MANAGER_ID
```

### Question

Display employee name and manager name.

### Answer / Query

```sql
SELECT E.EMPLOYEE_NAME AS EMPLOYEE,
       M.EMPLOYEE_NAME AS MANAGER
FROM EMPLOYEE E
LEFT JOIN EMPLOYEE M
    ON E.MANAGER_ID = M.EMPLOYEE_ID;
```

### Explanation

We use the same table twice:

```text
E → employee
M → manager
```

### Interview answer

> "A self join is a join in which a table is joined with itself, usually using different aliases. It is useful for hierarchical relationships such as employee-manager."

---

# 14. Use Subqueries When the Question Has Two Logical Steps

A very important difficult-query technique is:

> **Solve the inner problem first, then use its result in the outer query.**

### Question

Find employees earning more than the average salary.

### Step 1 — Find average salary

```sql
SELECT AVG(SALARY)
FROM EMPLOYEE;
```

Suppose:

```text
AVG(SALARY)
-----------
45000
```

### Step 2 — Find employees above it

### Answer / Query

```sql
SELECT EMPLOYEE_NAME,
       SALARY
FROM EMPLOYEE
WHERE SALARY > (
    SELECT AVG(SALARY)
    FROM EMPLOYEE
);
```

### Explanation

Inner query:

```sql
SELECT AVG(SALARY)
FROM EMPLOYEE
```

produces one value.

Outer query:

```sql
WHERE SALARY > ...
```

compares every employee against that value.

### Interview representation

> "I first calculate the average salary using a scalar subquery and then filter employees whose salary is greater than that result."

---

# 15. Learn Correlated Subqueries

A correlated subquery depends on the current row of the outer query.

### Question

Find employees whose salary is greater than the average salary of their own department.

### Answer / Query

```sql
SELECT E.EMPLOYEE_NAME,
       E.DEPTNO,
       E.SALARY
FROM EMPLOYEE E
WHERE E.SALARY > (
    SELECT AVG(E2.SALARY)
    FROM EMPLOYEE E2
    WHERE E2.DEPTNO = E.DEPTNO
);
```

### Think like this

For each employee:

```text
Take employee's department
        ↓
Find average salary of that department
        ↓
Compare employee salary with department average
        ↓
Return employee if salary is higher
```

### Why is it correlated?

Because the inner query refers to:

```sql
E.DEPTNO
```

from the outer query.

Correlated subqueries are specifically part of advanced SQL practice. 

---

# 16. Learn the Most Common Interview Query Patterns

These should become automatic patterns in your mind.

The practical interview set includes second highest salary, Nth highest salary, employees without managers, highest salary department-wise, duplicates, Top N, ranking, year-based joining, department reports, counts, aggregates, above-average salary, multiple departments, joins, and correlated subqueries. 

---

## Pattern 1 — Maximum Salary

### Question

Find the highest salary.

### Query

```sql
SELECT MAX(SALARY) AS MAX_SALARY
FROM EMPLOYEE;
```

### Output

```text
MAX_SALARY
----------
90000
```

---

# 17. Second Highest Salary

This is one of the most famous SQL interview questions.

### Question

Find the second highest distinct salary.

### Query

```sql
SELECT MAX(SALARY) AS SECOND_HIGHEST
FROM EMPLOYEE
WHERE SALARY < (
    SELECT MAX(SALARY)
    FROM EMPLOYEE
);
```

### Logic

First:

```text
Find maximum salary
```

Then:

```text
Remove salaries equal to maximum
```

Then:

```text
Find maximum among remaining salaries
```

That gives the second highest distinct salary.

---

# 18. Nth Highest Salary

For Oracle, an analytic function is a powerful solution.

### Question

Find the 3rd highest distinct salary.

### Query

```sql
SELECT SALARY
FROM (
    SELECT SALARY,
           DENSE_RANK() OVER (ORDER BY SALARY DESC) AS RN
    FROM EMPLOYEE
)
WHERE RN = 3;
```

### Explanation

Suppose salaries are:

```text
90000
80000
80000
70000
60000
```

`DENSE_RANK()` produces:

```text
SALARY | RN
------------
90000  | 1
80000  | 2
80000  | 2
70000  | 3
60000  | 4
```

Therefore:

```sql
WHERE RN = 3
```

returns:

```text
70000
```

### Important

Use:

```text
DENSE_RANK()
```

when you want **distinct salary ranking**.

---

# 19. Highest Salary in Each Department

This is another extremely common pattern.

### Question

Find the highest-paid employee in each department.

### Query

```sql
SELECT EMPLOYEE_NAME,
       DEPTNO,
       SALARY
FROM (
    SELECT EMPLOYEE_NAME,
           DEPTNO,
           SALARY,
           DENSE_RANK() OVER (
               PARTITION BY DEPTNO
               ORDER BY SALARY DESC
           ) AS RN
    FROM EMPLOYEE
)
WHERE RN = 1;
```

### Key idea

```text
PARTITION BY DEPTNO
        ↓
Create ranking separately for each department

ORDER BY SALARY DESC
        ↓
Highest salary gets rank 1

RN = 1
        ↓
Return highest-paid employee(s)
```

This pattern is much more powerful than simply using `MAX(SALARY)` because it can return the **employee details** too.

---

# 20. Find Duplicate Records

Suppose duplicate employee names exist.

### Question

Find employee names occurring more than once.

### Query

```sql
SELECT EMPLOYEE_NAME,
       COUNT(*) AS CNT
FROM EMPLOYEE
GROUP BY EMPLOYEE_NAME
HAVING COUNT(*) > 1;
```

### Logic

```text
GROUP BY name
      ↓
COUNT each name
      ↓
HAVING COUNT > 1
      ↓
Duplicates
```

### Memory

> Duplicate detection = `GROUP BY + COUNT + HAVING`

---

# 21. Find Employees Without Managers

### Question

Display employees who do not have a manager.

### Query

```sql
SELECT EMPLOYEE_NAME
FROM EMPLOYEE
WHERE MANAGER_ID IS NULL;
```

### Output

```text
EMPLOYEE_NAME
-------------
KING
```

This is a good example of combining a business requirement with NULL handling.

---

# 22. Employees Joined in a Particular Year

### Question

Find employees who joined in 2024.

### Query

```sql
SELECT EMPLOYEE_NAME,
       JOIN_DATE
FROM EMPLOYEE
WHERE EXTRACT(YEAR FROM JOIN_DATE) = 2024;
```

### Explanation

`EXTRACT(YEAR FROM JOIN_DATE)` obtains the year.

---

# 23. Department-Wise Salary Report

### Question

Display department number, employee count, minimum salary, maximum salary, and average salary.

### Query

```sql
SELECT DEPTNO,
       COUNT(*) AS EMPLOYEE_COUNT,
       MIN(SALARY) AS MIN_SALARY,
       MAX(SALARY) AS MAX_SALARY,
       AVG(SALARY) AS AVG_SALARY
FROM EMPLOYEE
GROUP BY DEPTNO;
```

### Why this is important

One query combines:

```text
GROUP BY
COUNT
MIN
MAX
AVG
```

This is the type of query you should be comfortable constructing during an interview.

---

# 24. Employees Working in Multiple Departments

This depends on the database design.

If an employee can have multiple department records:

### Question

Find employees associated with more than one department.

### Query

```sql
SELECT EMPLOYEE_ID,
       COUNT(DISTINCT DEPTNO) AS DEPT_COUNT
FROM EMPLOYEE_DEPARTMENT
GROUP BY EMPLOYEE_ID
HAVING COUNT(DISTINCT DEPTNO) > 1;
```

### Logic

```text
GROUP BY employee
       ↓
COUNT different departments
       ↓
Keep count > 1
```

---

# 25. Understand Set Operators

Important Oracle SQL set operators include:

```text
UNION
UNION ALL
INTERSECT
MINUS
```

### Example

Suppose:

```text
TABLE_A
-------
10
20
30
```

and:

```text
TABLE_B
-------
20
30
40
```

### UNION

```sql
SELECT ID FROM TABLE_A
UNION
SELECT ID FROM TABLE_B;
```

Output:

```text
10
20
30
40
```

Duplicates are removed.

---

### UNION ALL

```sql
SELECT ID FROM TABLE_A
UNION ALL
SELECT ID FROM TABLE_B;
```

Duplicates are retained.

---

### INTERSECT

```sql
SELECT ID FROM TABLE_A
INTERSECT
SELECT ID FROM TABLE_B;
```

Output:

```text
20
30
```

---

### MINUS

```sql
SELECT ID FROM TABLE_A
MINUS
SELECT ID FROM TABLE_B;
```

Output:

```text
10
```

---

# 26. Don't Repeat the Same Query Unnecessarily

If the same SQL logic is being written repeatedly, ask:

> "Can I make this simpler?"

For example, avoid unnecessarily repeating the same subquery when a join or analytic function provides a clearer solution.

The recommended practices explicitly include avoiding redundant queries and reducing unnecessary operations. 

---

# 27. Write Optimized Joins

A join should have a meaningful relationship.

### Question

Display employee and department information.

### Query

```sql
SELECT E.EMPLOYEE_NAME,
       D.DEPARTMENT_NAME
FROM EMPLOYEE E
JOIN DEPARTMENT D
    ON E.DEPTNO = D.DEPTNO;
```

### Important

Always understand:

```text
Which table?
       ↓
Which relationship?
       ↓
Which columns connect them?
       ↓
Which join type?
```

Do not randomly join tables.

---

# 28. Use Constraints Properly

Database design is not only about queries.

Important constraints include:

```text
PRIMARY KEY
FOREIGN KEY
UNIQUE
NOT NULL
CHECK
```

### Question

Create an employee table with a primary key and salary validation.

### Query

```sql
CREATE TABLE EMPLOYEE (
    EMPLOYEE_ID NUMBER PRIMARY KEY,
    EMPLOYEE_NAME VARCHAR2(50) NOT NULL,
    SALARY NUMBER CHECK (SALARY > 0)
);
```

### Why?

The database itself protects the data.

```text
PRIMARY KEY → uniquely identifies row
NOT NULL    → value required
CHECK       → validates condition
FOREIGN KEY → maintains relationship
UNIQUE      → prevents duplicate values
```

Proper constraints and suitable datatypes are part of good database practice. 

---

# 29. Normalize Tables Before Optimizing Them

A good database design generally starts with normalization.

Remember:

```text
1NF  → Atomic
2NF  → Partial
3NF  → Transitive
BCNF → Super Key
4NF  → Multivalued
5NF  → Join
```

Do not introduce redundancy simply because a query is difficult.

First ask:

> "Is the database design correct?"

Then consider performance requirements.

---

# 30. Test Queries Before Deployment

Never assume:

> "The query looks correct, so it must be correct."

Execute it and check:

* Returned rows
* Number of rows
* NULL values
* Sorting
* Aggregate calculations
* Grouping
* Join results

These are specifically recommended as things to analyze when executing SQL. 

---

# 31. Understand Query Execution Thinking

When solving difficult queries, don't look at the entire query at once.

Take this:

```sql
SELECT DEPTNO,
       AVG(SALARY)
FROM EMPLOYEE
WHERE SALARY > 30000
GROUP BY DEPTNO
HAVING AVG(SALARY) > 50000
ORDER BY AVG(SALARY) DESC;
```

Think:

```text
EMPLOYEE
   ↓
WHERE SALARY > 30000
   ↓
Remaining rows
   ↓
GROUP BY DEPTNO
   ↓
Department groups
   ↓
AVG(SALARY)
   ↓
HAVING AVG(SALARY) > 50000
   ↓
ORDER BY
   ↓
Final result
```

This mental model makes difficult SQL much easier.

---

# 32. The Most Important Technique: Break Difficult Queries into Steps

When an interviewer gives you a difficult query, **do not immediately write one huge statement**.

Suppose they ask:

> Find employees who earn more than the average salary of their department and display their department name.

Break it down.

### Step 1

What do I need?

```text
Employee
Department
Salary
```

### Step 2

How are the tables related?

```text
EMPLOYEE.DEPTNO
        ↓
DEPARTMENT.DEPTNO
```

### Step 3

What is the condition?

```text
Employee salary >
average salary of employee's department
```

### Step 4

Can I calculate department average?

```sql
SELECT DEPTNO,
       AVG(SALARY)
FROM EMPLOYEE
GROUP BY DEPTNO;
```

### Step 5

Can I compare each employee with that value?

Now use a correlated subquery:

```sql
SELECT E.EMPLOYEE_NAME,
       D.DEPARTMENT_NAME,
       E.SALARY
FROM EMPLOYEE E
JOIN DEPARTMENT D
    ON E.DEPTNO = D.DEPTNO
WHERE E.SALARY > (
    SELECT AVG(E2.SALARY)
    FROM EMPLOYEE E2
    WHERE E2.DEPTNO = E.DEPTNO
);
```

### This is the key skill

> **Break → Solve → Combine → Test**

---

# 33. A Universal Difficult-Query Solving Method

Whenever you receive an unfamiliar SQL problem, follow these **10 steps**.

```text
1. Read the question carefully
          ↓
2. Identify required output columns
          ↓
3. Identify required tables
          ↓
4. Identify relationships
          ↓
5. Identify filtering conditions
          ↓
6. Identify grouping requirement
          ↓
7. Identify aggregate requirement
          ↓
8. Decide JOIN / SUBQUERY / ANALYTIC FUNCTION
          ↓
9. Write the query step-by-step
          ↓
10. Test and verify the output
```

This is much better than memorizing hundreds of queries.

---

# 34. Keyword Recognition Technique

When you see certain words in an interview question, immediately think of the corresponding SQL technique.

| Question wording            | Think                    |
| --------------------------- | ------------------------ |
| all records                 | `SELECT`                 |
| only these columns          | column list              |
| unique                      | `DISTINCT`               |
| greater than                | `>`                      |
| between                     | `BETWEEN`                |
| one of these                | `IN`                     |
| starts with                 | `LIKE 'A%'`              |
| contains                    | `LIKE '%A%'`             |
| missing                     | `IS NULL`                |
| sorted                      | `ORDER BY`               |
| highest                     | `MAX()` / ranking        |
| lowest                      | `MIN()` / ranking        |
| average                     | `AVG()`                  |
| total                       | `SUM()`                  |
| count                       | `COUNT()`                |
| department-wise             | `GROUP BY`               |
| group condition             | `HAVING`                 |
| from another table          | `JOIN`                   |
| same table                  | `SELF JOIN`              |
| above average               | `SUBQUERY`               |
| Nth highest                 | `DENSE_RANK()` / ranking |
| duplicate                   | `GROUP BY + HAVING`      |
| hierarchy                   | `SELF JOIN`              |
| independent multiple values | 4NF/MVD                  |
| different result sets       | Set operators            |

---

# 35. How to Debug a Wrong Query

Suppose your query returns the wrong result.

Don't randomly change everything.

Use this process:

```text
Wrong Result
     ↓
Check FROM
     ↓
Check JOIN condition
     ↓
Check WHERE
     ↓
Check GROUP BY
     ↓
Check HAVING
     ↓
Check aggregate function
     ↓
Check NULL
     ↓
Check duplicates
     ↓
Check ORDER BY
```

### Example

Suppose you expected:

```text
5 departments
```

but received:

```text
20 rows
```

Immediately ask:

> "Did my JOIN create duplicate combinations?"

This is one of the most important real-world SQL debugging skills.

---

# 36. How to Modify Existing Queries

After writing a query, deliberately change:

* Column names
* Conditions
* Operators
* Aggregate functions
* Join conditions
* Sorting order

This is an effective way to develop SQL logic instead of merely copying examples. 

### Example

Original:

```sql
SELECT EMPLOYEE_NAME,
       SALARY
FROM EMPLOYEE
WHERE SALARY > 30000;
```

Change:

```sql
WHERE SALARY > 50000
```

Then:

```sql
ORDER BY SALARY DESC;
```

Then:

```sql
SELECT DEPTNO,
       AVG(SALARY)
FROM EMPLOYEE
GROUP BY DEPTNO;
```

The objective is to understand **what changes when the query changes**.

---

# 37. Build Small Databases for Practice

Instead of practicing only isolated queries, create small databases.

Useful practice domains include:

```text
Student Management
Library Management
Hospital Management
Employee Management
Banking
Online Shopping
School Management
E-Commerce
Payroll
HR Management
Inventory Management
Online Examination
```

Database exercises should include tables, constraints, relationships, sample data, and meaningful queries. 

---

# 38. Think in Terms of Business Questions

A real SQL developer doesn't receive:

> "Use GROUP BY."

They receive:

> "Management wants to know how many employees work in each department."

You translate:

```text
business question
       ↓
required information
       ↓
tables
       ↓
relationships
       ↓
SQL technique
       ↓
query
       ↓
result
```

For example:

### Business question

> How many employees are working in each department?

### SQL thinking

```text
Employee count
      +
Department
      ↓
GROUP BY department
      +
COUNT(*)
```

### Query

```sql
SELECT DEPTNO,
       COUNT(*) AS EMPLOYEE_COUNT
FROM EMPLOYEE
GROUP BY DEPTNO;
```

This is the mindset interviewers want.

---

# 39. SQL Interview Representation

When the interviewer asks:

> "Write a query to find employees earning above average salary."

Don't silently type the query.

Say:

> "First, I need to calculate the average salary. Since that produces a value that I need to compare against each employee's salary, I can use a scalar subquery. Then I will filter employees using the `WHERE` clause."

Then write:

```sql
SELECT EMPLOYEE_NAME,
       SALARY
FROM EMPLOYEE
WHERE SALARY > (
    SELECT AVG(SALARY)
    FROM EMPLOYEE
);
```

Then explain:

> "The inner query calculates the average salary. The outer query returns employees whose salary is greater than that average."

This shows **reasoning**, not memorization.

---

# 40. If You Don't Know the Query in an Interview

Never panic.

Say:

> "I'll break the requirement into smaller parts first."

Then identify:

```text
What should I display?
From which table?
Do I need another table?
Do I need filtering?
Do I need grouping?
Do I need an aggregate?
Do I need a subquery?
Do I need ranking?
```

Even if you don't immediately know the final query, demonstrating the reasoning process is much better than guessing.

---

# 41. Common Mistakes to Avoid

### Mistake 1

Using:

```sql
WHERE COUNT(*) > 2
```

instead of:

```sql
HAVING COUNT(*) > 2
```

---

### Mistake 2

Using:

```sql
= NULL
```

instead of:

```sql
IS NULL
```

---

### Mistake 3

Forgetting the join condition.

---

### Mistake 4

Using `INNER JOIN` when the requirement says **all employees**, including unmatched ones.

---

### Mistake 5

Using `MAX(SALARY)` when the question actually asks:

> "Who earns the highest salary?"

`MAX()` gives the salary, not necessarily the employee row.

---

### Mistake 6

Using `ROWNUM` without understanding its behavior.

---

### Mistake 7

Not considering duplicate salaries when solving Nth-highest-salary problems.

---

### Mistake 8

Writing a huge query without first breaking the problem into steps.

---

### Mistake 9

Not checking NULL values.

---

### Mistake 10

Copying a query without understanding why it works.

The recommended learning approach is explicitly to attempt problems independently before checking examples. 

---

# 42. SQL Learning Cycle

Do not follow:

```text
Read → Memorize → Forget
```

Use:

```text
        LEARN
          ↓
      UNDERSTAND
          ↓
        WRITE
          ↓
       EXECUTE
          ↓
       ANALYZE
          ↓
       MODIFY
          ↓
       PRACTICE
          ↓
        REVISE
          ↓
      INTERVIEW
```

A similar practical cycle is recommended: learn theory, study syntax, execute scripts, analyze results, experiment, practice independently, revise, and apply. 

---

# 43. Your Oracle SQL Interview Checklist

Before saying **"I know Oracle SQL"**, you should be able to explain and practice:

### Fundamentals

* Database
* DBMS
* RDBMS
* Oracle Database
* SQL
* SQL categories
* Oracle SQL syntax

### Data

* Datatypes
* NULL
* Literals
* DUAL

### Retrieval

* `SELECT`
* `DISTINCT`
* Column aliases
* Calculations

### Filtering

* `WHERE`
* Comparison operators
* Logical operators
* `IN`
* `BETWEEN`
* `LIKE`
* `IS NULL`

### Sorting

* `ORDER BY`
* ASC
* DESC

### Functions

* Character functions
* Number functions
* Date functions
* Conversion functions
* Single-row functions
* Aggregate/multirow functions

### Grouping

* `GROUP BY`
* `HAVING`

### Subqueries

* Single-row
* Multiple-row
* Nested
* Correlated
* Above-average problems

### Joins

* INNER
* LEFT
* RIGHT
* FULL
* SELF
* CROSS
* Multiple-table joins

### Commands

```text
DDL
DML
TCL
DCL
DQL
```

### Database design

* Tables
* Constraints
* Keys
* Relationships
* ER diagrams
* Normalization

### Database objects

* Views
* Indexes
* Procedures
* Triggers
* Sequences
* Synonyms

The covered interview areas include fundamentals, datatypes, constraints, SELECT, filtering, sorting, grouping, functions, subqueries, joins, SQL command categories, database objects, normalization, and ER diagrams. 

---

# 44. Final Difficult-Query Formula ⭐

Whenever you see a difficult SQL question, remember:

```text
QUESTION
   ↓
What is the OUTPUT?
   ↓
Which TABLES?
   ↓
What is the RELATIONSHIP?
   ↓
Which ROWS?
   ↓
Which GROUPS?
   ↓
Which CALCULATION?
   ↓
JOIN / SUBQUERY / ANALYTIC?
   ↓
WRITE SMALL QUERY
   ↓
COMBINE
   ↓
TEST
   ↓
EXPLAIN
```

---

# 45. Final Oracle SQL Memory Map

```text
                         ORACLE SQL
                              │
       ┌──────────────────────┼──────────────────────┐
       │                      │                      │
   FUNDAMENTALS           QUERYING               DATABASE
       │                      │                      │
   Datatypes               SELECT                Tables
   NULL                    WHERE                 Constraints
   DUAL                    ORDER BY              Keys
   Operators               GROUP BY              Relationships
   Aliases                 HAVING                ER Diagram
                              │                   Normalization
                    ┌─────────┴─────────┐
                    │                   │
                 FUNCTIONS          ADVANCED
                    │                   │
              Character              Joins
              Number                Subqueries
              Date                  Correlated
              Conversion            Set Operators
              Aggregate             Analytic
                                        │
                                        ▼
                                  INTERVIEW
                                        │
                         ┌──────────────┼──────────────┐
                         │              │              │
                     Concepts        Queries        Scenarios
                         │              │              │
                         ▼              ▼              ▼
                     Explain         Write          Solve
                         │              │              │
                         └──────────────┼──────────────┘
                                        ▼
                                   OPTIMIZATION
                                        │
                         ┌──────────────┼──────────────┐
                         │              │              │
                      Readable       Minimal       Efficient
                        SQL           Code          Operations
```

---

# 46. The Most Important 20 Best Practices — Final Revision

|  # | Best Practice                | Remember                           |
| -: | ---------------------------- | ---------------------------------- |
|  1 | Meaningful table names       | Understand the table immediately   |
|  2 | Descriptive column names     | Avoid `C1`, `C2`                   |
|  3 | Readable SQL                 | Format properly                    |
|  4 | Consistent formatting        | Same style everywhere              |
|  5 | Uppercase SQL keywords       | `SELECT`, `FROM`, `WHERE`          |
|  6 | Avoid unnecessary `SELECT *` | Select required columns            |
|  7 | Use comments appropriately   | Explain non-obvious logic          |
|  8 | Choose suitable datatypes    | Correct datatype for data          |
|  9 | Define constraints           | Protect data integrity             |
| 10 | Normalize tables             | Reduce redundancy                  |
| 11 | Write proper joins           | Correct relationship               |
| 12 | Avoid redundant queries      | Reduce unnecessary work            |
| 13 | Test before deployment       | Never assume                       |
| 14 | Keep scripts organized       | Modular SQL                        |
| 15 | Understand NULL              | `IS NULL`, not `= NULL`            |
| 16 | Understand clause purpose    | Don't memorize blindly             |
| 17 | Analyze output               | Rows, NULLs, groups, sorting       |
| 18 | Solve independently          | Attempt before checking            |
| 19 | Practice difficult patterns  | Salary, duplicates, ranking, joins |
| 20 | Optimize and explain         | Readable + efficient + explainable |

The core best-practice list emphasizes meaningful naming, readable/consistent SQL, uppercase keywords, avoiding unnecessary `SELECT *`, comments, appropriate datatypes, constraints, normalization, optimized joins, avoiding redundant queries, testing, modular scripts, and consistent naming. 

---

# 47. The One Rule I Want You to Remember

**Don't become a SQL person who remembers 500 queries.**

Become a SQL person who can see:

> **Question → Logic → SQL**

For example:

```text
"Second highest salary"
        ↓
Remove highest
        ↓
Find maximum
        ↓
MAX + SUBQUERY
```

```text
"Department-wise employee count"
        ↓
Create department groups
        ↓
Count rows
        ↓
GROUP BY + COUNT
```

```text
"Employee earning above average"
        ↓
Calculate average
        ↓
Compare every employee
        ↓
SUBQUERY
```

```text
"Highest-paid employee in each department"
        ↓
Rank within department
        ↓
Take rank 1
        ↓
DENSE_RANK + PARTITION BY
```

```text
"Employee and manager"
        ↓
Same table represents two roles
        ↓
SELF JOIN
```

```text
"Find duplicates"
        ↓
Group identical values
        ↓
Count
        ↓
HAVING COUNT(*) > 1
```

That **problem-solving mindset** is what will allow you to solve queries you have never seen before.

And the strongest preparation method is:

> **Learn → Understand → Write → Execute → Analyze → Modify → Solve independently → Revise → Explain in interview.** 
