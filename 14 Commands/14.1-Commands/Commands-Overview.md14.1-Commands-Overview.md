# 14.1-Commands-Overview

## 1. What are SQL Commands?

**SQL Commands** are instructions given to the database to perform different operations.

Using SQL commands, we can:

| Operation            | Example Purpose                 |
| -------------------- | ------------------------------- |
| Create               | Create a table                  |
| Modify               | Change the structure of a table |
| Insert               | Add data into a table           |
| Update               | Change existing data            |
| Delete               | Remove data                     |
| Retrieve             | Fetch data from a table         |
| Control permissions  | Give/remove access              |
| Control transactions | Save or undo changes            |

---

## 2. CRUD Operations

The notes introduce **CRUD** before classifying SQL commands.

**CRUD** stands for:

| Letter | Meaning | Basic Operation |
| ------ | ------- | --------------- |
| **C**  | Create  | Create          |
| **R**  | Read    | Read/Retrieve   |
| **U**  | Update  | Update          |
| **D**  | Delete  | Delete          |

### Simple Example

Suppose we have a `STUDENT` table.

```text
CREATE  → Create the table
INSERT  → Add student data
SELECT  → Read student data
UPDATE  → Change student data
DELETE  → Delete student data
```

---

# 3. Classification of SQL Commands

SQL commands are divided into **five categories** in this material.

| No. | Category | Full Form                    | Commands                      |
| --: | -------- | ---------------------------- | ----------------------------- |
|   1 | **DDL**  | Data Definition Language     | CREATE, ALTER, TRUNCATE, DROP |
|   2 | **DML**  | Data Manipulation Language   | INSERT, UPDATE, DELETE        |
|   3 | **DQL**  | Data Query Language          | SELECT                        |
|   4 | **DCL**  | Data Control Language        | GRANT, REVOKE                 |
|   5 | **TCL**  | Transaction Control Language | COMMIT, ROLLBACK, SAVEPOINT   |



---

# 4. DDL — Data Definition Language

### What is DDL?

DDL commands are used to **define the structure of a table**.

### DDL Commands

| Command      | Purpose                                     |
| ------------ | ------------------------------------------- |
| **CREATE**   | Create a database, table or object          |
| **ALTER**    | Modify the structure of an existing table   |
| **TRUNCATE** | Remove all rows from a table                |
| **DROP**     | Delete a table, database or database object |

The material explicitly lists these four commands under DDL. 

### Simple way to remember

```text
DDL
│
├── CREATE   → Build
├── ALTER    → Change structure
├── TRUNCATE → Remove all rows
└── DROP     → Remove object
```

We will study each one separately.

---

# 5. DML — Data Manipulation Language

### What is DML?

DML commands are used to **manipulate the data inside the table**.

The material describes DML operations as being related to the **rows of the table**. 

### DML Commands

| Command    | Purpose                    |
| ---------- | -------------------------- |
| **INSERT** | Insert data into the table |
| **UPDATE** | Change existing data       |
| **DELETE** | Remove data                |



### Simple way to remember

```text
DML
│
├── INSERT → Add
├── UPDATE → Change
└── DELETE → Remove
```

---

# 6. DQL — Data Query Language

### What is DQL?

DQL is used to **retrieve/query data from a table**.

### DQL Command

| Command    | Purpose       |
| ---------- | ------------- |
| **SELECT** | Retrieve data |

The notes list `SELECT` under Data Query Language. 

### Simple way to remember

```text
DQL
│
└── SELECT → Retrieve
```

---

# 7. DCL — Data Control Language

### What is DCL?

DCL deals with **controlling access/permissions**.

### DCL Commands

| Command    | Purpose            |
| ---------- | ------------------ |
| **GRANT**  | Give permissions   |
| **REVOKE** | Remove permissions |

The command classification lists `GRANT` and `REVOKE` under DCL. 

### Simple way to remember

```text
DCL
│
├── GRANT  → Give permission
└── REVOKE → Take back permission
```

---

# 8. TCL — Transaction Control Language

### What is TCL?

TCL stands for **Transaction Control Language**.

TCL commands are used to control transactions such as **insertion, updation and deletion**. They are used along with DML commands. 

### TCL Commands

| Command       | Purpose                                       |
| ------------- | --------------------------------------------- |
| **COMMIT**    | Permanently save DML changes                  |
| **ROLLBACK**  | Undo unsaved DML changes                      |
| **SAVEPOINT** | Create a temporary point inside a transaction |



### Simple way to remember

```text
TCL
│
├── COMMIT   → Save
├── ROLLBACK → Undo
└── SAVEPOINT → Mark a temporary point
```

---

# 9. Complete SQL Commands Map

This is the most important picture to remember:

```text
                    SQL COMMANDS
                         │
       ┌─────────────────┼─────────────────┐
       │                 │                 │
      DDL               DML               DQL
       │                 │                 │
   Structure           Data             Retrieve
       │                 │                 │
 ┌─────┼─────┐       ┌──┼──┐             │
 │     │     │       │  │  │             │
CREATE ALTER TRUNCATE INSERT UPDATE DELETE SELECT
             │
            DROP


                    SQL COMMANDS
                         │
              ┌──────────┴──────────┐
              │                     │
             DCL                   TCL
              │                     │
        Permissions             Transactions
              │                     │
          ┌───┴───┐             ┌──┼──────┐
          │       │             │  │      │
        GRANT   REVOKE       COMMIT ROLLBACK SAVEPOINT
```

---

# 10. Quick Comparison

| Category | Works Mainly With      | Commands                      |
| -------- | ---------------------- | ----------------------------- |
| **DDL**  | Table/object structure | CREATE, ALTER, TRUNCATE, DROP |
| **DML**  | Table data/rows        | INSERT, UPDATE, DELETE        |
| **DQL**  | Retrieving data        | SELECT                        |
| **DCL**  | Permissions            | GRANT, REVOKE                 |
| **TCL**  | Transactions           | COMMIT, ROLLBACK, SAVEPOINT   |

---

# 11. One-Line Memory Trick

Remember:

> **DDL → Structure**
> **DML → Data**
> **DQL → Query/Retrieve**
> **DCL → Control permissions**
> **TCL → Control transactions**

And the commands:

```text
DDL → CREATE, ALTER, TRUNCATE, DROP

DML → INSERT, UPDATE, DELETE

DQL → SELECT

DCL → GRANT, REVOKE

TCL → COMMIT, ROLLBACK, SAVEPOINT
```

This overview establishes the complete map. The following folders will explain each command and every `ALTER` sub-operation individually, with their syntax, syntax breakdown tables, questions, queries, outputs, explanations, and examples.
