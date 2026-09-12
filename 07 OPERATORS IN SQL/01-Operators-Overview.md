# 01-Operators-Overview

## What are Operators in SQL?

**Operators** are symbols or keywords used in SQL to perform an operation on data or to check a condition.

In simple words:

> **Operators tell Oracle what operation to perform on the data.**

For example:

```sql
SELECT salary + 1000
FROM emp;
```

Here:

* `salary` → data from the `EMP` table
* `+` → operator
* `1000` → value

Oracle takes the salary and adds `1000` to it.

---

## Why do we need Operators?

Operators are needed when we want SQL to **work with data**.

For example, we may want to:

* Add something to salary
* Subtract something from salary
* Compare two values
* Join two pieces of text
* Check whether a value falls within a range
* Check whether a value is present in a list
* Check for `NULL`
* Search for a particular pattern
* Combine multiple conditions

Without operators, SQL would have very limited ability to perform these operations.

---

## Simple Example

Suppose an employee has:

```text
SALARY = 34000
```

If we write:

```sql
salary + 1000
```

Oracle performs:

```text
34000 + 1000
     ↓
35000
```

Here `+` is the **operator**.

---

## Two Types of Operators

SQL operators are divided into **two types**:

### 1. Symbolic Operators

These operators are represented using symbols.

Examples:

```text
+
-
*
/
=
>
<
>=
<=
!=
<>
||
```

The `+`, `-`, `*`, `/`, etc. are symbols, so they are called **Symbolic Operators**.

---

### 2. Keywords As Operators

Some operators are represented using SQL keywords.

Examples:

```text
DISTINCT
BETWEEN
NOT BETWEEN
IN
NOT IN
IS NULL
IS NOT NULL
LIKE
AND
OR
```

These are called **Keywords As Operators**. 

---

## Easy Understanding

Think of an operator as an **instruction** given to Oracle.

For example:

```text
salary + 1000
       ↑
    "Add this"
```

```text
salary > 30000
       ↑
    "Compare this"
```

```text
f_name = 'Akash'
       ↑
    "Check whether equal"
```

So:

> **Operator = symbol or keyword that tells Oracle what to do or what condition to check.**

---

## Quick Classification

```text
                 OPERATORS IN SQL
                        |
             ┌──────────┴──────────┐
             |                     |
       Symbolic Operators    Keywords As Operators
             |                     |
       +  -  *  /              DISTINCT
       =  >  <                 BETWEEN
       >= <=                   IN
       != <>                   NOT IN
       ||                      LIKE
                               AND
                               OR
                               ...
```

---

## Important Point

At this stage, don't try to memorize every operator.

Just remember the main classification:

> **SQL Operators → Symbolic Operators + Keywords As Operators**

The individual operators will be understood separately, along with their queries.
