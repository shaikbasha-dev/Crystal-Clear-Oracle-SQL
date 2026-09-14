# 03-Arithmetic-Operators

## What are Arithmetic Operators?

**Arithmetic operators** are operators used to perform **mathematical calculations** on numeric values.

You already know these from normal mathematics:

```text
+    Addition
-    Subtraction
*    Multiplication
/    Division
```

Oracle SQL can use these operators with values stored in a table.

For example, if an employee's salary is:

```text
34000
```

Then:

```text
salary + 1000
```

means:

```text
34000 + 1000
       ↓
35000
```

---

# Arithmetic Operators in SQL

There are **4 arithmetic operators**:

| Operator | Meaning        | Simple example |
| -------- | -------------- | -------------- |
| `+`      | Addition       | `10 + 5 = 15`  |
| `-`      | Subtraction    | `10 - 5 = 5`   |
| `*`      | Multiplication | `10 * 5 = 50`  |
| `/`      | Division       | `10 / 5 = 2`   |

---

# 1. Addition `+`

The `+` operator is used to **add** values.

### Example

Suppose:

```text
salary = 34000
```

We want to increase the salary by `1000`.

```sql
SELECT salary + 1000
FROM emp;
```

Oracle performs:

```text
34000 + 1000
       ↓
35000
```

So the employee's displayed salary becomes `35000`.

---

## Query from the topic

To display employee ID, first name, last name and salary after increasing the salary by `1000`:

```sql
SELECT emp_id, f_name, l_name, salary + 1000
FROM emp;
```

### Understand the query

```text
SELECT
   emp_id          → employee ID
   f_name          → first name
   l_name          → last name
   salary + 1000   → increase salary by 1000

FROM emp
   ↓
take the data from EMP table
```

For example:

```text
Akash   Pandey   34000
```

becomes:

```text
Akash   Pandey   35000
```

---

# 2. Subtraction `-`

The `-` operator is used to **subtract** a value.

For example:

```text
34000 - 1000
       ↓
33000
```

### Query

```sql
SELECT emp_id, email, phone_number, salary - 1000
FROM emp;
```

This displays:

* Employee ID
* Email
* Phone number
* Salary after subtracting `1000`

---

# 3. Multiplication `*`

The `*` operator is used for **multiplication**.

For example:

```text
34000 * 2
       ↓
68000
```

We can also use multiplication inside a salary calculation.

For example:

```sql
SELECT emp_id, job_id, dept_id,
       salary + (salary * (10 / 100))
FROM emp;
```

### What is happening here?

Suppose:

```text
salary = 34000
```

First:

```text
10 / 100
   ↓
0.1
```

Then:

```text
34000 * 0.1
      ↓
3400
```

Then:

```text
34000 + 3400
       ↓
37400
```

So the query calculates the salary after a **10% increase**.

---

# 4. Division `/`

The `/` operator is used for **division**.

For example:

```text
34000 / 2
       ↓
17000
```

### Query

```sql
SELECT salary / 6
FROM emp;
```

This divides every employee's salary by `6`.

### Important correction

The notes describe this as a **half-yearly salary**, but mathematically:

```text
salary / 2 → half of salary
salary / 6 → one-sixth of salary
```

So if the salary represents an annual amount, `salary / 6` is **one-sixth**, not half-yearly.

---

# 5. Arithmetic Expression

We can use more than one arithmetic operator in the same expression.

For example:

```sql
SELECT emp_id, job_id, dept_id,
       salary - (salary * (20 / 100))
FROM emp;
```

This calculates salary after a **20% reduction**.

Suppose:

```text
salary = 34000
```

Then:

```text
20 / 100
   ↓
0.2
```

Then:

```text
34000 * 0.2
       ↓
6800
```

Then:

```text
34000 - 6800
       ↓
27200
```

So the displayed result is:

```text
27200
```

---

# 6. Why are Parentheses Used?

