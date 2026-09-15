# 18-ER-SCHEMA

## 1. What is an ER Schema?

**ER Schema** is the actual structure/design of the database represented using an **ER Diagram**.

Think of it like this:

```text
ER Diagram
   ↓
Picture of the database design
   ↓
ER Schema
   ↓
Shows Entities + Attributes + Relationships + Cardinality
```

The University Database case study gives a complete ER Schema containing:

```text
University
Student
Professor
Course
```

along with their attributes and relationships. 

---

# 2. University Database — Problem

The case study describes a university where:

* Students enroll into courses.
* A student may be assigned to at least one course.
* Each course is taught by a single professor.
* A professor can teach only one course. 

Now we convert these requirements into an ER Schema.

---

# 3. Step 1 — Identify Entities

First ask:

> **What are the important things in this system?**

We get:

```text
University
Student
Professor
Course
```

So:

```text
┌────────────┐
│ University │
└────────────┘

┌─────────┐
│ Student │
└─────────┘

┌───────────┐
│ Professor │
└───────────┘

┌────────┐
│ Course │
└────────┘
```

These are the main entities in the University ER Schema. 

---

# 4. Step 2 — Identify Attributes

Now ask:

> **What information do we need to store about each entity?**

---

## University

University has:

```text
Uid
Uname
Uloc
```

Diagram:

```text
             (Uid)
               |
            ┌───────┐
            │       │
      (Uname) University (Uloc)
            │       │
            └───────┘
```

The University section lists `Uid`, `Uname`, and `Uloc`. 

---

# 5. Student

Student has:

```text
Sid
Sname
Fname
Lname
marks
DOB
Age
```

The schema shows `Age` using a **dotted ellipse**, meaning it is a derived attribute. 

Simple representation:

```text
                    (Sid)
                       |
                  (Sname)
                       |
                  ┌─────────┐
                  │ Student │
                  └─────────┘
                  /    |     \
              (marks) (DOB)  (Age)
                              . . . .
                             .      .
                             . Age  .
                             . . . .
```

The name-related attributes are also represented with:

```text
Sname
 ├── Fname
 └── Lname
```

---

# 6. Professor

Professor has:

```text
Pid
Pname
salary
Ph no
```

Diagram:

```text
             (Pid)
               |
            (Pname)
               |
        ┌────────────┐
        │ Professor  │
        └────────────┘
          /        \
      (salary)   (Ph no)
```

These attributes are shown in the Professor portion of the schema. 

---

# 7. Course

Course has:

```text
Cid
Cname
Cdur
Cfee
```

Diagram:

```text
             (Cid)
               |
            (Cname)
               |
          ┌─────────┐
          │ Course  │
          └─────────┘
             /   \
          (Cdur) (Cfee)
```

These are the Course attributes shown in the schema. 

---

# 8. Step 3 — Identify Relationships

Now ask:

> **How are these entities connected?**

The University schema shows relationships such as:

```text
University ─── has ─── Student

University ─── Works in ─── Professor

Student ─── Enroll to ─── Course

Professor ─── teach ─── Course
```

The relationships are represented using **diamond/rhombus shapes**.  

---

# 9. University → Student

The schema shows:

```text
University ─── has ─── Student
```

with:

```text
1 : M
```

So we can understand it as:

```text
             1
University ────◇ has ◇──── M ─── Student
```

### Simple meaning

One University can have many Students.

```text
1 University
      ↓
Many Students
```

---

# 10. University → Professor

The schema shows:

```text
University ─── Works in ─── Professor
```

with:

```text
1 : M
```

Diagram:

```text
                 1              M
University ─────◇ Works in ◇──── Professor
```

### Simple meaning

```text
1 University
      ↓
Many Professors
```

---

# 11. Student → Course

The case study says:

> Students enroll into courses.

The schema shows:

```text
Student ─── Enroll to ─── Course
```

with:

```text
M : M
```

Diagram:

```text
                 M              M
Student ───────◇ Enroll to ◇──── Course
```

### Simple meaning

Many students can enroll in many courses.

```text
Student 1 ─── Course A
Student 1 ─── Course B
Student 2 ─── Course A
Student 2 ─── Course C
```

Therefore:

```text
Student ↔ Course
   M       M
```

The schema shows `M` on both sides of the `Enroll to` relationship. 

---

# 12. Professor → Course

The case study says:

> Each course is taught by a single professor.

The schema shows:

```text
Professor ─── teach ─── Course
```

with:

```text
1 : 1
```

Diagram:

```text
                 1              1
Professor ───────◇ teach ◇────── Course
```

### Simple meaning

```text
1 Professor
     ↓
1 Course
```

and the schema represents the relationship as `1 : 1`. 

---

# 13. Complete University ER Schema

Now let's put everything together.

```text
                              UNIVERSITY
                         ┌────────────────┐
                         │   University   │
                         └────────────────┘
                           /      |       \
                       (Uid)   (Uname)   (Uloc)
                           |
                           | 1
                           |
                       ◇ has ◇
                           |
                           | M
                           |
                       ┌─────────┐
                       │ Student │
                       └─────────┘
                       /    |     \
                    (Sid) (Sname) (marks)
                             |
                       ┌─────┴─────┐
                    (Fname)     (Lname)
                             |
                           (DOB)
                             |
                       . . . . . .
                      .    (Age)   .
                       . . . . . .

                           Student
                              |
                              | M
                         ◇ Enroll to ◇
                              |
                              | M
                              |
                          ┌────────┐
                          │ Course │
                          └────────┘
                         /    |     \
                     (Cid) (Cname) (Cdur)
                                      |
                                    (Cfee)


UNIVERSITY
     |
     | 1
     |
 ◇ Works in ◇
     |
     | M
     |
┌───────────┐
│ Professor │
└───────────┘
 /    |      \
(Pid)(Pname)(salary)
               |
             (Ph no)


PROFESSOR
     |
     | 1
     |
 ◇ teach ◇
     |
     | 1
     |
  COURSE
```

