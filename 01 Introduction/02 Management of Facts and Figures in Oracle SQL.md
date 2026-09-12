# Management of Facts and Figures in Oracle SQL

## 1. What is Management of Facts and Figures?

**Management of facts and figures** means handling the information properly.

It mainly involves two important activities:

1. **Store Permanently**
2. **Retrieve Efficiently**

So:

```text
Facts & Figures
       ↓
   Management
       ↓
 ┌───────────────┐
 │ Store         │
 │ Permanently   │
 └───────────────┘
       +
 ┌───────────────┐
 │ Retrieve      │
 │ Efficiently   │
 └───────────────┘
```

---

## 2. Why do we need it?

Imagine a university has information about thousands of students:

```text
Student Name
Age
Gender
Branch
Student ID
Marks
```

We need to:

* Keep this information safely for future use.
* Find the required student's information whenever needed.

Therefore, proper management of facts and figures is necessary.

---

## 3. Simple Real-Life Analogy

Imagine you have **1000 paper documents**.

If you simply throw them into a room:

```text
📄 📄 📄 📄 📄
📄 📄 📄 📄 📄
📄 📄 📄 📄 📄
```

Finding one particular document becomes difficult.

Instead, suppose you organize them properly:

```text
Student Documents
       ↓
Department-wise
       ↓
Student-wise
```

Now you can find information much more easily.

This is the basic idea behind managing facts and figures.

---

## 4. Two Important Requirements

### A. Store Permanently

Information should be stored so that it remains available for future use.

For example:

```text
Student ID: 458
Name: Basha
Age: 23
Marks: 93
```

Once stored, we should be able to use this information later.

---

### B. Retrieve Efficiently

**Retrieve** means **get/fetch the required information**.

For example, if a university has thousands of students and you want:

> "Give me the details of student ID 458."

The system should be able to find that information efficiently.

---

# 5. How was it managed in olden days?

In olden days, information was maintained using **ledgers**.

For example:

```text
----------------------------
Student Name : Basha
Age          : 23
Gender       : Male
Branch       : ECE
Student ID   : 458
Percentage   : 93
----------------------------
```

When the amount of information was small, this could be managed.

But when the amount of information became large, management became difficult.

---

# 6. Problem with Programming Languages

Programming languages can store information using variables.

For example:

```java
String name = "Basha";
int age = 23;
String gender = "Male";
String branch = "E.C.E";
int studentId = 458;
int percentage = 93;
```

For every fact or figure, we need to:

```text
Declare a variable
       ↓
Specify a data type
       ↓
Initialize the variable
```

This works for a **small volume of facts and figures**.

But imagine storing information about thousands or millions of students.

We would need a huge number of variables.

Therefore, programming languages alone become difficult for managing a **large volume of facts and figures**.

---

# 7. DBMS Came Into the Picture

To solve this problem, **DBMS (DataBase Management System)** came into the picture.

The basic flow is:

```text
Facts & Figures
      ↓
Small Volume
      ↓
Programming Languages
      ↓
Large Volume becomes difficult
      ↓
DBMS
      ↓
Database
      ↓
Large Volume of Facts & Figures
```

DBMS provides a way to manage large amounts of information.

---

# 8. Example

Suppose we have student information:

```text
Name       : Basha
Age        : 23
Gender     : Male
Branch     : ECE
Student ID : 458
Percentage : 93
```

This is a small amount of information.

Now imagine:

```text
Student 1
Student 2
Student 3
...
Student 10,000
```

Each student has:

```text
Name
Age
Gender
Branch
Student ID
Percentage
```

Now the amount of information becomes very large.

A **database and DBMS** help manage this large volume of facts and figures.

---

# 9. Important Rules

Remember these points:

### Rule 1

Management of facts and figures means properly handling information.

### Rule 2

Two important requirements are:

```text
Store Permanently
Retrieve Efficiently
```

### Rule 3

In olden days, information was managed using **ledgers**.

### Rule 4

Programming languages can successfully store a **small volume** of facts and figures.

### Rule 5

For every fact and figure in a programming language, we generally need a:

```text
Variable
+
Data Type
+
Initialization
```

### Rule 6

Programming languages become difficult for managing a **large volume** of facts and figures.

### Rule 7

**DBMS = DataBase Management System**

### Rule 8

DBMS came into the picture to manage large volumes of facts and figures.

---

# 10. Common Confusion

### Is storing information the only part of management?

No.

Management involves at least these two important activities in this topic:

```text
Store Permanently
        +
Retrieve Efficiently
```

### Why can't we simply use Java variables?

For a small amount of information, we can.

For example:

```java
String name = "Basha";
int age = 23;
```

But managing thousands or millions of records using individual variables becomes difficult.

---

# 11. Data → Database → DBMS

Keep these three concepts connected:

```text
DATA
↓
Facts & Figures
↓
Small Volume

DATABASE
↓
Large Volume of Facts & Figures

DBMS
↓
DataBase Management System
↓
Manages the Database
```

---

# 12. Interview Questions

### Q1. What is meant by management of facts and figures?

> It means storing facts and figures permanently and retrieving them efficiently.

### Q2. What are the two important requirements for managing facts and figures?

> **Store permanently** and **retrieve efficiently**.

### Q3. How was data managed in olden days?

> Data was managed using **ledgers**.

### Q4. Why did programming languages become difficult for managing large volumes of data?

> Because for every fact and figure, we need to declare a variable, specify a data type, and perform initialization. Managing a large volume this way becomes difficult.

### Q5. Why did DBMS come into the picture?

> DBMS came into the picture when programming languages failed to manage large volumes of facts and figures effectively.

---

# 13. Interview-Ready Answer

If the interviewer asks:

**"What do you mean by management of facts and figures?"**

You can answer:

> **Management of facts and figures means storing information permanently and retrieving it efficiently. In olden days, information was managed using ledgers. Programming languages could manage a small volume of facts and figures, but managing a large volume became difficult. Therefore, DBMS came into the picture to manage large volumes of facts and figures.**

---

# 14. Practice Questions

1. What is meant by management of facts and figures?
2. What are the two important requirements of management?
3. What does "store permanently" mean?
4. What does "retrieve efficiently" mean?
5. How was information managed in olden days?
6. Why did programming languages become difficult for large volumes?
7. What three things are required for storing each fact using a programming language?
8. Why did DBMS come into the picture?
9. What is the full form of DBMS?
10. Explain the flow from programming languages to DBMS.

---

## 🧠 Memory Trick

Just remember:

```text
MANAGEMENT
     ↓
┌──────────────┐
│ STORE        │
│ PERMANENTLY  │
└──────────────┘
       +
┌──────────────┐
│ RETRIEVE     │
│ EFFICIENTLY  │
└──────────────┘
```

**One-line memory:**

> **Management of facts and figures = Store permanently + Retrieve efficiently.**
