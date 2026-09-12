# RETRIEVING THE DATA

**Retrieving the data** means **fetching the required data from a table**.

For example, suppose we have a `student` table:

| NAME  | AGE | GENDER | MARKS |
| ----- | --: | ------ | ----: |
| Cat   |  23 | Male   |    93 |
| Rat   |  24 | Female |    88 |
| Tiger |  26 | Female |    98 |
| Lion  |  18 | male   |    34 |

When we want to see information from this table, we use the **`SELECT` statement**.

Your notes explain retrieving data using two concepts:

1. **Selection**
2. **Projection** 

---

# 1. Selection

### What is Selection?

**Selection means fetching data from a table by eliminating certain rows from it.**

In simple words:

> We don't want all rows. We want only the rows that satisfy a particular condition.



### Example

Suppose we want only students whose gender is `Male`.

```sql
SELECT *
FROM student
WHERE gender = 'Male';
```

Here, Oracle checks the rows and returns only the row satisfying the condition.

Result:

| NAME | AGE | GENDER | MARKS |
| ---- | --: | ------ | ----: |
| Cat  |  23 | Male   |    93 |

So:

```text
Selection
   ↓
Condition applied
   ↓
Some rows eliminated
   ↓
Required rows fetched
```

---

# 2. Projection

### What is Projection?

**Projection means fetching data from a table without eliminating any rows from the table.**

In simple words:

> We want all rows, but we want only particular columns.



For example:

```sql
SELECT name, age, gender
FROM student;
```

Oracle returns the `name`, `age`, and `gender` columns for **all students**.

Result:

| NAME  | AGE | GENDER |
| ----- | --: | ------ |
| Cat   |  23 | Male   |
| Rat   |  24 | Female |
| Tiger |  26 | Female |
| Lion  |  18 | male   |

Notice:

* No rows were eliminated.
* Only selected columns were displayed.

---

# 3. Query: Display Name from Student Table

### Question

> Write a query to display name from the student table.

### Query

```sql
SELECT name
FROM student;
```



### Output

```text
NAME
----
Cat
Rat
Tiger
Lion
```

### What happened?

We selected only the `name` column.

All four rows are still present.

Therefore, this is **Projection**.

---

# 4. Query: Display Name, Age, Gender

### Question

> Write a query to display name, age, gender from the student table.

### Query

```sql
SELECT name, age, gender
FROM student;
```



### Output

| NAME  | AGE | GENDER |
| ----- | --: | ------ |
| Cat   |  23 | Male   |
| Rat   |  24 | Female |
| Tiger |  26 | Female |
| Lion  |  18 | male   |

Again, **all rows are present**, but only three columns are displayed.

Therefore, this is **Projection**.

---

# 5. Query: Display All Data

### Question

> Write a query to display all the data from student table.

### Query

```sql
SELECT *
FROM student;
```



Here `*` means:

> **All columns**

### Output

| NAME  | AGE | GENDER | MARKS |
| ----- | --: | ------ | ----: |
| Cat   |  23 | Male   |    93 |
| Rat   |  24 | Female |    88 |
| Tiger |  26 | Female |    98 |
| Lion  |  18 | male   |    34 |

All columns and all rows are displayed.

---

# 6. Query: Name of Student Whose Age is 22

### Question

> Write a query to display name of student whose age is 22.

### Query

```sql
SELECT name
FROM student
WHERE age = 22;
```



### Output

```text
no data found
```

Why?

Because there is **no student whose age is 22** in the data shown in your notes.

The ages are:

```text
23
24
26
18
```

There is no `22`.

---

# 7. Query: Details of Students Whose Gender is Male

### Question

> Write a query to display details of the students whose gender is male.

### Query

```sql
SELECT *
FROM student
WHERE gender = 'Male';
```



### Output

| NAME | AGE | GENDER | MARKS |
| ---- | --: | ------ | ----: |
| Cat  |  23 | Male   |    93 |

Here:

```sql
WHERE gender = 'Male'
```

is the **condition**.

Rows that don't satisfy the condition are eliminated.

Therefore, this is **Selection**.

---

# 8. Query: Students Who Scored Greater Than 60

### Question

> Write a query to display details of students who scored greater than 60 marks.

### Query

```sql
SELECT *
FROM student
WHERE marks > 60;
```



### Output

| NAME  | AGE | GENDER | MARKS |
| ----- | --: | ------ | ----: |
| Cat   |  23 | Male   |    93 |
| Rat   |  24 | Female |    88 |
| Tiger |  26 | Female |    98 |

Why is `Lion` not displayed?

Because:

```text
Lion → 34 marks
```

and:

```text
34 > 60 ❌
```

Therefore, the `Lion` row is eliminated.

This is **Selection**.

---

# ⭐ Selection vs Projection

| Selection               | Projection                  |
| ----------------------- | --------------------------- |
| Eliminates **rows**     | Does not eliminate rows     |
| Uses a condition        | Selects required columns    |
| Usually uses `WHERE`    | Uses columns in `SELECT`    |
| Example: `WHERE age=22` | Example: `SELECT name, age` |
| Works mainly on rows    | Works mainly on columns     |

### Easy Memory Trick

**Selection → Select rows**

**Projection → Select columns**

Think:

```text
SELECTION
   ↓
Rows

PROJECTION
   ↓
Columns
```

---

# 🔥 All Queries From This Topic

Do not forget these **7 queries** from the `RETRIEVING THE DATA` section of your notes:

### 1. Display name

```sql
SELECT name
FROM student;
```

### 2. Display name, age, gender

```sql
SELECT name, age, gender
FROM student;
```

### 3. Display all data

```sql
SELECT *
FROM student;
```

### 4. Display name where age = 22

```sql
SELECT name
FROM student
WHERE age = 22;
```

### 5. Display details where gender = Male

```sql
SELECT *
FROM student
WHERE gender = 'Male';
```

### 6. Display details where marks > 60

```sql
SELECT *
FROM student
WHERE marks > 60;
```

These are the queries listed under **RETRIEVING THE DATA** in the relevant section of your notes. 

---

## 🧠 Final Revision

```text
RETRIEVING DATA
       ↓
   SELECT
       ↓
 ┌─────┴─────┐
 ↓           ↓
Selection   Projection
 ↓           ↓
Rows        Columns
 ↓           ↓
WHERE       SELECT
condition   required columns
```

**One-line interview answer:**

> **Selection fetches data by eliminating certain rows, whereas Projection fetches data without eliminating rows.** 
