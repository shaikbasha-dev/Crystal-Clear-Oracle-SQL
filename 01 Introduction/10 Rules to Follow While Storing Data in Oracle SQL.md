# Rules to Follow While Storing Data in Oracle SQL

According to your notes, there are **3 main rules** to follow while storing data in a database:

### 1. Create a Table

First, we need to **create a table** where the data will be stored.

**Syntax:**

```sql
CREATE TABLE table_name
(
    column_name1 datatype,
    column_name2 datatype,
    column_name3 datatype
);
```

**Example:**

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

Here, the `student` table is created with six columns.

---

### 2. Specify the Columns

While creating the table, we need to **specify the columns and their data types**.

For example:

| Column | Data Type    |
| ------ | ------------ |
| Name   | VARCHAR2(16) |
| Age    | NUMBER       |
| Gender | CHAR(6)      |
| Branch | VARCHAR2(16) |
| Id     | INT          |
| Marks  | INT          |

The **data type tells Oracle what type of data that column can store**.

For example:

* `Name` → text
* `Age` → number
* `Marks` → number

---

### 3. Insert Values

After creating the table and specifying its columns, we can **insert values into the table**.

**Syntax:**

```sql
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```

**Example:**

```sql
INSERT INTO student
VALUES ('Shaik Mahaboob Basha', 23, 'Male', 'E.C.E', 458, 93);
```

Now the data is stored as a row in the `student` table.

### Complete Flow

```text
Create Table
     ↓
Specify Columns + Data Types
     ↓
Insert Values
     ↓
Data Stored in Table
```

### ⭐ Easy Memory Trick

**C → S → I**

* **C** = Create the table
* **S** = Specify columns
* **I** = Insert values

These are the **three rules given in your material for storing data**. 
