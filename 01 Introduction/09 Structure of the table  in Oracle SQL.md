# Structure of a Table in Oracle SQL

## 1. What is a Table?

A **table** is a structure in which data is stored in an organized manner.

Think of a table like a spreadsheet:

```text
        Columns
           ↓
+------+--------+-----+--------+
| Name | Age    | Gender | Marks |
+------+--------+-----+--------+
| Cat  | 23     | Male   | 93    |
| Rat  | 24     | Female | 88    |
| Tiger| 26     | Female | 98    |
| Lion | 18     | Male   | 34    |
+------+--------+-----+--------+
              ↑
             Rows
```

Your material calls a table a **Table / Relation**. 

---

# 2. Main Parts of a Table

There are two important parts:

### 1. Rows

Rows represent individual records.

A row is also called:

* **Tuple**
* **Record**

For example:

```text
Cat | 23 | Male | 93
```

This is one row/record/tuple.

### 2. Columns

Columns represent individual fields/attributes.

A column is also called:

* **Attribute**
* **Field**

For example:

```text
Name
Age
Gender
Marks
```

These are columns/attributes/fields.

Your material gives these equivalent terms. 

---

# 3. Simple Analogy

Think about a **student register**.

```text
+------+--------+------+-------+
| Name | Age    | Gender | Marks |
+------+--------+------+-------+
| Cat  | 23     | Male   | 93    |
| Rat  | 24     | Female | 88    |
```

### Columns

```text
Name
Age
Gender
Marks
```

These tell us **what type of information** we are storing.

### Rows

```text
Cat | 23 | Male | 93
Rat | 24 | Female | 88
```

These contain the **actual records**.

---

# 4. Structure of a Table

The basic structure is:

```text
                    TABLE / RELATION
                           |
             +-------------+-------------+
             |                           |
           ROWS                       COLUMNS
             |                           |
      Tuple / Record            Attribute / Field
```

So remember:

```text
Row
 ↓
Tuple / Record

Column
 ↓
Attribute / Field

Table
 ↓
Relation
```

---

# 5. Example from Oracle SQL

Suppose we create a `student` table:

```sql
CREATE TABLE student (
    Name VARCHAR2(16),
    Age NUMBER,
    Gender CHAR(6),
    Branch VARCHAR2(16),
    Id INT,
    Marks INT
);
```

The table structure will be:

```text
STUDENT

+----------------------+----------+
| Column               | Data Type|
+----------------------+----------+
| Name                 | VARCHAR2 |
| Age                  | NUMBER   |
| Gender               | CHAR     |
| Branch               | VARCHAR2 |
| Id                   | INT      |
| Marks                | INT      |
+----------------------+----------+
```

Your material uses this `student` table example. 

---

# 6. After Inserting Data

If we insert:

```sql
INSERT INTO student
VALUES ('Shaik Mahaboob Basha', 23, 'Male', 'E.C.E', 458, 93);
```

the table contains:

```text
+----------------------+-----+------+-------+-----+-------+
| Name                 | Age |Gender| Branch| Id  | Marks |
+----------------------+-----+------+-------+-----+-------+
| Shaik Mahaboob Basha | 23  | Male | E.C.E | 458 | 93    |
+----------------------+-----+------+-------+-----+-------+
```

The **columns** define what information can be stored, while the **row** contains one student's information. 

---

# 7. Why do we need Columns?

Before storing data, we need to specify what information the table should contain.

For example:

```text
Student
   ↓
Name
Age
Gender
Branch
Id
Marks
```

Each column has a **data type**.

For example:

```text
Name   → VARCHAR2
Age    → NUMBER
Gender → CHAR
Id     → INT
Marks  → INT
```

This tells the database what type of data each column is expected to hold.

---

# 8. Why do we need Rows?

After defining the columns, we insert actual information.

For example:

```text
Name                  Age   Gender   Branch   Id    Marks
----------------------------------------------------------
Shaik Mahaboob Basha  23    Male     E.C.E    458   93
```

This complete horizontal entry is one **row/record/tuple**.

---

# 9. Important Terminology

This is very important for interviews:

| Term       | Also called       |
| ---------- | ----------------- |
| **Table**  | Relation          |
| **Row**    | Tuple / Record    |
| **Column** | Attribute / Field |

Your material specifically gives these relationships. 

### 🧠 Memory Trick

```text
TABLE  → RELATION
ROW    → RECORD / TUPLE
COLUMN → FIELD / ATTRIBUTE
```

Think:

> **Table has Rows and Columns.**
> **Rows are Records.**
> **Columns are Fields.**

---

# 10. Common Confusion

### Row vs Column

A **row** goes horizontally:

```text
Cat | 23 | Male | 93
```

A **column** goes vertically:

```text
Name
-----
Cat
Rat
Tiger
Lion
```

### Record vs Field

```text
Record → complete row
Field  → individual column
```

For example:

```text
Cat | 23 | Male | 93
```

is one **record**.

`Age` is one **field**.

---

# 11. Interview Questions

### Q1. What is a table?

> A table is an organized structure used to store data in rows and columns. A table is also called a relation.

### Q2. What is a row?

> A row is a record or tuple in a table.

### Q3. What is a column?

> A column is an attribute or field in a table.

### Q4. What is another name for a table?

> **Relation.**

### Q5. What are the other names for a row?

> **Tuple and Record.**

### Q6. What are the other names for a column?

> **Attribute and Field.**

---

# 12. Interview-Ready Answer

If the interviewer asks:

**"Explain the structure of a table."**

You can say:

> **A table, also called a relation, is structured using rows and columns. A row is also called a tuple or record, and a column is also called an attribute or field. Columns define the type of information to be stored, and rows contain the actual records.**

---

# 13. Practice Questions

1. What is a table?
2. What is another name for a table?
3. What is a row?
4. What are the other names for a row?
5. What is a column?
6. What are the other names for a column?
7. What is the difference between a row and a column?
8. What is a record?
9. What is an attribute?
10. What is a field?
11. What is a tuple?
12. Explain the structure of a table with an example.

---

## 🧠 Final Memory

```text
             TABLE
            /     \
         ROWS     COLUMNS
          ↓          ↓
   Tuple/Record   Attribute/Field
```

**One-line memory:**

> **Table = Relation, Row = Tuple/Record, Column = Attribute/Field.**
