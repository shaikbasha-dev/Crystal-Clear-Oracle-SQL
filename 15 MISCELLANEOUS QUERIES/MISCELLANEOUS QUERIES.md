# 15-Miscellaneous-Queries

This section contains **all six queries** under `MISCELLANEOUS QUERIES`. Each one is presented as:

**Question → Understand the question → Query → Query explanation → Output**

---

## 1. Replace `p` with `&` in `f_name`

### Question

**Get `f_name` from the `emp` table after replacing `'p'` with `'&'`.**

### Understand the question

We need to:

1. Take the `f_name` column from `emp`.
2. Find the character `p`.
3. Replace `p` with `&`.
4. Display the modified names.

The function used for this is `REPLACE()`.

### Query

```sql
SELECT REPLACE(f_name, 'p', '&')
FROM emp;
```



### Query explanation

```text
REPLACE(f_name, 'p', '&')
       │       │    │
       │       │    └── New character
       │       └────── Character to find
       └────────────── Column
```

For every value in `f_name`, Oracle searches for lowercase `p` and replaces it with `&`.

### Output

The output shown is:

| REPLACE(F_NAME,'P','&') |
| ----------------------- |
| Akash                   |
| Prabhakaran             |
| DEEP                    |
| Ashwin                  |
| John                    |
| Shashi                  |
| Andy                    |
| Daniel                  |
| Adam                    |
| Meghana                 |
| Madavan                 |
| Braven                  |
| Mamatha                 |
| Savitha                 |
| Mrudul                  |
| Pankaj                  |
| Janardhan               |
| Sardhar                 |
| Jinnath                 |



> **Important:** `REPLACE()` is performing character replacement in the returned value; it does not modify the original `emp` table.

---

# 2. Calculate different percentages of salary

### Question

**Select 35% of salary from Pandey, 10% of salary for Ganeshan, and 15% of salary for other employees from the `emp` table.**

### Understand the question

We have three conditions:

```text
If employee = Pandey
       ↓
35% of salary

If employee = Ganeshan
       ↓
10% of salary

For all other employees
       ↓
15% of salary
```

This requires a `CASE` expression.

### Query

The query shown is:

```sql
SELECT CASE
       WHEN l_name = 'Pandey' THEN salary * 0.35
       WHEN l_name = 'ganeshan' THEN salary * 0.35
       ELSE salary * 0.15
       END
FROM emp;
```



### ⚠️ Important correction

There is a mismatch between the **question and the query**.

The question asks:

```text
Pandey    → 35%
Ganeshan  → 10%
Others    → 15%
```

But the query actually contains:

```sql
WHEN l_name = 'ganeshan' THEN salary * 0.35
```

That means the query calculates **35% for Ganeshan**, not 10%.

### Correct query for the stated question

```sql
SELECT CASE
       WHEN l_name = 'Pandey' THEN salary * 0.35
       WHEN l_name = 'ganeshan' THEN salary * 0.10
       ELSE salary * 0.15
       END
FROM emp;
```

### Query explanation

```text
CASE
  ↓
Check conditions one by one

Pandey?
  ↓ YES → salary × 0.35

Ganeshan?
  ↓ YES → salary × 0.10

Otherwise
  ↓
salary × 0.15
```

### Output

The displayed output in the document is:

| CASE result |
| ----------: |
|       11900 |
|        6750 |
|        8250 |
|        5400 |
|        2700 |
|       12750 |
|        4275 |
|        1800 |
|        7950 |
|        7950 |
|        3750 |
|        6825 |
|        6900 |
|        1800 |
|        2925 |
|        5925 |
|        4425 |
|        4425 |
|        1425 |



**Interview point:** Always check the conditions and calculations carefully. Here the stated requirement and the written query do not match.

---

# 3. Select the top 2 salaries

### Question

**Select TOP 2 salaries from the `emp` table.**

### Understand the question

We need to find the **two highest salary values**.

To do that:

1. Sort salaries from highest to lowest.
2. Take the first two rows.

```text
All salaries
     ↓
ORDER BY salary DESC
     ↓
Highest → Lowest
     ↓
Take first 2
```

### Query

```sql
SELECT salary
FROM (
    SELECT salary
    FROM emp
    ORDER BY salary DESC
)
WHERE ROWNUM < 3;
```



### Query explanation

### Inner query

```sql
SELECT salary
FROM emp
ORDER BY salary DESC
```

This sorts salaries in **descending order**.

Example:

```text
85000
55000
...
```

### Outer query

```sql
WHERE ROWNUM < 3
```

This means:

```text
ROWNUM = 1 → take
ROWNUM = 2 → take
ROWNUM = 3 → don't take
```

Therefore, only two salaries are returned.

### Output

| SALARY |
| -----: |
|  85000 |
|  55000 |



### Interview point

