# DEFAULT Constraint in Oracle SQL

A **DEFAULT constraint** gives a **default value to a column when no value is specified**.

### Simple Example

```sql
CREATE TABLE citizen
(
    Id INT PRIMARY KEY,
    Name VARCHAR2(65),
    Address VARCHAR2(54) DEFAULT 'India'
);
```

Here:

```sql
Address VARCHAR2(54) DEFAULT 'India'
```

means:

> If we don't provide an `Address` while inserting a row, Oracle uses **`India`** as the value.

### Example

```sql
INSERT INTO citizen(Id, Name)
VALUES(101, 'Basha');
```

We did **not** provide Address.

So the result will be:

```text
Id     Name      Address
101    Basha     India
```

### Another Example

If we explicitly provide the address:

```sql
INSERT INTO citizen(Id, Name, Address)
VALUES(102, 'Ravi', 'Hyderabad');
```

Result:

```text
Id     Name      Address
102    Ravi      Hyderabad
```

So:

**Value provided → provided value is stored**

**Value not provided → default value is stored**

### 🧠 Memory Trick

> **DEFAULT = If you don't give a value, Oracle gives the default value.**

### Interview Answer

> **DEFAULT is a constraint that automatically assigns a specified value to a column when no value is provided for that column during insertion.**