Look at:

```sql
salary + (salary * (10 / 100))
```

The parentheses tell Oracle which calculation belongs together.

Think of it like normal mathematics:

```text
salary + (salary × percentage)
```

First calculate the percentage amount:

```text
salary × percentage
```

Then add it to salary.

---

# 7. Arithmetic Operator Precedence

When several arithmetic operators appear in an expression, Oracle needs to know **which calculation should happen first**.

This is called **operator precedence**.

The notes show:

```text
Operator    Precedence
*           1
/           2
+           3
-           4
```

### Technical correction

The important Oracle rule is:

```text
* and / have the same precedence
+ and - have the same precedence
```

Operators with the same precedence are evaluated **from left to right**.

Parentheses can be used when we want to explicitly control the calculation order.

---

# 8. Very Simple Example

Consider:

```sql
SELECT 10 + 5 * 2
FROM dual;
```

Multiplication is performed before addition:

```text
5 * 2
 ↓
10

10 + 10
   ↓
20
```

Result:

```text
20
```

If we write:

```sql
SELECT (10 + 5) * 2
FROM dual;
```

Parentheses come first:

```text
10 + 5
  ↓
15

15 * 2
   ↓
30
```

Result:

```text
30
```

---

# 9. All Arithmetic Queries Together

### Increase salary by 1000

```sql
SELECT emp_id, f_name, l_name, salary + 1000
FROM emp;
```

### Decrease salary by 1000

```sql
SELECT emp_id, email, phone_number, salary - 1000
FROM emp;
```

### Increase salary by 10%

```sql
SELECT emp_id, job_id, dept_id,
       salary + (salary * (10 / 100))
FROM emp;
```

### Decrease salary by 20%

```sql
SELECT emp_id, job_id, dept_id,
       salary - (salary * (20 / 100))
FROM emp;
```

### Divide salary by 6

```sql
SELECT salary / 6
FROM emp;
```

---

# 10. Important Understanding

Arithmetic operators **do not change the actual salary stored in the table** when used like this:

```sql
SELECT salary + 1000
FROM emp;
```

They only calculate a value for the **query result**.

For example, if the table contains:

```text
SALARY
34000
```

and we execute:

```sql
SELECT salary + 1000
FROM emp;
```

the result displays:

```text
35000
```

but the stored salary remains:

```text
34000
```

---

# 11. Common Confusion

### `+` does not permanently increase salary

```sql
SELECT salary + 1000
FROM emp;
```

means:

> "Show me salary after adding 1000."

It does **not** mean:

> "Change the salary in the table."

---

### `*` means multiplication

```sql
salary * 10
```

means:

> salary multiplied by 10.

---

### `/` means division

```sql
salary / 6
```

means:

> salary divided by 6.

---

### Parentheses matter

```text
salary + salary * 10 / 100
```

and

```text
salary + (salary * (10 / 100))
```

use arithmetic precedence to determine the calculation order.

Using parentheses makes the intended calculation much easier to understand.

---

# 12. Memory Trick

Remember the four arithmetic operators as:

```text
+  → ADD
-  → REMOVE
*  → MULTIPLY
/  → DIVIDE
```

Or simply:

> **A S M D**

```text
A → Addition
S → Subtraction
M → Multiplication
D → Division
```

---

# Interview Understanding

### What are arithmetic operators in SQL?

> Arithmetic operators are used to perform mathematical calculations on numeric values in SQL. The main arithmetic operators are addition `+`, subtraction `-`, multiplication `*`, and division `/`.

### What is the use of `salary + 1000`?

> It calculates and displays the salary after adding 1000 to the existing salary. It does not permanently modify the stored salary.

### What is operator precedence?

> Operator precedence determines the order in which arithmetic operations are evaluated. In Oracle, multiplication and division have higher precedence than addition and subtraction, and operators of the same precedence are evaluated from left to right.
