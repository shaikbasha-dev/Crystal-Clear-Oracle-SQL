# PRIMARY KEY Constraint in Oracle SQL

A **Primary Key** is a constraint used to **uniquely identify each row in a table**.

According to your notes, a Primary Key is a combination of:

> **UNIQUE + NOT NULL** 

So a Primary Key has **two important rules**:

```text
PRIMARY KEY
     ↓
 ┌───┴────┐
 ↓        ↓
UNIQUE   NOT NULL
 ↓        ↓
No       No
duplicate NULL
```

---

## 1. No Duplicate Values

Because Primary Key includes `UNIQUE`, duplicate values are **not allowed**.

Example:

```text
ID
---
101
102
103
101  ❌
```

The second `101` is not allowed.

---

## 2. No NULL Values

Because Primary Key also includes `NOT NULL`, a Primary Key **cannot contain NULL**.

```text
ID
---
101
102
NULL  ❌
```

So:

```text
Duplicate → ❌
NULL      → ❌
```

---

## 3. Primary Key Identifies Each Row

The main purpose of a Primary Key is to **identify every row uniquely**.

For example:

|  ID | Name  |
| --: | ----- |
| 101 | Cat   |
| 102 | Rat   |
| 103 | Tiger |

Here, `ID` can uniquely identify each student.

```text
101 → Cat
102 → Rat
103 → Tiger
```

Each row has its own unique identification.

---

## 4. Only One Primary Key Per Table

According to your notes:

> **Only one Primary Key is allowed per table.** 

For example:

```sql
CREATE TABLE student
(
    Id INT PRIMARY KEY,
    Name VARCHAR2(30)
);
```

Here, `Id` is the Primary Key.

---

## 5. Syntax

```sql
CREATE TABLE table_name
(
    column_name datatype PRIMARY KEY
);
```

### Example

```sql
CREATE TABLE Department
(
    did INT PRIMARY KEY,
    dname VARCHAR2(54)
);
```

This is the Primary Key example given in your notes. 

Here:

```text
did
 ↓
PRIMARY KEY
 ↓
UNIQUE + NOT NULL
```

---

## 6. Primary Key and Parent Key

Your notes state that the **table having a Primary Key is called the Parent Key**. 

This terminology is used in your notes for explaining the relationship with a Foreign Key.

---

## 7. Primary Key vs UNIQUE vs NOT NULL

| Constraint    | Duplicate | NULL |
| ------------- | --------- | ---- |
| `UNIQUE`      | ❌         | ✅    |
| `NOT NULL`    | ✅         | ❌    |
| `PRIMARY KEY` | ❌         | ❌    |

The easiest way to remember:

```text
UNIQUE
→ Duplicate ❌
→ NULL ✅

NOT NULL
→ Duplicate ✅
→ NULL ❌

PRIMARY KEY
→ Duplicate ❌
→ NULL ❌
```

---

# 🧠 Memory Trick

Remember:

> **PRIMARY KEY = UNIQUE + NOT NULL**

And its main purpose:

> **PRIMARY KEY = Uniquely identifies each row.**

### Interview Answer

> **A Primary Key is a constraint that uniquely identifies each row in a table. It is a combination of UNIQUE and NOT NULL, so it does not allow duplicate or NULL values. According to the notes, only one Primary Key is allowed per table.** 
