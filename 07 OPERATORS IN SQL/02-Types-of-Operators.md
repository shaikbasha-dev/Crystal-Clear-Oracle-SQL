# 02-Types-of-Operators

Let's understand this **from absolute zero**.

Imagine you are giving instructions to Oracle.

For example:

```sql
salary + 1000
```

You are telling Oracle:

> "Take the salary and add 1000."

Here, `+` is an **operator**.

SQL operators are divided into **two main types**:

```text
OPERATORS
   │
   ├── 1. Symbolic Operators
   │
   └── 2. Keywords As Operators
```

---

## 1. Symbolic Operators

### What does "symbolic" mean?

**Symbolic** simply means the operator is written using a **symbol**.

For example:

```text
+
-
*
/
>
<
=
||
```

These are symbols, so they are called **Symbolic Operators**.

The symbolic operators in this topic are:

### A. Arithmetic Operators

```text
+
-
*
/
```

These are used for calculations.

Think about normal mathematics:

```text
10 + 5
10 - 5
10 * 5
10 / 5
```

The same idea is used in SQL.

Example:

```sql
SELECT salary + 1000
FROM emp;
```

Here:

```text
salary → value
+      → operator
1000   → value
```

---

### B. Relational Operators

These are used when we want to **compare values**.

They are:

```text
=
>
<
>=
<=
!=
<>
```

For example:

```sql
SELECT *
FROM emp
WHERE salary > 30000;
```

This means:

> "Give me employees whose salary is greater than 30000."

Oracle compares the values and gives the matching rows.

---

### C. Concatenation Operator

The concatenation operator is:

```text
||
```

It is used to **join values together**.

For example:

```sql
SELECT f_name || l_name
FROM emp;
```

Suppose:

```text
f_name = Akash
l_name = Pandey
```

Then:

```text
Akash || Pandey
       ↓
AkashPandey
```

If we want a space:

```sql
SELECT f_name || ' ' || l_name
FROM emp;
```

Result:

```text
Akash Pandey
```

---

# 2. Keywords As Operators

Now comes the second type.

Some operators are not symbols.

They are written using **words/keywords**.

For example:

```sql
BETWEEN
```

or:

```sql
IN
```

or:

```sql
LIKE
```

These are called **Keywords As Operators**.

The operators covered are:

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

---

## Why are they called Keywords As Operators?

Because these are **SQL keywords that perform an operator-like operation**.

For example:

```sql
SELECT *
FROM emp
WHERE salary BETWEEN 10000 AND 30000;
```

Here:

```text
BETWEEN
```

helps Oracle check whether the salary falls within a particular range.

Similarly:

```sql
SELECT *
FROM emp
WHERE dept_id IN (21, 22, 23);
```

Here:

```text
IN
```

helps Oracle check whether the department ID is one of the given values.

---

# Very Simple Difference

Think like this:

### Symbolic Operators

Oracle sees a **symbol**:

```text
+  -  *  /  =  >  <  ||
```

### Keywords As Operators

Oracle sees a **keyword**:

```text
BETWEEN
IN
LIKE
AND
OR
...
```

So:

```text
             OPERATORS
                 |
        ┌────────┴────────┐
        |                 |
     SYMBOLS           KEYWORDS
        |                 |
     + - * /          BETWEEN
     = > <            IN
     >= <=            NOT IN
     != <>            LIKE
     ||               AND
                      OR
                      ...
```

---

# One Important Point

Don't confuse **operator type** with **individual operator**.

For example:

```text
Symbolic Operators
       ↓
Arithmetic Operators
       ↓
+
-
*
/
```

And:

```text
Keywords As Operators
       ↓
BETWEEN
IN
LIKE
AND
OR
...
```

We will study each individual operator separately.

---

# Easy Memory Trick

Remember:

> **Symbolic = Symbols**

```text
+  -  *  /  =  >  <  ||
```

> **Keywords As Operators = Words**

```text
BETWEEN
IN
LIKE
AND
OR
...
```

### Final picture

```text
                    OPERATORS IN SQL
                           |
              ┌────────────┴────────────┐
              |                         |
       SYMBOLIC OPERATORS       KEYWORDS AS OPERATORS
              |                         |
       ┌──────┼──────┐          DISTINCT
       |      |      |          BETWEEN
   Arithmetic Relational        NOT BETWEEN
       |      |                  IN
   + - * /  = > <                 NOT IN
            >= <=                IS NULL
            != <>                IS NOT NULL
            ||                   LIKE
                                 AND
                                 OR
```

This is the complete **types/classification** part.
