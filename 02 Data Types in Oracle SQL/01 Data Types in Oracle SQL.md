# Data Types in Oracle SQL

A **data type** tells Oracle **what kind of data a column is going to store**.

For example:

* A person's **age** → number
* A person's **name** → text
* A person's **gender** → text
* A person's **date of birth** → date

Think of a database table like a set of **boxes**. Before putting something into a box, we tell Oracle what kind of thing that box is meant to hold.

---

## 1. Why do we need Data Types?

When we create a table, Oracle needs to know:

> **“What type of data will this column store?”**

For example:

```sql
CREATE TABLE student
(
    Name VARCHAR2(16),
    Age NUMBER,
    Gender CHAR(6),
    Branch VARCHAR2(16),
    Id INT,
    Marks INT
);
```

Here Oracle knows:

| Column   | Data Type  | What it stores |
| -------- | ---------- | -------------- |
| `Name`   | `VARCHAR2` | Name/text      |
| `Age`    | `NUMBER`   | Number         |
| `Gender` | `CHAR`     | Text           |
| `Branch` | `VARCHAR2` | Text           |
| `Id`     | `INT`      | Integer        |
| `Marks`  | `INT`      | Integer        |

So, **data type indicates what type of data a column holds in the future.** 

---

# 2. Data Types in Your Notes

Your notes divide the data types into these categories:

```text
Data Types
│
├── Numeric
│   ├── INT
│   └── NUMBER
│       └── NUMBER(P,S)
│
├── Alphanumeric
│   ├── CHAR(size)
│   └── VARCHAR2(size)
│
└── Date
```

We will study each category separately.

---

# 3. Numeric Data Types

Numeric data types are used for **numbers**.

Your notes contain:

### `INT`

Used for **integer values**.

Example:

```sql
Age INT
```

It can store:

```text
10
25
100
500
```

It does not accept fractional values according to your notes.

---

### `NUMBER`

Used for **numeric values**, including integers and real/fractional numbers.

Example:

```sql
Salary NUMBER
```

It can store values such as:

```text
5000
25000
73.69
```

---

### `NUMBER(P,S)`

Used when we want to specify **precision and scale**.

Example:

```sql
Percentage NUMBER(4,2)
```

Your notes explain:

* **P = Precision**
* **S = Scale**

We will study this in detail in the **Numeric Data Types** response.

---

# 4. Alphanumeric Data Types

Alphanumeric means data containing:

* Alphabets
* Numbers
* Special symbols

Your notes contain two alphanumeric data types:

### `CHAR(size)`

Example:

```sql
Name CHAR(10)
```

`CHAR` is **static** in nature.

### `VARCHAR2(size)`

Example:

```sql
Name VARCHAR2(10)
```

`VARCHAR2` is **dynamic** in nature.

We will study `CHAR` and `VARCHAR2` in detail in the **Alphanumeric Data Types** response.

---

# 5. Date

The `DATE` data type is used for storing **date information**.

Your notes give the Oracle date format as:

```text
DD-MM-YYYY
```

Example:

```text
29-May-2000
```

Your notes also mention that MySQL uses:

```text
YYYY-MM-DD
```

We will study **Date** separately in the fourth response.

---

# 6. Simple Example

Suppose we want to create a student table.

```sql
CREATE TABLE student
(
    Name VARCHAR2(16),
    Age NUMBER,
    Gender CHAR(6),
    Id INT,
    Marks INT
);
```

Oracle looks at the table like this:

```text
Name   → VARCHAR2 → Text
Age    → NUMBER   → Number
Gender → CHAR     → Text
Id     → INT      → Integer
Marks  → INT      → Integer
```

Then we can insert data:

```sql
INSERT INTO student
VALUES ('Basha', 23, 'Male', 458, 93);
```

Oracle checks the values against the respective column data types.

---

# 7. Most Important Point

Remember this definition for interviews:

> **Data types indicate what type of data a column can hold.**

And remember the classification from your notes:

```text
                 DATA TYPES
                     │
        ┌────────────┼────────────┐
        ↓            ↓            ↓
     Numeric     Alphanumeric     Date
        │            │
     INT          CHAR
     NUMBER       VARCHAR2
```

### 🧠 Memory Trick

**N → A → D**

**N**umeric → Numbers
**A**lphanumeric → Text/characters
**D**ate → Dates

The next three responses will cover **Numeric**, **Alphanumeric**, and **Date** separately and in detail.
