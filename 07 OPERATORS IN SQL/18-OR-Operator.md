# 18-OR-Operator

## 1. What is the OR Operator?

The **OR operator** is used in SQL when we want to check **multiple conditions and accept a row if at least one condition is true**.

In simple words:

> **OR = ANY ONE condition can be TRUE.**

If one condition is true, the row can be selected.

---

## 2. Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1
OR condition2;
```

Here:

* `condition1` → first condition
* `OR` → connects the conditions
* `condition2` → second condition

### Easy way to remember

```text
Condition 1  OR  Condition 2
     ↓              ↓
   TRUE           FALSE
        ↓
      RESULT
```

At least **one condition must be TRUE**.

---

# 3. OR Operator — Query 1

### Question

**Write a query to display the grade from `J_GRADE` where grade is `A` or `HIGH_SAL` is greater than 80000.**

### Answer / Query

```sql
SELECT grade
FROM j_grade
WHERE grade = 'A'
OR high_sal > 80000;
```

### Explanation

The query checks two conditions:

```sql
grade = 'A'
```

**OR**

```sql
high_sal > 80000
```

A row is selected when **either one or both conditions are true**.

### Remember

```text
grade = 'A'       → TRUE  → selected
grade ≠ 'A'
BUT high_sal > 80000 → TRUE → selected
both FALSE         → not selected
```

---

# 4. OR Operator — Query 2

### Question

**Write a query to display the details of employees whose job_id is `ST_CLERK` or whose salary is less than 19000.**

### Answer / Query

```sql
SELECT *
FROM emp
WHERE job_id = 'ST_CLERK'
OR salary < 19000;
```

### Explanation

There are two conditions:

```sql
job_id = 'ST_CLERK'
```

**OR**

```sql
salary < 19000
```

An employee will be displayed if:

* their `JOB_ID` is `ST_CLERK`, **or**
* their salary is less than `19000`, **or**
* both conditions are true.

---

# 5. OR Truth Table

| Condition 1 | Condition 2 | OR Result |
| ----------- | ----------- | --------- |
| TRUE        | TRUE        | **TRUE**  |
| TRUE        | FALSE       | **TRUE**  |
| FALSE       | TRUE        | **TRUE**  |
| FALSE       | FALSE       | **FALSE** |

### Memory Trick

> **OR = At least ONE condition must be TRUE.**

---

# 6. AND vs OR

| AND                         | OR                                  |
| --------------------------- | ----------------------------------- |
| All conditions must be TRUE | At least one condition must be TRUE |
| More restrictive            | Less restrictive                    |
| `condition1 AND condition2` | `condition1 OR condition2`          |

### Easy memory

```text
AND → ALL
OR  → ANY ONE
```

---

# 7. Interview Questions

### Q1. What is the OR operator in SQL?

**Answer:**
The `OR` operator is used to combine multiple conditions. A row is selected when at least one of the conditions is true.

### Q2. If the first condition is FALSE and the second condition is TRUE, what is the result of OR?

**Answer:**
The result is **TRUE**.

### Q3. If both conditions are FALSE?

**Answer:**
The result is **FALSE**.

### Q4. What is the easiest way to remember OR?

**Answer:**

> **OR = At least one condition should be TRUE.**
