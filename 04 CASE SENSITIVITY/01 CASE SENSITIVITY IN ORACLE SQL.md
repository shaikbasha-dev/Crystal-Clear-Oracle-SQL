# CASE SENSITIVITY IN ORACLE SQL

**Case sensitivity** means whether Oracle treats **uppercase and lowercase letters as different or the same**.

According to your notes, there are **five areas** to remember. 

---

## 1. Commands / Keywords

Oracle SQL **commands and keywords are not case-sensitive**.

For example, all of these mean the same thing:

```sql
SELECT * FROM student;
```

```sql
select * from student;
```

```sql
SeLeCt * FrOm student;
```

So:

```text
SELECT = select = SeLeCt
```

Oracle understands them all.

---

## 2. Table Names

According to your notes, **table names are not case-sensitive**.

For example:

```sql
SELECT * FROM student;
```

and

```sql
SELECT * FROM STUDENT;
```

are treated the same.

---

## 3. Column Names

Column names are also **not case-sensitive** according to your notes.

For example:

```sql
SELECT name FROM student;
```

and

```sql
SELECT NAME FROM student;
```

refer to the same column.

---

## 4. Data Types

Data types are also **not case-sensitive**.

For example:

```sql
VARCHAR2(20)
```

and

```sql
varchar2(20)
```

are treated the same.

Similarly:

```sql
NUMBER
```

and

```sql
number
```

mean the same data type.

---

## 5. Data Stored in the Table

This is the important exception.

**Data stored in the table is case-sensitive** according to your notes. 

Suppose the table contains:

```text
Gender
Male
```

Then:

```sql
SELECT *
FROM student
WHERE gender = 'Male';
```

can match the value `Male`.

But:

```sql
SELECT *
FROM student
WHERE gender = 'male';
```

is different because the stored value is `Male`.

So:

```text
'Male' ≠ 'male'
```

The capitalization of the **actual data value matters**.

---

## 6. Constraints

According to your notes, **constraints are not case-sensitive**. 

For example:

```sql
PRIMARY KEY
```

and

```sql
primary key
```

represent the same constraint keyword.

---

# ⭐ Complete Summary

| Part                 | Case Sensitive? |
| -------------------- | --------------- |
| Commands / Keywords  | ❌ No            |
| Table Names          | ❌ No            |
| Column Names         | ❌ No            |
| Data Types           | ❌ No            |
| Data stored in table | ✅ Yes           |
| Constraints          | ❌ No            |



---

## 🧠 Easy Memory Trick

Remember:

> **SQL structure is not case-sensitive, but the data is case-sensitive.**

Example:

```text
SELECT  → SELECT / select / SeLeCt  → Same
student → STUDENT / student         → Same
NAME    → name / NAME               → Same
VARCHAR2 → varchar2                 → Same

'Male' → 'male' → Different
```

### Interview Answer

> **In Oracle SQL, commands, keywords, table names, column names, data types, and constraints are not case-sensitive, whereas the data stored in the table is case-sensitive.** 
