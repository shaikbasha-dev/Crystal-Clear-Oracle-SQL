# NOT NULL Constraint in Oracle SQL

The **NOT NULL constraint** is a rule applied to a column that says:

> **The column cannot contain NULL values.**

Your notes specifically state:

* A `NOT NULL` column **cannot have NULL**.
* It **can have duplicate values**. 

---

## 1. What does NOT NULL mean?

Suppose we have a `Phone_Number` column with `NOT NULL`.

```text
Phone_Number
------------
9876543210
9123456789
NULL        ❌
```

The `NULL` value is not allowed.

Why?

Because we have given Oracle the rule:

```text
NOT NULL
   ↓
NULL is not allowed
```

---

## 2. Can Duplicate Values Exist?

**Yes.**

`NOT NULL` does **not** prevent duplicates.

For example:

```text
Phone_Number
------------
9876543210
9123456789
9876543210   ✅
```

The value `9876543210` appears twice, but this is allowed because the `NOT NULL` constraint only prevents `NULL`.

So:

```text
NOT NULL
   ↓
NULL      → ❌
Duplicate → ✅
```

---

## 3. UNIQUE vs NOT NULL

This is an important difference:

| Constraint | Duplicate     | NULL          |
| ---------- | ------------- | ------------- |
| `UNIQUE`   | ❌ Not allowed | ✅ Allowed     |
| `NOT NULL` | ✅ Allowed     | ❌ Not allowed |

### Easy Memory Trick

**UNIQUE → No duplicates**

**NOT NULL → No NULL**

---

## 4. Example from Your Notes

Your notes use `NOT NULL` in the `citizen` table:

```sql
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

Here:

```sql
Phone_number NUMBER NOT NULL
```

means the `Phone_number` column **cannot contain NULL**. 

---

## 🧠 Final Revision

```text
NOT NULL
   ↓
NULL → ❌
Duplicate → ✅
```

### Interview Answer

> **NOT NULL is a constraint that prevents NULL values in a particular column, but duplicate values are allowed.**
