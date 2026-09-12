# FOREIGN KEY Constraint in Oracle SQL

A **Foreign Key** is a constraint that **refers to the Primary Key of another table**.

It is used to establish a **relationship between two tables** and achieve **referential integrity**.

---

## 1. Simple Example

Consider two tables:

### Department

```text
DID
---
10
20
30
```

Here, `DID` is the **Primary Key**.

### Employee

```text
ID    NAME     DID
---   -----    ---
101   Akash    10
102   Ravi     20
103   John     10
```

Here, `DID` in the Employee table is the **Foreign Key**.

It refers to:

```text
Employee.DID
      ↓
Department.DID
```

So the Foreign Key connects the two tables.

---

## 2. Parent Table and Child Table

```text
Department
    ↓
Primary Key
    ↓
Parent Table
```

```text
Employee
    ↓
Foreign Key
    ↓
Child Table
```

The Foreign Key is present in the **Child table**, while the referenced Primary Key is present in the **Parent table**.

---

## 3. Syntax

```sql
CREATE TABLE Department
(
    did INT PRIMARY KEY,
    dname VARCHAR2(54)
);
```

```sql
CREATE TABLE Employee
(
    id INT PRIMARY KEY,
    name VARCHAR2(87),
    salary NUMBER,
    did INT,
    FOREIGN KEY(did) REFERENCES Department(did)
);
```

The important part is:

```sql
FOREIGN KEY(did) REFERENCES Department(did)
```

It means:

> `did` in `Employee` refers to `did` in `Department`.

---

## 4. Duplicate Values

A Foreign Key **can contain duplicate values**.

For example:

```text
ID    DID
101   10
102   20
103   10
```

Here `10` appears twice.

That is allowed.

```text
Foreign Key
     ↓
Duplicate → ✅
```

---

## 5. NULL Values

A Foreign Key **can contain NULL values**.

```text
ID    DID
101   10
102   20
103   NULL
```

This is allowed.

```text
Foreign Key
     ↓
NULL → ✅
```

---

## 6. Referential Integrity

The Foreign Key helps achieve **referential integrity**.

It maintains the relationship between the Foreign Key in the child table and the Primary Key in the parent table.

```text
Parent Table
Department
    │
    │ Primary Key
    ↓
Child Table
Employee
    │
    │ Foreign Key
    ↓
Relationship
```

---

## 7. Primary Key vs Foreign Key

| Primary Key                  | Foreign Key                            |
| ---------------------------- | -------------------------------------- |
| Uniquely identifies each row | Refers to Primary Key of another table |
| Duplicate values ❌           | Duplicate values ✅                     |
| NULL values ❌                | NULL values ✅                          |
| Present in Parent table      | Present in Child table                 |

---

## 🧠 Memory Trick

**Primary Key → Parent**

**Foreign Key → Child**

And remember:

> **Foreign Key = Reference to another table's Primary Key**

### Interview Answer

> **A Foreign Key is a constraint that refers to the Primary Key of another table. It establishes a relationship between tables and helps achieve referential integrity. A Foreign Key can contain duplicate and NULL values.**
