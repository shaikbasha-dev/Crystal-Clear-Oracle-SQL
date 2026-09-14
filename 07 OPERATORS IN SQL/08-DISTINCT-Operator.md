# 08-DISTINCT-Operator

## 1. What is DISTINCT?

`DISTINCT` is used with `SELECT` when we want to display **unique values** and avoid displaying duplicate values in the result.

Think of it like this:

```text
EMP table

DEPT_ID
-------
21
22
22
23
23
24
24
24
25
110
110
```

If we simply select `DEPT_ID`, Oracle can show:

```text
21
22
22
23
23
24
24
24
25
110
110
```

But if we use `DISTINCT`:

```sql
SELECT DISTINCT dept_id
FROM emp;
```

Oracle displays each department ID only once:

```text
21
22
23
24
25
110
```

So remember:

> **DISTINCT = show the value only once.**

---

# 2. Why do we need DISTINCT?

Suppose 10 employees work in department `22`.

Without `DISTINCT`:

```text
22
22
22
22
22
22
22
22
22
22
```

But if our question is:

> "What are the different departments in which employees work?"

We don't need `22` ten times.

We need:

```text
22
```

Therefore, we use `DISTINCT`.

---

# 3. Syntax

```sql
SELECT DISTINCT column_name
FROM table_name;
```

### Example

```sql
SELECT DISTINCT dept_id
FROM emp;
```

Meaning:

```text
SELECT
   ↓
I want to display

DISTINCT
   ↓
Don't repeat duplicate values

dept_id
   ↓
Display department IDs

FROM emp
   ↓
Take them from EMP table
```

---

# 4. DISTINCT does NOT delete data

This is very important.

Suppose `EMP` contains:

```text
22
22
22
23
23
```

When we execute:

```sql
SELECT DISTINCT dept_id
FROM emp;
```

the output may be:

```text
22
23
```

But the actual `EMP` table is still:

```text
22
22
22
23
23
```

### Therefore:

```text
DISTINCT
   ↓
Changes the SELECT result
   ↓
Does NOT delete duplicate records
```

---

# 5. Question 1

### Question

**Write a query to display unique department id from employee table.** 

### Answer / Query

```sql
SELECT DISTINCT dept_id
FROM emp;
```

### Output shown in the notes

```text
DEPT_ID
-------
22
25
21
24
110
23
```



---

## Step-by-step explanation

The query is:

```sql
SELECT DISTINCT dept_id
FROM emp;
```

### Step 1 — `FROM emp`

Oracle takes the data from the `EMP` table.

### Step 2 — `dept_id`

We are interested in the department ID.

### Step 3 — `DISTINCT`

Oracle checks the department IDs and removes duplicate values **from the result**.

### Step 4 — Display

Only unique department IDs are displayed.

```text
EMP
 ↓
DEPT_ID
 ↓
Find duplicates
 ↓
Remove duplicates from result
 ↓
Display unique DEPT_ID
```

---

# 6. Question 2

### Question

**Display the distinct salaries from employees.** 

### Answer / Query

```sql
SELECT DISTINCT salary
FROM emp;
```

### Output shown in the notes

```text
SALARY
------
28500
12000
29500
55000
...
```

Only distinct salary values are displayed. 

---

## Step-by-step explanation

The query is:

```sql
SELECT DISTINCT salary
FROM emp;
```

### Step 1 — `FROM emp`

Take salary information from the `EMP` table.

### Step 2 — `salary`

Select the salary column.

### Step 3 — `DISTINCT`

If multiple employees have the same salary, don't repeat that salary in the result.

### Step 4 — Display

Display each salary value only once.

---

# 7. Simple Example

Suppose the `EMP` table has:

```text
SALARY
------
34000
45000
55000
34000
18000
55000
18000
```

### Without DISTINCT

```sql
SELECT salary
FROM emp;
```

Result:

```text
34000
45000
55000
34000
18000
55000
18000
```

