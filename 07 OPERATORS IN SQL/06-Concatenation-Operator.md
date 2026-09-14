# 06-Concatenation-Operator

## What is Concatenation?

**Concatenation** means **joining two or more values together**.

In very simple words:

> **Concatenation = Joining**

In Oracle SQL, the concatenation operator is:

```text
||
```

So whenever you see:

```text
||
```

think:

> **"Join these values."**

---

## Simple Example

Suppose we have:

```text
F_NAME = Akash
L_NAME = Pandey
```

We want:

```text
Akash Pandey
```

We can join them using `||`.

```sql
SELECT f_name || ' ' || l_name
FROM emp;
```

Oracle does this:

```text
Akash
   +
space
   +
Pandey
   ↓
Akash Pandey
```

---

# Concatenation Operator

The operator is:

```text
||
```

It is called the **Concatenation Operator**.

---

# 1. Concatenate First Name and Last Name

### Question

Write a query to concatenate `f_name` and `l_name` from the `EMP` table and display it as **full name**.

### Query

```sql
SELECT f_name || ' ' || l_name AS "full name"
FROM emp;
```

### Understand it step by step

Suppose one row contains:

```text
f_name = Akash
l_name = Pandey
```

The expression is:

```text
f_name || ' ' || l_name
```

First:

```text
Akash || ' '
       ↓
Akash_
```

Then:

```text
Akash_ || Pandey
         ↓
Akash Pandey
```

The space comes from:

```sql
' '
```

The result heading is:

```text
full name
```

because we used:

```sql
AS "full name"
```

The query and resulting full names are given in the material. 

---

# Why do we use `' '`?

Look at these two queries.

### Without space

```sql
SELECT f_name || l_name
FROM emp;
```

Result:

```text
AkashPandey
```

### With space

```sql
SELECT f_name || ' ' || l_name
FROM emp;
```

Result:

```text
Akash Pandey
```

So:

```text
' '
```

means:

> **one blank space**

---

# 2. Concatenate Two Literal Values

We can also concatenate values that are written directly in the query.

### Question

Write a query to concatenate `Sachin` and `Tendulkar` and display it as **full name**.

### Query

```sql
SELECT 'Sachin ' || ' Tendulkar' AS "full name"
FROM dual;
```

Result:

```text
Full Name
----------------
Sachin Tendulkar
```

Here:

```text
'Sachin '
     ||
' Tendulkar'
     ↓
Sachin Tendulkar
```

The `||` operator joins the two character values. 

---

# Why is `DUAL` used here?

There is no employee table needed for this calculation.

We simply want Oracle to calculate:

```text
'Sachin ' || ' Tendulkar'
```

For this type of constant expression, the material uses the Oracle `DUAL` table.

`DUAL` is a special one-row, one-column table available in Oracle. Its column is `DUMMY`, and its value is `X`. 

We will study `DUAL` separately.

For now, remember:

> **When we need Oracle to evaluate a simple expression without needing data from another table, `DUAL` is used.**

---

# 3. Concatenate Numbers

The concatenation operator can also join numeric values.

### Query

```sql
SELECT 111 || 222 AS "full number"
FROM dual;
```

Oracle joins:

```text
111
 ||
222
 ↓
111222
```

Result:

```text
111222
```

The important idea is that this is **concatenation**, not mathematical addition.



---

# `||` vs `+`

This is very important.

### `+`

Means:

> **Add**

```text
111 + 222
   ↓
333
```

### `||`

Means:

> **Join**

```text
111 || 222
    ↓
111222
```

So:

```text
+   → Mathematics
||  → Joining
```

---

# 4. Concatenate Text and Number

### Query

```sql
SELECT 'Bond' || 7777 AS "movie character"
FROM dual;
```

Oracle joins:

```text
Bond
 ||
7777
 ↓
Bond7777
```

Result:

```text
Movie Character
----------------
Bond7777
```



---

# 5. Concatenate with NULL

This is an important example.

### Query

```sql
SELECT 'bond' || NULL AS "result"
FROM dual;
```

Result:

```text
bond
```

Why?

Because in this concatenation example, concatenating `NULL` does not add visible characters to the result.

So:

```text
bond || NULL
      ↓
bond
```

The material shows exactly this result. 

---

# 6. Concatenate Column Values with Text

Now we can make a complete sentence using values from the `EMP` table.

### Required output

```text
Akash works in department 21
Prabhakaran works in department 22
Andy works in department 22
...
```

### Query

```sql
SELECT f_name || ' works in department ' || dept_id AS "Salary Details"
FROM emp;
```

Let's understand one row.

Suppose:

```text
f_name  = Akash
dept_id = 21
```

The expression becomes:

```text
Akash
   ||
' works in department '
   ||
21
```

Result:

```text
Akash works in department 21
```

The same operation happens for every employee row. 

---

# How `||` Works

Think of `||` as **glue**.

```text
'Hello'
   ||
' '
   ||
'World'
```

The `||` joins everything:

```text
Hello World
```

Another example:

```text
f_name
   ||
' works in department '
   ||
dept_id
```

becomes:

```text
Akash works in department 21
```

---

# All Concatenation Queries

### Query 1

```sql
SELECT f_name || ' ' || l_name AS "full name"
FROM emp;
```

### Query 2

```sql
SELECT 'Sachin ' || ' Tendulkar' AS "full name"
FROM dual;
```

### Query 3

```sql
SELECT 111 || 222 AS "full number"
FROM dual;
```

### Query 4

```sql
SELECT 'Bond' || 7777 AS "movie character"
FROM dual;
```

### Query 5

```sql
SELECT 'bond' || NULL AS "result"
FROM dual;
```

### Query 6

```sql
SELECT f_name || ' works in department ' || dept_id AS "Salary Details"
FROM emp;
```

---

# Common Confusion

## `||` does not mean addition

Wrong thinking:

```text
111 || 222 = 333
```

No.

It means joining:

```text
111 || 222
     ↓
111222
```

---

## Spaces must be supplied when needed

This:

```sql
SELECT f_name || l_name
FROM emp;
```

produces:

```text
AkashPandey
```

This:

```sql
SELECT f_name || ' ' || l_name
FROM emp;
```

produces:

```text
Akash Pandey
```

The space is explicitly provided using:

```text
' '
```

---

# Memory Trick

Whenever you see:

```text
||
```

say:

> **JOIN**

So:

```text
A || B
```

means:

```text
A JOIN B
```

---

# Interview Questions

### What is concatenation?

> Concatenation means joining two or more values together.

### Which operator is used for concatenation in Oracle SQL?

```text
||
```

### What is the difference between `+` and `||`?

> `+` is used for arithmetic addition, whereas `||` is used to concatenate or join values.

### How do you concatenate first name and last name with a space?

```sql
SELECT f_name || ' ' || l_name
FROM emp;
```

### Does concatenating `NULL` with `'bond'` produce `NULL` here?

No. The expression:

```sql
'bond' || NULL
```

produces:

```text
bond
```

in the example used here.
