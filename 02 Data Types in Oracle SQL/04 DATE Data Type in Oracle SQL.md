# DATE Data Type in Oracle SQL

The **DATE** data type is used to store **date values**.

According to your notes, Oracle follows the date format:

> **DD-MM-YYYY**



---

## 1. What is DATE?

When we need to store information related to a date, we use the `DATE` data type.

For example:

```text
29-May-2000
```

This represents a date.

---

## 2. Syntax

The basic syntax is:

```sql
column_name DATE
```

### Example

```sql
CREATE TABLE student
(
    Name VARCHAR2(16),
    Date_of_Birth DATE
);
```

Here:

```text
Name          → VARCHAR2
Date_of_Birth → DATE
```

---

## 3. Example Date

Your notes give:

```text
29-May-2000
```

as an example of an Oracle date.

The format mentioned in your notes is:

```text
DD-MM-YYYY
```

Meaning:

| Part   | Meaning |
| ------ | ------- |
| `DD`   | Day     |
| `MM`   | Month   |
| `YYYY` | Year    |

So conceptually:

```text
29 - 05 - 2000
↓    ↓     ↓
Day Month Year
```

---

## 4. Oracle vs MySQL Date Format

Your notes specifically compare the formats:

| Database   | Format       |
| ---------- | ------------ |
| **Oracle** | `DD-MM-YYYY` |
| **MySQL**  | `YYYY-MM-DD` |



### Memory Trick

**Oracle → DD-MM-YYYY**

**MySQL → YYYY-MM-DD**

---

## 5. Simple Example

```sql
CREATE TABLE student
(
    Id INT,
    Name VARCHAR2(16),
    Date_of_Birth DATE
);
```

A row could contain:

```text
458 | Basha | 29-May-2000
```

Here:

* `458` → `INT`
* `Basha` → `VARCHAR2`
* `29-May-2000` → `DATE`

---

# ⭐ Interview Answer

**Q: What is the DATE data type in Oracle SQL?**

**Answer:**
The `DATE` data type is used to store date values. According to the given notes, Oracle uses the `DD-MM-YYYY` date format, with `29-May-2000` as an example.

---

## 🔑 Final Revision

```text
DATE
 ↓
Used to store date values
 ↓
Oracle format → DD-MM-YYYY
 ↓
Example → 29-May-2000
```

This completes the **Data Types** section covered in your notes: **Numeric → Alphanumeric → Date**.
