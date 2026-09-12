# 02-Types-of-Operators

## Types of Operators in SQL

SQL operators are divided into **two types**:

```text
OPERATORS IN SQL
       │
       ├── 1. Symbolic Operators
       │
       └── 2. Keywords As Operators
```

---

## 1. Symbolic Operators

These operators are represented using **symbols**.

The symbolic operators covered here are:

### Arithmetic Operators

```text
+
-
*
/
```

They are used for mathematical calculations.

Example:

```sql
SELECT salary + 1000
FROM emp;
```

Here `+` is an arithmetic operator.

---

### Relational Operators

```text
=
>
<
>=
<=
!=
<>
```

They are used to **compare values**.

Example:

```sql
SELECT *
FROM emp
WHERE salary > 30000;
```

Here `>` compares the employee's salary with `30000`.

---

### Concatenation Operator

```text
||
```

It is used to **combine values**, especially character values.

Example:

```sql
SELECT f_name || l_name
FROM emp;
```

Here `||` joins the first name and last name.

---

## 2. Keywords As Operators

Some operators are written using **SQL keywords** instead of symbols.

The keywords covered are:

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

These are used for different purposes such as filtering, checking ranges, checking lists, checking `NULL`, pattern matching, and combining conditions.

---

## Easy Classification

```text
                    OPERATORS
                        │
          ┌─────────────┴─────────────┐
          │                           │
   SYMBOLIC OPERATORS       KEYWORDS AS OPERATORS
          │                           │
    ┌─────┼─────┐              ┌──────┼─────────┐
    │     │     │              │      │         │
Arithmetic Relational     DISTINCT  BETWEEN    IN
    │        │             NOT BETWEEN          │
+ - * /   = > <            NOT IN              │
           >= <=           IS NULL             │
           != <>           IS NOT NULL         │
                  ||       LIKE                │
                           AND                 OR
```

## Remember

### Symbolic Operators

**Symbols →**

```text
+  -  *  /  =  >  <  >=  <=  !=  <>  ||
```

### Keywords As Operators

**Words →**

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

The important thing to remember is simply:

> **SQL Operators = Symbolic Operators + Keywords As Operators**.