This is an important Oracle SQL pattern for retrieving the **top N records** using `ORDER BY` inside a subquery and `ROWNUM` outside.

---

# 4. Find the 2nd highest salary

### Question

**Select the 2nd highest salary from the `emp` table.**

### Understand the question

We need the salary that comes **second when distinct salaries are arranged from highest to lowest**.

For example:

```text
Highest salary
     ↓
2nd highest salary ← Required
     ↓
3rd highest
     ↓
...
```

### Query

```sql
SELECT MIN(salary)
FROM (
    SELECT DISTINCT salary
    FROM emp
    ORDER BY salary DESC
)
WHERE ROWNUM <= 2;
```



### Query explanation

### Step 1 — Get distinct salaries

```sql
SELECT DISTINCT salary
FROM emp
```

Duplicate salary values are removed.

### Step 2 — Sort descending

```sql
ORDER BY salary DESC
```

Highest salary comes first.

### Step 3 — Take first two

```sql
WHERE ROWNUM <= 2
```

Only the two highest distinct salaries remain.

For example:

```text
85000
55000
```

### Step 4 — Find the minimum of those two

```sql
SELECT MIN(salary)
```

The minimum of:

```text
85000
55000
```

is:

```text
55000
```

Therefore, `55000` is the 2nd highest salary.

### Output

| MIN(SALARY) |
| ----------: |
|       55000 |



### Interview point

`DISTINCT` is important here because we are looking for the **2nd highest distinct salary**.

---

# 5. Fetch common records only once

### Question

**If there are two tables `employee1` and `employee2`, and both have common records, how can we fetch all the records but common records only once?**

### Understand the question

We have:

```text
employee1
   ↓
Records

employee2
   ↓
Records
```

Some records may appear in **both tables**.

We need:

* All records from both tables.
* If a record exists in both tables, display it **only once**.

The operator used is `UNION`.

### Query

```sql
SELECT *
FROM employee1

UNION

SELECT *
FROM employee2;
```



### Query explanation

```text
employee1
    +
employee2
    ↓
  UNION
    ↓
Combined result
    ↓
Duplicate records removed
```

### Output

The exact rows depend on the contents of `employee1` and `employee2`.

The result contains:

* All records from `employee1`
* All records from `employee2`
* Common/duplicate records appear only once.

### Important

`UNION` removes duplicate rows from the combined result.

---

# 6. Fetch only common records

### Question

**How can we fetch only common records from two tables `employee1` and `employee2`?**

### Understand the question

Here we do **not** want all records.

We want only records that exist in:

```text
employee1
      AND
employee2
```

The operator used is `INTERSECT`.

### Query

```sql
SELECT *
FROM employee1

INTERSECT

SELECT *
FROM employee2;
```



### Query explanation

```text
employee1
    ∩
employee2
    ↓
Only common records
```

Suppose:

```text
employee1       employee2
--------        ---------
A               B
B               C
C               D
```

Then:

```text
INTERSECT
   ↓
B
C
```

### Output

The exact rows depend on the data present in both tables.

The result contains **only records common to both `employee1` and `employee2`**.

---

# 7. Fetch records from EMPLOYEE1 that are not in EMPLOYEE2

### Question

**How can we retrieve all records of `employee1` that should not be present in `employee2`?**

### Understand the question

We want:

```text
employee1
   MINUS
employee2
```

In simple words:

> Give me records that exist in `employee1` but do **not** exist in `employee2`.

### Query

```sql
SELECT *
FROM employee1

MINUS

SELECT *
FROM employee2;
```



### Query explanation

Imagine:

```text
employee1       employee2
--------        ---------
A               B
B               C
C               D
E
```

`MINUS` performs:

```text
employee1
   -
employee2
   ↓
A
E
```

So records present only in `employee1` are returned.

### Output

The exact rows depend on the contents of the two tables.

The result contains:

> **Records present in `employee1` but absent from `employee2`.**

---

# Quick Interview Revision

| Question type                             | Operator / Technique                         |
| ----------------------------------------- | -------------------------------------------- |
| Replace one character with another        | `REPLACE()`                                  |
| Different calculation based on conditions | `CASE`                                       |
| Top 2 salaries                            | `ORDER BY DESC` + `ROWNUM`                   |
| 2nd highest salary                        | `DISTINCT` + `ORDER BY` + `ROWNUM` + `MIN()` |
| Combine two tables and remove duplicates  | `UNION`                                      |
| Get only common records                   | `INTERSECT`                                  |
| Records in first table but not second     | `MINUS`                                      |

### Most important patterns to remember

```text
UNION
employee1 + employee2
→ All records, duplicates removed


INTERSECT
employee1 ∩ employee2
→ Only common records


MINUS
employee1 - employee2
→ Records in employee1 but not employee2
```

All seven question/query items under **MISCELLANEOUS QUERIES** are included above. 
