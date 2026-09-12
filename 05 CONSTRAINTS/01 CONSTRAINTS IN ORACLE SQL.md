# CONSTRAINTS IN ORACLE SQL

## 1. What is a Constraint?

A **constraint** is a **rule or restriction** that we apply to a particular column of a table.

In simple words:

> A constraint tells Oracle **what is allowed and what is not allowed** in a column.

For example, imagine a college student table.

We may have rules like:

* Student ID should not be duplicated.
* Student ID should not be empty.
* Age should be greater than 18.
* Gender may have a specific restriction.
* Department ID should refer to an existing department.

These rules can be implemented using **constraints**.

Your notes define constraints as **rules/restrictions implemented on particular table columns**. They help to **standardize the table** and achieve **business rules/client requirements**. 

---

# 2. Why Do We Need Constraints?

Without constraints, incorrect or unwanted data could be inserted into a table.

For example, suppose we have:

```text
Student ID
---------
101
102
101
```

If Student ID is supposed to identify each student uniquely, having `101` twice is a problem.

We can use a **constraint** to prevent duplicate values.

Similarly, suppose age must be greater than 18:

```text
Age
---
23     ✅
25     ✅
15     ❌
```

A constraint can prevent `15` from being inserted.

So constraints help us **control the data stored in a table**.

---

# 3. Simple Real-Life Analogy

Think about entering a college building.

There are rules:

```text
Student ID must be valid
Age must satisfy the requirement
One student cannot have two identical IDs
Department must exist
```

These rules control what is allowed.

Similarly, in a database:

```text
Database Table
      ↓
Constraints
      ↓
Rules / Restrictions
      ↓
Control the data
```

---

# 4. Types of Constraints in Your Notes

Your notes contain **six types of constraints**:

```text
                 CONSTRAINTS
                      │
       ┌──────────────┼──────────────┐
       ↓              ↓              ↓
    UNIQUE         NOT NULL      PRIMARY KEY
       ↓              ↓              ↓
FOREIGN KEY        CHECK          DEFAULT
```



We will study each one separately.

---

# 5. UNIQUE Constraint

### Meaning

The `UNIQUE` constraint ensures that a particular column **cannot contain duplicate values**.

However, according to your notes, it **can contain NULL values**. 

Example:

```text
Student_ID
----------
101
102
103
101  ❌
```

The second `101` violates the `UNIQUE` constraint.

But:

```text
101
102
NULL
```

is allowed according to your notes.

---

# 6. NOT NULL Constraint

### Meaning

The `NOT NULL` constraint ensures that a column **cannot contain NULL**.

However, it **can contain duplicate values**. 

Example:

```text
Phone_Number
------------
9876543210
9876543210
9123456789
NULL          ❌
```

Duplicates are allowed, but `NULL` is not allowed.

---

# 7. PRIMARY KEY Constraint

### Meaning

A **Primary Key** is a combination of:

```text
UNIQUE + NOT NULL
```

Therefore, a primary key:

* Cannot contain duplicate values.
* Cannot contain NULL values.
* Uniquely identifies every row.
* Only **one primary key** is allowed per table according to your notes. 

Example:

```text
ID
---
101
102
103
101  ❌
NULL ❌
```

So:

> **Primary Key = Unique + Not Null**

---

# 8. FOREIGN KEY Constraint

### Meaning

A **Foreign Key** refers to the **Primary Key of another table**.

It is used to establish a relationship between tables and achieve **referential integrity**. 

For example:

### Department

```text
DID
---
10
20
30
```

### Employee

```text
EMP_ID    DID
------    ---
101       10
102       20
103       10
```

Here `Employee.DID` can refer to `Department.DID`.

The table containing the foreign key is called the **Child table** in your notes.

Your notes also state that a foreign key can accept:

* Duplicate values
* NULL values 

---

# 9. CHECK Constraint

### Meaning

The `CHECK` constraint is used to impose a **condition** on a column.

For example:

```sql id="k6o0qf"
CHECK(age > 18)
```

This means:

```text
Age = 25  → ✅
Age = 20  → ✅
Age = 18  → ❌
Age = 15  → ❌
```

The value must satisfy the specified condition.

Your notes give examples such as:

```sql id="f3z8bq"
CHECK(age > 18)
```



---

# 10. DEFAULT Constraint

### Meaning

The `DEFAULT` constraint provides a **default value** when a value is not specified.

For example:

```sql id="h5v2h8"
Address VARCHAR2(54) DEFAULT 'India'
```

If we don't provide an address while inserting a row, Oracle uses:

```text
India
```

as the default value.

Your notes give this example in the `citizen` table. 

---

# 11. Citizen Table Example from Your Notes

Your notes combine several constraints in one table:

```sql id="w7a3qf"
CREATE TABLE citizen
(
    Id INT PRIMARY KEY,
    Name VARCHAR2(65),
    Gender VARCHAR2(65),
    Address VARCHAR2(54) DEFAULT 'India',
    Phone_number NUMBER NOT NULL,
    Age INT CHECK(age > 18)
);
```



Let's understand it:

```text
Id
 ↓
PRIMARY KEY
 ↓
No duplicate + No NULL
```

```text
Address
 ↓
DEFAULT 'India'
 ↓
If no value is supplied → India
```

```text
Phone_number
 ↓
NOT NULL
 ↓
Cannot be NULL
```

```text
Age
 ↓
CHECK(age > 18)
 ↓
Age must satisfy the condition
```

---

# 12. NULL — Important Concept

Your notes specifically give these rules about `NULL`: 

### NULL ≠ NULL

`NULL` does not equal another `NULL`.

```text
NULL ≠ NULL
```

### NULL ≠ 0

`NULL` and zero are different.

```text
NULL ≠ 0
```

`0` means an actual numeric value.

`NULL` means there is no value.

### NULL + 5 = NULL

If you perform an arithmetic operation with `NULL`:

```text
NULL + 5 = NULL
```

The result remains `NULL`.

---

# ⭐ 13. Quick Comparison

| Constraint      | Main Rule                                 |
| --------------- | ----------------------------------------- |
| **UNIQUE**      | No duplicate values; NULL allowed         |
| **NOT NULL**    | NULL not allowed; duplicates allowed      |
| **PRIMARY KEY** | No duplicates + no NULL                   |
| **FOREIGN KEY** | Refers to another table's primary key     |
| **CHECK**       | Value must satisfy a condition            |
| **DEFAULT**     | Supplies a value when one isn't specified |



---

# 🧠 14. Easy Memory Trick

Remember:

**U N P F C D**

```text
U → UNIQUE
N → NOT NULL
P → PRIMARY KEY
F → FOREIGN KEY
C → CHECK
D → DEFAULT
```

Or remember what each one does:

```text
UNIQUE      → Duplicate ❌
NOT NULL    → NULL ❌
PRIMARY KEY → Duplicate ❌ + NULL ❌
FOREIGN KEY → Relationship
CHECK       → Condition
DEFAULT     → Automatic value
```

---

# 🎯 Interview-Ready Answer

**What are constraints in Oracle SQL?**

> **Constraints are rules or restrictions applied to particular columns of a table. They help standardize the table and enforce business rules or client requirements. The constraints covered here are UNIQUE, NOT NULL, PRIMARY KEY, FOREIGN KEY, CHECK, and DEFAULT.** 

### One-line revision

> **Constraint = Rule/Restriction used to control the data stored in a table.**