### With DISTINCT

```sql
SELECT DISTINCT salary
FROM emp;
```

Result:

```text
34000
45000
55000
18000
```

The duplicate values are removed **only from the displayed result**.

---

# 8. DISTINCT with Different Columns

The concept is exactly the same.

### Department IDs

```sql
SELECT DISTINCT dept_id
FROM emp;
```

Means:

> Show every different department ID only once.

### Salaries

```sql
SELECT DISTINCT salary
FROM emp;
```

Means:

> Show every different salary only once.

---

# 9. Common Confusion

### Confusion 1: Does DISTINCT remove duplicate rows from the table?

**No.**

It only removes duplicate values from the query result.

---

### Confusion 2: Is DISTINCT a function?

No.

Here, `DISTINCT` is used as a **keyword/operator in the SELECT statement**.

```sql
SELECT DISTINCT salary
FROM emp;
```

---

### Confusion 3: Where do we write DISTINCT?

Immediately after `SELECT`.

```sql
SELECT DISTINCT column_name
FROM table_name;
```

Not:

```sql
SELECT column_name DISTINCT
FROM table_name;
```

---

# 10. DISTINCT vs Normal SELECT

| Normal SELECT              | SELECT with DISTINCT                |
| -------------------------- | ----------------------------------- |
| Can display duplicates     | Removes duplicates from result      |
| `SELECT dept_id FROM emp;` | `SELECT DISTINCT dept_id FROM emp;` |
| Shows repeated values      | Shows unique values                 |
| Does not remove table data | Does not remove table data          |

---

# 11. Important Point for Your Revision

Suppose:

```text
EMP table contains:

DEPT_ID
-------
21
22
22
23
23
23
24
```

Then:

```sql
SELECT dept_id
FROM emp;
```

can produce:

```text
21
22
22
23
23
23
24
```

But:

```sql
SELECT DISTINCT dept_id
FROM emp;
```

produces:

```text
21
22
23
24
```

### Remember:

> **DISTINCT removes repetition from the result, not from the table.**

---

# 12. Interview Questions

### Q1. What is DISTINCT?

`DISTINCT` is used with `SELECT` to display unique values by eliminating duplicate values from the query result.

### Q2. What is the syntax of DISTINCT?

```sql
SELECT DISTINCT column_name
FROM table_name;
```

### Q3. Does DISTINCT delete duplicate records from the table?

No. It only removes duplicate values from the result displayed by the `SELECT` statement.

### Q4. Where is DISTINCT placed in a SELECT statement?

Immediately after `SELECT`.

### Q5. Why do we use DISTINCT?

To display only unique values when duplicate values are present.

---

# 13. Complete Questions + Answers from this DISTINCT Section

### Question 1

**Write a query to display unique department id from employee table.**

```sql
SELECT DISTINCT dept_id
FROM emp;
```

### Question 2

**Display the distinct salaries from employees.**

```sql
SELECT DISTINCT salary
FROM emp;
```

These are the **DISTINCT queries in this Operators section of the PDF**. 

> **Important:** The PDF later contains queries such as `COUNT(DISTINCT salary)`, `MIN(DISTINCT salary)`, `MAX(DISTINCT salary)`, `SUM(DISTINCT salary)`, and `AVG(DISTINCT salary)`. Those belong to the later **Multirow Functions** section, so they should be covered when we reach that section rather than mixed into this `DISTINCT-Operator` folder. 

## Quick Memory

```text
DISTINCT
   ↓
SELECT
   ↓
Remove duplicate values
   ↓
Show unique values
```

### Main syntax

```sql
SELECT DISTINCT column_name
FROM table_name;
```

### Questions from this folder

```text
1. Display unique department IDs
2. Display distinct salaries
```

### Answers

```sql
SELECT DISTINCT dept_id
FROM emp;

SELECT DISTINCT salary
FROM emp;
```
