# Numeric Data Types in Oracle SQL

According to your notes, **Numeric Data Types** are used to store numerical values. Your notes cover **two numeric data types: `INT` and `NUMBER`**. 

---

## 1. `INT`

### What is `INT`?

`INT` is used to store **integer values**.

An integer is a number **without a decimal/fractional part**.

### Examples

```text
10
25
100
500
-20
```

### Syntax

```sql
column_name INT
```

### Example

```sql
CREATE TABLE student
(
    Id INT,
    Marks INT
);
```

Here:

* `Id` → can store integer values
* `Marks` → can store integer values

For example:

```sql
INSERT INTO student VALUES (458, 93);
```

### Important point from your notes

Your notes mention:

> `INT` size = **4 bytes**

and that it accepts **integer values, not fractional values**. 

---

# 2. `NUMBER`

### What is `NUMBER`?

`NUMBER` is used to store **numeric values**.

According to your notes, it can accept:

* Integer values
* Real/fractional values

### Examples

```text
100
5000
73.69
61.3
```

### Syntax

```sql
column_name NUMBER
```

### Example

```sql
CREATE TABLE employee
(
    Salary NUMBER
);
```

We can insert:

```sql
INSERT INTO employee VALUES (25000);
```

or:

```sql
INSERT INTO employee VALUES (25000.50);
```

---

# 3. `NUMBER(P,S)`

`NUMBER` can also be used with **Precision (P)** and **Scale (S)**.

### Syntax

```sql
column_name NUMBER(P,S)
```

Example:

```sql
Percentage NUMBER(4,2)
```

Here:

* `P` = Precision
* `S` = Scale

Your notes describe:

### Precision — `P`

The **total number of digits** considered before the decimal point.

### Scale — `S`

The **number of digits after the decimal point**.

Your notes use:

```sql
Percentage NUMBER(4,2)
```

and give examples such as:

| Value     | Notes' result |
| --------- | ------------- |
| `8`       | ✅ Yes         |
| `73.69`   | ✅ Yes         |
| `61.3267` | ❌ No          |
| `61.3`    | ✅ Yes         |
| `564`     | ❌ No          |
| `100`     | ❌ No          |



### ⚠️ Technical correction

There is an important technical issue in the notes here.

In **Oracle**, the first number in `NUMBER(P,S)` is the **total precision (total significant digits), not simply the digits before the decimal point**.

So `NUMBER(4,2)` means:

* Maximum precision = **4 digits total**
* Scale = **2 digits to the right of the decimal**

For example:

```text
73.69
```

has 4 total digits → valid.

```text
61.3267
```

has more than 4 total digits → it cannot fit as entered.

So remember the **actual Oracle definition**:

> **Precision = total number of significant digits.**
> **Scale = number of digits to the right of the decimal point.**

---

# 4. `INT` vs `NUMBER`

| Feature        | `INT`          | `NUMBER`        |
| -------------- | -------------- | --------------- |
| Used for       | Integer values | Numeric values  |
| Decimal values | ❌              | ✅               |
| Example        | `100`          | `100`, `73.69`  |
| Syntax         | `Age INT`      | `Salary NUMBER` |
| `NUMBER(P,S)`  | ❌              | ✅               |

### Simple memory trick

**INT → Integer**

**NUMBER → Number, including decimal values**

---

# 5. Example Using Both

```sql
CREATE TABLE student
(
    Id INT,
    Marks INT,
    Percentage NUMBER(4,2)
);
```

Then:

```sql
INSERT INTO student
VALUES (458, 93, 93.50);
```

Here:

```text
Id          → INT
Marks       → INT
Percentage  → NUMBER(4,2)
```

---

# 6. Interview Questions

### Q1. What is a numeric data type?

**Answer:**
A numeric data type is used to store numerical values in a database.

### Q2. What numeric data types are covered in your Oracle SQL notes?

**Answer:**
`INT` and `NUMBER`.

### Q3. What is the difference between INT and NUMBER?

**Answer:**
`INT` is used for integer values, whereas `NUMBER` can store numeric values including fractional values.

### Q4. What is `NUMBER(P,S)`?

**Answer:**
`NUMBER(P,S)` allows us to specify **precision and scale**, where precision represents the total number of significant digits and scale represents the number of digits to the right of the decimal point.

### ⭐ One-line revision

```text
Numeric Data Types
       ↓
   INT → Integer
       ↓
 NUMBER → Numeric values
       ↓
NUMBER(P,S) → Precision + Scale
```
