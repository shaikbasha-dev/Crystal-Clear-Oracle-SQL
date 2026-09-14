# 19-AND-OR-Combination

When **AND** and **OR** are used together in the same SQL query, we call it an **AND-OR combination**.

The important point is that **parentheses `()`** help us clearly control which condition should be evaluated together.

---

## 1. Simple Understanding

Suppose we have:

```sql
condition1 OR condition2
```

and then we want:

```sql
(condition1 OR condition2) AND condition3
```

This means:

> First satisfy **either condition1 or condition2**, and then also satisfy **condition3**.

So:

```text
        OR
       /  \
 Condition1 Condition2
       \    /
        AND
         |
    Condition3
```

---

# 2. AND-OR Combination — Query 1

### Question

**Write a query to display the details of employees whose `JOB_ID` is `AD_PRES` or `SA_REP`, or whose salary is greater than 35000.**

### Answer / Query

```sql
SELECT *
FROM emp
WHERE (job_id = 'AD_PRES'
       OR job_id = 'SA_REP'
       OR salary > 35000);
```

### Explanation

Inside the parentheses, there are three conditions connected by `OR`:

```sql
job_id = 'AD_PRES'
OR job_id = 'SA_REP'
OR salary > 35000
```

Therefore, an employee is selected if **at least one** of these is true:

1. `JOB_ID` is `AD_PRES`
2. `JOB_ID` is `SA_REP`
3. `SALARY` is greater than `35000`

The parentheses make the complete `OR` group clear.

---

# 3. AND-OR Combination — Query 2

### Question

**Write a query to display the details of employees whose `JOB_ID` is `AD_PRES` or `SA_REP`, and whose salary is greater than 25000.**

### Answer / Query

```sql
SELECT *
FROM emp
WHERE ((job_id = 'AD_PRES'
        OR job_id = 'SA_REP')
       AND salary > 25000);
```

### Explanation

Here we have both `OR` and `AND`.

First, this part is evaluated:

```sql
job_id = 'AD_PRES'
OR job_id = 'SA_REP'
```

The employee must have either:

```text
AD_PRES
     OR
SA_REP
```

Then the `AND` condition is applied:

```sql
salary > 25000
```

So the employee must satisfy:

```text
(AD_PRES OR SA_REP)
          AND
      salary > 25000
```

### In simple words

> The employee must have **either AD_PRES or SA_REP**, **AND** their salary must be greater than 25000.

---

# 4. Difference Between the Two Queries

### Query 1

```sql
WHERE (job_id = 'AD_PRES'
       OR job_id = 'SA_REP'
       OR salary > 35000);
```

Meaning:

> Any **one** of the three conditions can be true.

### Query 2

```sql
WHERE ((job_id = 'AD_PRES'
        OR job_id = 'SA_REP')
       AND salary > 25000);
```

Meaning:

> `JOB_ID` must be either `AD_PRES` or `SA_REP`, **and additionally** salary must be greater than `25000`.

---

## 5. Why Parentheses Are Important

Consider:

```sql
(job_id = 'AD_PRES' OR job_id = 'SA_REP')
AND salary > 25000
```

The parentheses clearly tell us:

> First consider the two `JOB_ID` choices together, then apply the salary condition.

### Memory Trick

```text
() → Group conditions
OR → Any one
AND → All required conditions
```

So remember:

> **Parentheses + OR + AND = carefully control the condition combination.**

---

## 6. Interview Questions

### Q1. Can AND and OR be used together in SQL?

**Answer:**
Yes. `AND` and `OR` can be combined in a `WHERE` clause to create multiple conditions.

### Q2. Why are parentheses used with AND and OR?

**Answer:**
Parentheses are used to group conditions and make the intended evaluation clear.

### Q3. What does this mean?

```sql
(job_id = 'AD_PRES' OR job_id = 'SA_REP')
AND salary > 25000
```

**Answer:**
The employee must have either `AD_PRES` or `SA_REP`, and the salary must be greater than `25000`.

### Q4. What should we remember about AND-OR combination?

**Answer:**

> **OR gives choices; AND adds requirements; parentheses group the choices/conditions.**
