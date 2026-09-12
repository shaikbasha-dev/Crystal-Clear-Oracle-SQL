# UNIQUE Constraint in Oracle SQL

A **UNIQUE constraint** is a rule applied to a column that says:

> **Duplicate values are not allowed in that column.**

Your notes specifically state two things about `UNIQUE`:

1. A particular column **cannot have duplicate values**.
2. A particular column **can have NULL values**. 

---

## 1. Understanding with a Simple Table

Suppose we have a column with a UNIQUE constraint:

|  ID |
| --: |
| 101 |
| 102 |
| 103 |

This is valid because every value is different.

Now suppose we try:

|  ID |
| --: |
| 101 |
| 102 |
| 101 |

This is **not allowed**, because `101` appears more than once.

```text
UNIQUE
   ↓
Duplicate value → ❌
```

---

## 2. UNIQUE Can Have NULL

A UNIQUE column can contain a `NULL` value.

For example:

|   ID |
| ---: |
|  101 |
|  102 |
| NULL |

This is allowed according to your notes.

So remember:

```text
Duplicate → ❌
NULL      → ✅
```

---

## 3. UNIQUE vs Normal Column

### Normal column

A normal column can contain duplicate values:

|  ID |
| --: |
| 101 |
| 102 |
| 101 |

No UNIQUE rule → duplicate is possible.

### UNIQUE column

```text
101
102
101 ❌
```

The duplicate is rejected.

---

## 4. Most Important Point

Don't confuse `UNIQUE` with `NOT NULL`.

```text
UNIQUE
→ Duplicate ❌
→ NULL ✅
```

```text
NOT NULL
→ Duplicate ✅
→ NULL ❌
```

---

## 🧠 Memory Trick

**UNIQUE = Unique values**

Just remember:

> **UNIQUE stops duplicates, but NULL is allowed.**

### Interview Answer

> **UNIQUE constraint is used to prevent duplicate values in a particular column. It allows NULL values.** 
