# Alphanumeric Data Types in Oracle SQL

**Alphanumeric data types** are used to store data containing **alphabets, numbers, and special symbols**.

According to your notes, there are **two alphanumeric data types**:

1. `CHAR(size)`
2. `VARCHAR2(size)` 

---

# 1. CHAR(size)

## What is `CHAR`?

`CHAR` is an alphanumeric data type used to store:

* Alphabets
* Numbers
* Special symbols

### Syntax

```sql
column_name CHAR(size)
```

### Example

```sql
Name CHAR(10)
```

This means the `Name` column is defined using `CHAR` with a size of 10.

---

## Important Property of CHAR

According to your notes, `CHAR` is **static**.

Think of it like a box that is fixed at the specified size.

For example:

```sql
Name CHAR(10)
```

If we store:

```text
Sachin
```

the value contains only **6 characters**, but the column has been defined with a size of **10**.

Your notes describe this as **memory being wasted** because `CHAR` is static. 

### Maximum Size

Your notes specify:

> `CHAR` can store up to **2000 characters**. 

---

# 2. VARCHAR2(size)

## What is `VARCHAR2`?

`VARCHAR2` is an alphanumeric data type used to store:

* Alphabets
* Numbers
* Special symbols

### Syntax

```sql
column_name VARCHAR2(size)
```

### Example

```sql
Name VARCHAR2(10)
```

---

## Important Property of VARCHAR2

According to your notes, `VARCHAR2` is **dynamic**.

For example:

```sql
Name VARCHAR2(10)
```

If we store:

```text
Sachin
```

only the required amount of storage is used rather than treating the entire 10-character size as fixed storage.

Therefore, your notes describe `VARCHAR2` as avoiding the memory wastage associated with `CHAR`. 

### Maximum Size

Your notes specify:

> `VARCHAR2` can store up to **4000 characters**. 

---

# 3. CHAR vs VARCHAR2

This is the **most important comparison**.

| Feature                    | CHAR                        | VARCHAR2              |
| -------------------------- | --------------------------- | --------------------- |
| Type                       | Alphanumeric                | Alphanumeric          |
| Storage nature             | Static                      | Dynamic               |
| Syntax                     | `CHAR(size)`                | `VARCHAR2(size)`      |
| Maximum size in your notes | 2000 characters             | 4000 characters       |
| Example                    | `Name CHAR(10)`             | `Name VARCHAR2(10)`   |
| Notes' storage explanation | Fixed-size, may waste space | Uses required storage |



---

# 4. Simple Example

```sql
CREATE TABLE student
(
    Name CHAR(10),
    Branch VARCHAR2(16)
);
```

Here:

```text
Name
 ↓
CHAR(10)
 ↓
Static
```

and:

```text
Branch
   ↓
VARCHAR2(16)
   ↓
Dynamic
```

---

# 5. Easy Way to Remember

### CHAR → Fixed

Think:

> **CHAR = Fixed-size box**

### VARCHAR2 → Variable

Think:

> **VARCHAR2 = Variable-size box**

So:

```text
CHAR      → Static
VARCHAR2  → Dynamic
```

---

# 6. Interview Questions

### Q1. What are alphanumeric data types in your notes?

**Answer:**
The alphanumeric data types are `CHAR` and `VARCHAR2`.

### Q2. What is CHAR?

**Answer:**
`CHAR` is an alphanumeric data type used to store alphabets, numbers, and special symbols. It is static in nature.

### Q3. What is VARCHAR2?

**Answer:**
`VARCHAR2` is an alphanumeric data type used to store alphabets, numbers, and special symbols. It is dynamic in nature.

### Q4. What is the difference between CHAR and VARCHAR2?

**Answer:**
`CHAR` is static, whereas `VARCHAR2` is dynamic.

### ⭐ One-line revision

```text
Alphanumeric Data Types
          ↓
     ┌────┴─────┐
     ↓          ↓
   CHAR      VARCHAR2
  Static      Dynamic
  2000         4000
```