This is a simplified text reconstruction of the University ER Schema shown on the page. 

---

# 14. The Actual Schema Logic

The complete relationship structure can be remembered as:

```text
                 UNIVERSITY
                 /        \
              1 /          \ 1
               /            \
              M              M
         STUDENT          PROFESSOR
             |                |
             | M              | 1
             |                |
             |                |
             M                1
           COURSE ←───────────
```

More clearly:

```text
University
    │
    ├── 1 : M ──→ Student
    │
    └── 1 : M ──→ Professor

Student
    │
    └── M : M ──→ Course

Professor
    │
    └── 1 : 1 ──→ Course
```

---

# 15. Why are `1` and `M` Important?

They tell us **how many** entities can participate in the relationship.

```text
1 = One
M = Many
```

Therefore:

```text
1 : 1 → One to One
1 : M → One to Many
M : 1 → Many to One
M : M → Many to Many
```

The four relationship types are explicitly listed in the ER section. 

---

# 16. Understanding the University Schema Like a Story

Don't try to memorize the whole diagram at once.

Read it as a story:

### Step 1

```text
University
    ↓
has
    ↓
Students
```

### Step 2

```text
University
    ↓
Works in
    ↓
Professors
```

### Step 3

```text
Students
    ↓
Enroll to
    ↓
Courses
```

### Step 4

```text
Professors
    ↓
teach
    ↓
Courses
```

So the whole database story is:

> **A University has Students and Professors. Students enroll in Courses. Professors teach Courses.**

---

# 17. Attributes in One Table

| Entity     | Attributes                                |
| ---------- | ----------------------------------------- |
| University | Uid, Uname, Uloc                          |
| Student    | Sid, Sname, Fname, Lname, marks, DOB, Age |
| Professor  | Pid, Pname, salary, Ph no                 |
| Course     | Cid, Cname, Cdur, Cfee                    |

These are the attributes represented in the University schema. 

---

# 18. Relationships in One Table

| Relationship | Entities               | Cardinality |
| ------------ | ---------------------- | ----------- |
| has          | University → Student   | 1:M         |
| Works in     | University → Professor | 1:M         |
| Enroll to    | Student → Course       | M:M         |
| teach        | Professor → Course     | 1:1         |

The case-study diagram supplies these relationship names and cardinalities. 

---

# 19. Important Attributes in the Schema

### Student

```text
Sid
```

is the key-type attribute representing the student's identity.

### University

```text
Uid
```

identifies the university.

### Professor

```text
Pid
```

identifies the professor.

### Course

```text
Cid
```

identifies the course.

The schema visually distinguishes key-style attributes using the ER attribute notation. 

---

# 20. Derived Attribute in the Schema

The Student entity contains:

```text
DOB
Age
```

The diagram represents:

```text
Age
```

using a **dotted ellipse**. 

Why?

Because:

```text
DOB
 ↓
Age
```

Age can be obtained from the Date of Birth.

So:

```text
DOB = stored information
Age = derived information
```

---

# 21. How to Draw This ER Schema in an Exam

Follow these four steps:

```text
1. Identify Entities
        ↓
2. Identify Attributes
        ↓
3. Identify Relationships
        ↓
4. Identify Cardinality Ratio
```

These are the four drawing steps given in the section. 

For this University case:

```text
Entities:
University
Student
Professor
Course

Relationships:
has
Works in
Enroll to
teach

Cardinality:
1:M
1:M
M:M
1:1
```

---

# 22. Final Exam-Friendly ER Schema

```text
                         ┌────────────┐
                         │ University │
                         └────────────┘
                           /   |    \
                        Uid Uname  Uloc
                           |
                           | 1
                        ◇ has ◇
                           |
                           | M
                           |
                     ┌───────────┐
                     │  Student  │
                     └───────────┘
                    /   |    |    \
                  Sid Sname marks DOB
                       / \
                    Fname Lname
                          |
                       . . . .
                      .  Age  .
                       . . . .
                          |
                          | M
                    ◇ Enroll to ◇
                          |
                          | M
                          |
                     ┌─────────┐
                     │ Course  │
                     └─────────┘
                    /    |     \
                  Cid  Cname   Cdur
                              Cfee


        ┌────────────┐
        │ University │
        └────────────┘
               |
               | 1
          ◇ Works in ◇
               | M
               |
        ┌────────────┐
        │ Professor  │
        └────────────┘
         /    |      \
       Pid  Pname   salary
                       |
                     Ph no
               |
               | 1
           ◇ teach ◇
               | 1
               |
            Course
```

## ⭐ Final Memory Trick

```text
ENTITY       → Rectangle
ATTRIBUTE    → Ellipse
RELATIONSHIP → Diamond
KEY          → Underlined
DERIVED      → Dotted ellipse

1 → One
M → Many
```

And for the University case:

```text
University ──1:M── Student
University ──1:M── Professor
Student    ──M:M── Course
Professor  ──1:1── Course
```

That is the **core ER Schema** you should be able to draw and explain without looking at the diagram.
