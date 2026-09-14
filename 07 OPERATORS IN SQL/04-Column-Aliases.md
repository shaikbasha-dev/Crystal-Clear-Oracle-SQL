# 04-Column-Aliases

## What is a Column Alias?

A **column alias** is another name that we give to a column **only for displaying the result of a query**.

Think of it like giving a **nickname** to a column.

For example, suppose the table has:

```text
F_NAME
```

But when we display the result, we want the heading to be:

```text
FIRST NAME
```

We can give `F_NAME` an alias.

The basic idea is:

```text
Original column name
        ↓
     F_NAME
        ↓
    Alias name
        ↓
   FIRST NAME
```

A column alias is simply **another name given to a column in SQL**. 

---

# Why do we need Column Aliases?

Sometimes the original column name is:

* difficult to understand
* too short
* not user-friendly
* an expression instead of a normal column name

For example:

```sql
SELECT salary + 1000
FROM emp;
```

Oracle may display the heading as:

```text
SALARY+1000
```

That heading is not very readable.

We can give it a better name:

```sql
SELECT salary + 1000 AS new_salary
FROM emp;
```

Now the result heading becomes:

```text
NEW_SALARY
```

So the alias makes the **output easier to understand**.

---

# Syntax

There are two ways to specify a column alias.

## Method 1 — Using `AS`

```sql
columnname AS aliasname
```

Example:

```sql
SELECT salary AS new_salary
FROM emp;
```

Here:

```text
salary
  ↓
original column

AS
  ↓
tells Oracle that a new display name is coming

new_salary
  ↓
alias
```

---

## Method 2 — Using Double Quotes

The other syntax is:

```sql
columnname "alias name"
```

Example:

```sql
SELECT salary "New Salary"
FROM emp;
```

Here the alias is:

```text
New Salary
```

Notice that there is a **space** between `New` and `Salary`.

The material gives both forms:

```sql
columnname AS aliasname
```

and

```sql
columnname "alias name"
```



---

# Simple Example

Suppose the `EMP` table contains:

```text
F_NAME
Akash
Prabhakaran
DEEP
```

If we write:

```sql
SELECT f_name
FROM emp;
```

The heading is:

```text
F_NAME
```

Now:

```sql
SELECT f_name AS first_name
FROM emp;
```

The heading becomes:

```text
FIRST_NAME
```

The actual values are still:

```text
Akash
Prabhakaran
DEEP
```

Only the **heading displayed by the query** has changed.

---

# Alias Does NOT Change the Table

This is very important.

Suppose the actual table has:

```text
F_NAME
```

and we execute:

```sql
SELECT f_name AS first_name
FROM emp;
```

We have **not renamed `F_NAME` in the table**.

We have only told Oracle:

> "While showing this query result, display this column with the name `FIRST_NAME`."

The alias does not get reflected in the actual table stored on the computer. 

Think of it like this:

```text
ACTUAL TABLE
     ↓
   F_NAME
     │
     │  SELECT ... AS ...
     ↓
QUERY OUTPUT
     ↓
 FIRST_NAME
```

The table still has:

```text
F_NAME
```

---

# Alias with an Expression

Aliases become especially useful when we perform calculations.

For example:

```sql
SELECT salary + 1000
FROM emp;
```

The result heading may be:

```text
SALARY+1000
```

We can make it easier to understand:

```sql
SELECT salary + 1000 AS increased_salary
FROM emp;
```

Now:

```text
INCREASED_SALARY
```

is displayed as the heading.

---

# Alias with a Space

Suppose we want the heading to appear as:

```text
Employee Salary
```

There is a space between the two words.

We can use double quotes:

```sql
SELECT salary "Employee Salary"
FROM emp;
```

Result heading:

```text
Employee Salary
```

The double quotes allow us to write the alias in the desired form.

---

# `AS` vs Double Quotes

| Syntax        | Example                | Purpose                                    |
| ------------- | ---------------------- | ------------------------------------------ |
| `AS`          | `salary AS new_salary` | Gives a simple alias                       |
| Double quotes | `salary "New Salary"`  | Allows a display name such as `New Salary` |

Remember:

```sql
salary AS new_salary
```

and:

```sql
salary "New Salary"
```

are giving a **new name to the column in the query result**.

---

# Very Important Difference

Don't confuse:

### Column Alias

```sql
SELECT salary AS new_salary
FROM emp;
```

with changing the actual column name.

A column alias:

```text
Changes the displayed heading
        ↓
Does NOT change the actual table
```

So:

```text
Alias = temporary display name
```

---

# Easy Analogy

Imagine your friend's actual name is:

```text
Mohammed
```

You call him:

```text
Mahi
```

His official name has not changed.

`Mahi` is just another name you use to refer to him.

Similarly:

```text
Actual column → salary
Alias         → new_salary
```

The actual column remains:

```text
salary
```

The query result can display:

```text
new_salary
```

---

# Common Confusion

### Is an alias a new column?

**No.**

```sql
SELECT salary AS new_salary
FROM emp;
```

This does not create another column in `EMP`.

It only changes the heading of the result.

---

### Does alias permanently rename the column?

**No.**

The actual column remains unchanged.

---

### Why use an alias?

To give a column a **more understandable or meaningful name in the query output**.

---

# Memory Trick

Remember:

> **Alias = Another Name**

```text
Column
  ↓
Another name
  ↓
Alias
```

And:

> **Alias changes the display name, not the actual table column name.**

---

# Interview Questions

### 1. What is a column alias?

> A column alias is another name given to a column in SQL for displaying a meaningful name in the query result.

### 2. What is the syntax for a column alias?

```sql
columnname AS aliasname
```

or

```sql
columnname "alias name"
```

### 3. Does a column alias change the actual column name?

> No. A column alias only changes the name displayed in the query result. It does not change the actual column name in the table.

### 4. Why are aliases useful?

> They make column headings easier to understand, especially when working with expressions or when the original column name is not descriptive.
