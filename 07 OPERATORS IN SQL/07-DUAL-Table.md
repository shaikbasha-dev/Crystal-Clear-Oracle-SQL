# 07-DUAL-Table

## 1. What is DUAL?

**DUAL** is a special table available by default in Oracle.

It contains:

* **1 row**
* **1 column**
* Column name: `DUMMY`
* Data type: `VARCHAR2(1)`
* Value: `X`

```text
DUAL
------
DUMMY
------
X
```

The main purpose of DUAL is to allow us to use a `SELECT` statement when we want to calculate or display a **constant value/expression** and we do not need data from an actual table. 

---

# 2. Structure of DUAL

### Question 1

**Write a query to describe the DUAL table.**

```sql
DESC DUAL;
```

The important structure is:

```text
DUMMY    VARCHAR2(1)
```

The DUAL table has one `VARCHAR2(1)` column named `DUMMY`. 

---

### Question 2

**Write a query to display all the data from the DUAL table.**

```sql
SELECT * FROM DUAL;
```

**Output:**

```text
DUMMY
-----
X
```

DUAL contains one row, and the value of `DUMMY` is `X`. 

---

# 3. Why is DUAL used?

### Question 3

**Why is selecting from the DUAL table useful?**

DUAL is useful for computing a **constant expression** with the `SELECT` statement.

For example:

```sql
SELECT 111 + 222
FROM DUAL;
```

Since DUAL has only **one row**, the result is returned only once.

If we select the same expression from a table containing 20 rows, the expression can be returned 20 times. 

---

# 4. DUAL with Concatenation

These are the DUAL-related questions and queries in this section.

---

### Question 4

**Write a query to concatenate 111 and 222 and display it as full number.**

```sql
SELECT 111||222 AS "full number"
FROM DUAL;
```

**Output:**

```text
Full Number
-----------
111222
```

### Explanation

`||` is the **concatenation operator**.

It joins:

```text
111
+
222
```

and produces:

```text
111222
```

The alias `"full number"` is used for the output column. 

---

### Question 5

**Write a query to concatenate Bond and 7777 and display it as movie character.**

```sql
SELECT 'Bond'||7777 AS "movie character"
FROM DUAL;
```

**Output:**

```text
Movie Character
---------------
Bond7777
```

### Explanation

The concatenation operator joins:

```text
'Bond'
+
7777
```

Result:

```text
Bond7777
```



---

### Question 6

**Write a query to concatenate bond with null and display the result.**

```sql
SELECT 'bond'||NULL AS "result"
FROM DUAL;
```

**Output:**

```text
Result
------
bond
```

### Explanation

Here:

```sql
'bond' || NULL
```

produces:

```text
bond
```

The `NULL` does not add any visible characters to the concatenated result. 

---

### Question 7

**Write a query to concatenate Sachin and Tendulkar and display it as full name.**

```sql
SELECT 'Sachin '||' Tendulkar' AS "full name"
FROM DUAL;
```

**Output:**

```text
Full Name
---------
Sachin Tendulkar
```

### Explanation

Notice the spaces:

```sql
'Sachin '
```

has a space after `Sachin`.

And:

```sql
' Tendulkar'
```

has a space before `Tendulkar`.

Therefore the output is:

```text
Sachin Tendulkar
```



---

# 5. DUAL vs an Actual Table

### Example using DUAL

```sql
SELECT 'Sachin '||' Tendulkar'
FROM DUAL;
```

The values are directly written in the query.

So we don't need `EMP`, `DEPT`, etc.

### Example using EMP

```sql
SELECT f_name||' '||l_name
FROM EMP;
```

Here `f_name` and `l_name` come from the `EMP` table, so we use `EMP`.

---

# 6. Very Important Rule

Remember:

```text
DUAL
 ↓
1 row
 ↓
1 column
 ↓
DUMMY
 ↓
VARCHAR2(1)
 ↓
X
```

Because DUAL has only **one row**, a constant expression selected from DUAL is normally displayed **once**. 

---

# 7. Common Confusion

### ❌ Wrong understanding

> DUAL is required whenever we use `||`.

No.

### ✅ Correct understanding

`||` can be used with any appropriate table or expression.

For example:

```sql
SELECT f_name||' '||l_name
FROM EMP;
```

No DUAL is required because the data comes from `EMP`.

DUAL is used when we need to execute a `SELECT` expression without retrieving business data from another table.

---

# 8. Interview Questions

### Q1. What is DUAL?

DUAL is a special one-row, one-column table available by default in Oracle.

### Q2. What is the column name of DUAL?

`DUMMY`

### Q3. What is the data type of DUMMY?

`VARCHAR2(1)`

### Q4. What value is stored in DUMMY?

`X`

### Q5. How many rows does DUAL contain?

One row.

### Q6. Why do we use DUAL?

To evaluate or display constant expressions using `SELECT` when actual table data is not required.

### Q7. Why does a constant expression from DUAL return only one result?

Because DUAL contains only one row.

---

# 9. Complete DUAL Query Set

For revision, here are **all the questions with their corresponding queries together**:

### 1. Write a query to describe the DUAL table.

```sql
DESC DUAL;
```

### 2. Write a query to display all the data from the DUAL table.

```sql
SELECT * FROM DUAL;
```

### 3. Write a query to concatenate 111 and 222 and display it as full number.

```sql
SELECT 111||222 AS "full number"
FROM DUAL;
```

### 4. Write a query to concatenate Bond and 7777 and display it as movie character.

```sql
SELECT 'Bond'||7777 AS "movie character"
FROM DUAL;
```

### 5. Write a query to concatenate bond with null and display the result.

```sql
SELECT 'bond'||NULL AS "result"
FROM DUAL;
```

### 6. Write a query to concatenate Sachin and Tendulkar and display it as full name.

```sql
SELECT 'Sachin '||' Tendulkar' AS "full name"
FROM DUAL;
```

**Core memory point:**

> **DUAL = one-row, one-column Oracle table used mainly when we need `SELECT` to evaluate/display a constant or expression without requiring actual table data.**
