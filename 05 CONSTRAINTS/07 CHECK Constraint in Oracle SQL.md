# CHECK Constraint in Oracle SQL

A **CHECK constraint** is a rule that says:

> **The value entered into a column must satisfy a specified condition.**

### Simple Example

```sql
CREATE TABLE citizen
(
    Id INT PRIMARY KEY,
    Name VARCHAR2(65),
    Gender VARCHAR2(65),
    Address VARCHAR2(54) DEFAULT 'India',
    Phone_number NUMBER NOT NULL,
    Age INT CHECK(Age > 18)
);
```

The important part is:

```sql
Age INT CHECK(Age > 18)
```

It means:

> The `Age` must be **greater than 18**.

### If Age is valid ✅

```sql
INSERT INTO citizen
VALUES(101, 'Basha', 'Male', 'India', 9876543210, 25);
```

`25 > 18`, so the value is accepted.

### If Age is invalid ❌

```sql
INSERT INTO citizen
VALUES(102, 'Ravi', 'Male', 'India', 9876543211, 16);
```

`16 > 18` is false, so Oracle will **not allow the value**.

### Memory Trick 🧠

**CHECK = Check a condition before accepting the value.**

```text
CHECK(Age > 18)
       ↓
Condition must be TRUE
       ↓
Value accepted
```

### Interview Answer

> **CHECK constraint is used to specify a condition that must be satisfied by the values entered into a column.**
