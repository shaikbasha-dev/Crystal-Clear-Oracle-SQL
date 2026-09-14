# 20-Operator-Precedence

## 1. What is Operator Precedence?

**Operator precedence** means the **order in which Oracle evaluates operators** when more than one operator is present in an expression.

In simple words:

> When a SQL expression contains multiple operators, Oracle follows a particular order to decide **which operation should happen first**.

---

# 2. Arithmetic Operator Precedence

The notes show the following precedence order:

| Operator | Precedence |
| -------- | ---------: |
| `*`      |          1 |
| `/`      |          2 |
| `+`      |          3 |
| `-`      |          4 |

So, according to the order shown:

```text
*  → first
/  → next
+  → next
-  → last
```

### Important correction

The **precedence numbering shown above is not technically accurate for Oracle SQL**.

In Oracle:

```text
* and / → same precedence
+ and - → same precedence
```

When operators have the same precedence, evaluation proceeds **from left to right**.

So do not memorize the numbers `1, 2, 3, 4` as Oracle's actual precedence levels.

---

# 3. AND and OR Precedence

The notes give:

| Operator | Precedence |
| -------- | ---------: |
| `AND`    |          1 |
| `OR`     |          2 |

This means:

> **AND is evaluated before OR.**

So:

```sql
condition1 OR condition2 AND condition3
```

is understood as:

```sql
condition1 OR (condition2 AND condition3)
```

not:

```sql
(condition1 OR condition2) AND condition3
```

---

# 4. Why Parentheses Are Important

Parentheses allow us to explicitly tell Oracle **which conditions should be grouped together**.

For example:

```sql
(job_id = 'AD_PRES' OR job_id = 'SA_REP')
AND salary > 25000
```

Here the parentheses clearly group the `OR` conditions first.

The meaning is:

```text
AD_PRES OR SA_REP
        ↓
     one group
        ↓
AND salary > 25000
```

---

# 5. Query from the Notes

### Question

**Write a query to display the details of all employees who are presidents or sales representatives but they must earn more than 25000.**

### Answer / Query

```sql id="x0u4v6"
SELECT *
FROM emp
WHERE ((job_id = 'AD_PRES' OR job_id = 'SA_REP')
       AND salary > 25000);
```

### Step-by-step explanation

First, this part:

```sql
(job_id = 'AD_PRES' OR job_id = 'SA_REP')
```

means:

> The employee must be either a president or a sales representative.

Then:

```sql
AND salary > 25000
```

adds another requirement:

> The employee must earn more than `25000`.

So the complete meaning is:

```text
(AD_PRES OR SA_REP)
          AND
    salary > 25000
```

Both parts must be satisfied.

---

# 6. AND vs OR Precedence

Remember:

```text
AND → evaluated first
OR  → evaluated after AND
```

### Example

```sql
A OR B AND C
```

is treated as:

```sql
A OR (B AND C)
```

### If you want a different order

Use parentheses:

```sql
(A OR B) AND C
```

Therefore:

> **When AND and OR are combined, use parentheses whenever you want to make the intended logic clear.**

---

# 7. Easy Memory Trick

Remember:

```text
Arithmetic:
* / → before + -

Logical:
AND → before OR
```

And the safest rule:

> **When confused about AND-OR evaluation, use parentheses.**

---

# 8. Interview Questions

### Q1. What is operator precedence?

**Answer:**
Operator precedence determines the order in which operators are evaluated when multiple operators are present in an SQL expression.

### Q2. Which has higher precedence, AND or OR?

**Answer:**
`AND` has higher precedence than `OR`.

### Q3. How can we control the evaluation order?

**Answer:**
By using **parentheses `()`**.

### Q4. How is this evaluated?

```sql
A OR B AND C
```

**Answer:**

```sql
A OR (B AND C)
```

because `AND` has higher precedence than `OR`.

### Q5. What is the safest way to write a complex AND-OR condition?

**Answer:**
Use parentheses to explicitly group the conditions and make the intended logic clear.
