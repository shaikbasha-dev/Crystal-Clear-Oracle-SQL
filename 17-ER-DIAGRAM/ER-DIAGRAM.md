# 17-ER-DIAGRAM

## 1. What is an ER Diagram?

**ER Diagram** means **Entity Relationship Diagram**.

It is a **diagrammatic representation of tables in a database**. 

In very simple words:

> **ER Diagram is a picture that shows what things exist in a database, their properties, and how those things are connected.**

For example, in a university database we may have:

```text
University
Student
Professor
Course
```

An ER Diagram helps us visually understand these things and their relationships.

---

# 2. Why do we need an ER Diagram?

Imagine someone tells you:

> "A university has students. Students enroll in courses. Professors teach courses."

If we write everything as sentences, it can become difficult to understand.

Instead, we can draw:

```text
University ─── has ─── Students

Professor ─── teaches ─── Course

Students ─── enroll ─── Course
```

Now the database design becomes much easier to understand.

---

# 3. Main Things in an ER Diagram

The important concepts covered here are:

```text
ER DIAGRAM
    │
    ├── Entity
    │    ├── Physical Entity
    │    └── Conceptual Entity
    │
    ├── Attribute
    │    ├── Simple Attribute
    │    ├── Single-Valued Attribute
    │    ├── Key Attribute
    │    ├── Derived Attribute
    │    ├── Composite Attribute
    │    └── Multi-Valued Attribute
    │
    ├── Weak Entity
    │
    ├── Strong Entity
    │
    ├── Relationship
    │
    ├── Types of Relationship
    │    ├── One-to-One
    │    ├── One-to-Many
    │    ├── Many-to-One
    │    └── Many-to-Many
    │
    ├── Cardinality Ratio
    │
    └── Steps to Draw ER Diagram
```

---

# 4. Entity

## What is an Entity?

> **Anything or any object which exists in the real world is called an Entity.** 

Examples:

```text
Student
Teacher
Employee
University
Course
Car
Person
```

An entity is basically a **thing about which we want to store information**.

---

# 5. Types of Entity

The two types given are:

```text
Entity
  │
  ├── Physical Entity
  │
  └── Conceptual Entity
```



---

## 5.1 Physical Entity

A **Physical Entity** is an entity that exists physically in the real world.

Examples given:

```text
Pen
Paper
Camera
```



### Easy understanding

You can physically see or touch:

```text
Pen
 ↓
Physical Entity
```

```text
Camera
 ↓
Physical Entity
```

---

## 5.2 Conceptual Entity

A **Conceptual Entity** is an entity that exists conceptually in the real world. 

Examples given include:

```text
Internet
Programming Languages
```

### Easy understanding

These are concepts rather than physical objects that you can hold.

```text
Internet
   ↓
Conceptual Entity
```

```text
Programming Language
   ↓
Conceptual Entity
```

---

# 6. How is an Entity Represented?

An Entity is represented using a:

**Rectangle**

The representation shown is:

```text
┌─────────────┐
│   Student   │
└─────────────┘
```

The rectangle represents the Entity. 

### Easy memory

> **Entity → Rectangle**

---

# 7. Attribute

## What is an Attribute?

> The **property that describes/decides an entity** is called an Attribute. 

For example:

```text
Student
```

can have:

```text
ID
Name
Age
Address
Marks
DOB
```

These are properties of Student.

So:

```text
Student → Entity

Name → Attribute
Age  → Attribute
Marks → Attribute
```

---

# 8. How is an Attribute Represented?

An Attribute is represented using an **ellipse (oval)**. 

Example:

```text
          ( Name )
             |
             |
      ┌─────────────┐
      │   Student   │
      └─────────────┘
```

### Easy memory

> **Attribute → Ellipse**

---

# 9. Entity + Attribute Diagram

A simple representation is:

```text
             (Name)
                |
                |
        (Age) ─ Student ─ (Marks)
                |
             (Address)
```

Or using the actual ER shapes:

```text
           ( Name )
               |
               |
        ┌─────────────┐
        │   Student   │
        └─────────────┘
               |
             ( Age )
```

---

# 10. Types of Attributes

The section covers:

```text
Attributes
    │
    ├── Simple Attribute
    │
    └── Composite Attribute
```

It then explains:

```text
Simple Attribute
    ├── Single-Valued Attribute
    ├── Key Attribute
    └── Derived Attribute

Composite Attribute
    └── Multi-Valued Attribute
```

The terminology in the source places “multi-valued” under the composite heading, while the earlier classification says simple/composite. That classification is internally inconsistent; the individual definitions and diagrams are preserved below rather than silently changing them.  

---

# 11. Simple Attribute

A **Simple Attribute** is an attribute that **cannot be further divided**. 

For example:

```text
Age
```

is treated as one value and is not divided into smaller attributes.

```text
Student
   |
 ( Age )
```

---

# 12. Single-Valued Attribute

A **Single-Valued Attribute** is an attribute that has **only one value**. 

For example:

```text
Student
   |
 ( Age )
```

A student has one age value at a particular point in time.

Another example:

```text
Student
   |
 ( Address )
```

---

# 13. Key Attribute

A **Key Attribute** represents the **primary key of the table**.

It helps us identify each row uniquely. 

For example:

```text
Student
   |
 ( Id )
```

If `Id` is the key:

```text
Student IDs:

101
102
103
104
```

Each student can be uniquely identified using the ID.

---

## Representation of Key Attribute

A Key Attribute is represented as an **ellipse with its text underlined**. 

Example:

```text
       __________
      (   Id     )
           |
           |
     ┌───────────┐
     │  Student  │
     └───────────┘
```

The underline indicates that `Id` is the key attribute.

### Easy memory

> **Key Attribute → Underlined ellipse**

---

# 14. Derived Attribute

A **Derived Attribute** is an attribute whose value is derived from another attribute. 

It is represented using a **dotted ellipse**. 

For example:

```text
DOB ───────→ Age
```

Age can be derived from Date of Birth.

Diagram:

```text
             ( DOB )
                |
                |
          . . . . . . .
         .     Age      .
          . . . . . . .
```

The dotted ellipse represents the derived attribute.

### Easy memory

> **Derived Attribute → Dotted Ellipse**

---

# 15. Attribute Examples Shown

The diagrams include examples such as:

```text
Student
   |
 ┌───────┬───────┬───────┐
 Id     marks    age
```

and:

```text
Student
   |
 address
```

The source also illustrates `Student → name` with `First`, `Middle`, and `Last`, showing how an attribute can be divided. 

---

# 16. Composite Attribute

A **Composite Attribute** is an attribute that **can be further divided**. 

The clearest example shown is:

```text
Name
 ├── First
 ├── Middle
 └── Last
```

So instead of treating:

```text
Name
```

as one indivisible item, it can be divided into:

```text
First Name
Middle Name
Last Name
```

### Diagram

```text
                  ( Name )
                 /   |    \
                /    |     \
        ( First ) ( Middle ) ( Last )
```

---

# 17. Multi-Valued Attribute

A **Multi-Valued Attribute** is an attribute that can have **more than one value**. 

For example:

```text
Student
   |
 Ph_no
```

A student may have multiple phone numbers.

```text
Student
   |
(( Ph_no ))
```

The diagram uses a double ellipse-style representation for the multi-valued attribute. The source labels the section under “Composite Attribute.” 

### Easy memory

> **Multi-valued → More than one value**

---

# 18. Important Attribute Symbols

| Concept                | Representation     |
| ---------------------- | ------------------ |
| Entity                 | Rectangle          |
| Attribute              | Ellipse            |
| Key Attribute          | Underlined ellipse |
| Derived Attribute      | Dotted ellipse     |
| Multi-Valued Attribute | Double ellipse     |

### Memory Trick

```text
Entity        → Box
Attribute     → Oval
Key           → Underlined Oval
Derived       → Dotted Oval
Multi-valued  → Double Oval
```

---

# 19. Strong Entity

A **Strong Entity** is an entity that **has its own key attribute**. 

It is represented using a **single rectangular box**. 

Example:

```text
       __________
      (   Id     )
           |
     ┌───────────┐
     │  Student  │
     └───────────┘
```

Here:

```text
Student
   ↓
has its own key
   ↓
Strong Entity
```

### Easy memory

> **Strong Entity → Own Key → Single Rectangle**

---

# 20. Weak Entity

A **Weak Entity** is an entity that **does not have its own key attribute**. 

It is **dependent on a Strong Entity**. 

A Weak Entity is represented using a **double rectangular box**. 

Diagram:

```text
Strong Entity             Weak Entity

┌──────────────┐         ╔══════════════╗
│   Employee   │─────────║  Dependent   ║
└──────────────┘         ╚══════════════╝
```

The source's example is:

```text
Employee ───────── Dependent
```

with Employee shown as the strong entity and Dependent as the weak entity. 

### Easy memory

```text
Strong Entity → Single Box
Weak Entity   → Double Box
```

---

# 21. Strong Entity vs Weak Entity

| Strong Entity                   | Weak Entity               |
| ------------------------------- | ------------------------- |
| Has its own key                 | Does not have its own key |
| Can be identified independently | Depends on Strong Entity  |
| Single rectangle                | Double rectangle          |
| Example: Employee               | Example: Dependent        |

### Super-easy memory

> **Strong = Own key**
> **Weak = Depends on another entity**

---

# 22. Relationship

## What is a Relationship?

> The **association between any two entities** is called a Relationship. 

For example:

```text
Driver ─── Drives ─── Car
```

Here:

```text
Driver → Entity
Car    → Entity
Drives → Relationship
```

---

# 23. How is a Relationship Represented?

A Relationship is represented using a **Rhombus (diamond)**. 

Example:

```text
┌──────────┐       ◇ Drives ◇       ┌──────────┐
│  Driver  │────────────────────────│   Car    │
└──────────┘                         └──────────┘
```

### Easy memory

> **Relationship → Diamond**

---

# 24. Types of Relationships

There are four types:

```text
1. One-to-One       (1:1)
2. One-to-Many      (1:M)
3. Many-to-One      (M:1)
4. Many-to-Many     (M:M)
```



---

# 25. One-to-One Relationship — 1:1

One entity occurrence is associated with **one** occurrence of another entity.

The example shown is:

```text
Person ─── have ─── Passport
```

with:

```text
1 : 1
```



### Diagram

```text
┌──────────┐      ◇ have ◇      ┌──────────┐
│  Person  │─────── 1 : 1 ──────│ Passport │
└──────────┘                     └──────────┘
```

### Meaning

```text
1 Person
   ↓
1 Passport
```

### Memory

> **1:1 = One ↔ One**

---

# 26. One-to-Many Relationship — 1:M

One occurrence of an entity can be associated with **many** occurrences of another entity.

The example shown is:

```text
Teachers ─── Teacher ─── Students
```

with:

```text
1 : M
```



### Diagram

```text
┌───────────┐      ◇ Teacher ◇      ┌───────────┐
│ Teachers  │─────── 1 : M ─────────│ Students  │
└───────────┘                        └───────────┘
```

### Meaning

```text
1 Teacher
   ↓
Many Students
```

### Memory

> **1:M = One → Many**

---

# 27. Many-to-One Relationship — M:1

Many occurrences of one entity are associated with **one** occurrence of another entity.

The example shown is:

```text
Employees ─── Works ─── Company
```

with:

```text
M : 1
```



### Diagram

```text
┌───────────┐       ◇ Works ◇       ┌──────────┐
│ Employees │─────── M : 1 ─────────│ Company  │
└───────────┘                        └──────────┘
```

### Meaning

```text
Many Employees
      ↓
   1 Company
```

### Memory

> **M:1 = Many → One**

---

# 28. Many-to-Many Relationship — M:M

Many occurrences of one entity can be associated with **many** occurrences of another entity.

The relationship type is:

```text
M : M
```



A simple representation:

```text
┌───────────┐       ◇ Relationship ◇       ┌───────────┐
│ Entity A  │────────── M : M ─────────────│ Entity B  │
└───────────┘                              └───────────┘
```

### Meaning

```text
Many A
  ↕
Many B
```

### Easy memory

> **M:M = Many ↔ Many**

---

# 29. Relationship Types — One View

```text
1 : 1
One  → One

1 : M
One  → Many

M : 1
Many → One

M : M
Many → Many
```

| Relationship | Simple Meaning                |
| ------------ | ----------------------------- |
| 1:1          | One entity ↔ One entity       |
| 1:M          | One entity → Many entities    |
| M:1          | Many entities → One entity    |
| M:M          | Many entities ↔ Many entities |

---

# 30. Cardinality Ratio

The numbers:

```text
1 : 1
1 : M
M : 1
M : M
```

show **how many instances of one entity can be associated with another entity**.

This is the **Cardinality Ratio**.

It is one of the four steps specifically given for drawing an ER Diagram. 

---

# 31. Complete Basic ER Diagram

Now combine:

* Entity
* Attribute
* Relationship
* Cardinality

Example:

```text
                    ( Id )
                      |
               ┌────────────┐
               │  Student   │
               └────────────┘
                      |
                      | M
                      |
                 ◇ Enroll ◇
                      |
                      | M
                      |
               ┌────────────┐
               │   Course   │
               └────────────┘
```

This tells us:

```text
Student → Entity
Course  → Entity
Enroll  → Relationship
M : M    → Cardinality
```

---

# 32. Steps to Draw an ER Diagram

There are exactly **four steps**:

```text
1. Identify the Entities.
2. Identify the Attributes.
3. Identify the Relationship.
4. Identify the Cardinality Ratio.
```



### Easy memory:

```text
E → A → R → C

Entity
Attribute
Relationship
Cardinality
```

---

# 33. Case Study — University Database

The case study describes a **University Database**.

The requirements are:

> In a university, students enroll into courses. A student may be assigned to at least one course. Each course is taught by a single professor. To maintain institution quality, a professor can teach only one course. 

Let's understand this sentence slowly.

---

## 34. Identify the Entities

From the case study, the main entities are:

```text
University
Student
Professor
Course
```

The diagram represents these as rectangles.

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

---

# 35. University Attributes

The University entity has:

```text
Uid
Uname
Uloc
```

The diagram shows:

```text
             ( Uid )
                |
       ( Uname ) | ( Uloc )
             \   |   /
          ┌────────────┐
          │ University │
          └────────────┘
```

These attributes are shown in the University portion of the ER schema. 

---

# 36. Student Attributes

The Student entity has:

```text
Sid
Sname
Fname
Lname
marks
DOB
Age
```

The diagram also shows `Age` as a **dotted ellipse**, indicating a derived attribute. 

A simplified reconstruction:

```text
                 ( Sid )
                    |
               ( Sname )
                    |
            ┌─────────────┐
            │   Student   │
            └─────────────┘
              /    |    \
          (Fname)(Lname)(marks)
                       \
                      (DOB)
                        |
                   . . . . .
                  .   Age   .
                   . . . . .
```

---

# 37. Professor Attributes

The Professor entity has:

```text
Pid
Pname
salary
Ph no
```

The diagram shows these connected to Professor. 

Simplified:

```text
          ( Pid )
             |
          ( Pname )
             |
       ┌────────────┐
       │ Professor  │
       └────────────┘
          /       \
     (salary)   (Ph no)
```

---

# 38. Course Attributes

The Course entity has:

```text
Cid
Cname
Cdur
Cfee
```



Simplified:

```text
             ( Cid )
                |
            ( Cname )
                |
          ┌──────────┐
          │  Course  │
          └──────────┘
             /    \
         (Cdur)  (Cfee)
```

---

# 39. University Relationships

The University ER schema contains these relationships:

```text
University ─── have ─── Person/Passport
University ─── has ─── Students
University ─── Works in ─── Professor
Students ─── Enroll to ─── Course
Professor ─── teach ─── Course
```

The exact schema labels and cardinalities are shown in the case-study diagram. 

---

# 40. Main University ER Schema — Simplified Diagram

Here is the complete structure represented in an easy-to-read form:

```text
                         ┌────────────┐
                         │ University │
                         └────────────┘
                          /    |     \
                       Uid   Uname   Uloc
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
                    /   |    \
                  Sid Sname  marks
                       |
                 Fname/Lname
                       |
                      DOB
                       |
                  . . . . .
                 .    Age   .
                  . . . . .

                         Student
                            |
                            | M
                            |
                       ◇ Enroll ◇
                            |
                            | M
                            |
                         Course
```

The source's actual page diagram additionally shows the University–Professor and Professor–Course relationships and the corresponding attributes. 

---

# 41. Professor–Course Relationship

The case study says:

> Each course is taught by a single professor.

The diagram shows:

```text
Professor ─── teach ─── Course
    1                    1
```

So:

```text
┌───────────┐       ◇ teach ◇       ┌────────┐
│ Professor │────────── 1 : 1 ──────│ Course │
└───────────┘                       └────────┘
```

The ER schema shows `1` on both sides of the `teach` relationship. 

---

# 42. Student–Course Relationship

The case study says:

> Students enroll into courses.

The diagram shows:

```text
Student ─── Enroll to ─── Course
   M                         M
```

So:

```text
┌─────────┐       ◇ Enroll to ◇       ┌────────┐
│ Student │────────── M : M ──────────│ Course │
└─────────┘                            └────────┘
```

The case-study diagram shows `M` on the Student side and `M` on the Course side. 

---

# 43. University–Professor Relationship

The diagram shows:

```text
University ─── Works in ─── Professor
      1                      M
```

So:

```text
┌────────────┐       ◇ Works in ◇       ┌───────────┐
│ University │────────── 1 : M ─────────│ Professor │
└────────────┘                           └───────────┘
```

This represents the relationship shown in the case-study ER schema. 

---

# 44. Complete Case Study at a Glance

```text
                         UNIVERSITY
                       /      |       \
                    Uid     Uname     Uloc
                      |
                      | 1
                      |
                  ◇ has ◇
                      |
                      | M
                      |
                   STUDENT
              /       |       \
           Sid      Sname     marks
                       |
                 Fname/Lname
                       |
                      DOB
                       |
                  . . . . .
                 .    Age   .
                  . . . . .
                      |
                      | M
                 ◇ Enroll to ◇
                      |
                      | M
                      |
                    COURSE
                  /   |    \
               Cid Cname   Cdur
                          Cfee

UNIVERSITY
     |
     | 1
  ◇ Works in ◇
     | M
     |
 PROFESSOR
 /    |      \
Pid  Pname  salary
       \
      Ph no

PROFESSOR
     |
     | 1
  ◇ teach ◇
     | 1
     |
   COURSE
```

This combines the entities, attributes, relationships, and cardinalities represented in the case-study ER schema. 

---

# 45. Symbols — Must Remember

| ER Component           | Shape              |
| ---------------------- | ------------------ |
| Entity                 | ▭ Rectangle        |
| Weak Entity            | Double Rectangle   |
| Attribute              | ○ Ellipse          |
| Key Attribute          | Underlined Ellipse |
| Derived Attribute      | Dotted Ellipse     |
| Multi-Valued Attribute | Double Ellipse     |
| Relationship           | ◇ Diamond/Rhombus  |

### Visual memory

```text
ENTITY
┌───────────┐
│  Student  │
└───────────┘


ATTRIBUTE
   ( Name )


KEY ATTRIBUTE
  ( Id )
  ─────


DERIVED ATTRIBUTE
 . . . . .
.   Age   .
 . . . . .


RELATIONSHIP
  ◇ Enroll ◇


WEAK ENTITY
╔═══════════╗
║ Dependent ║
╚═══════════╝
```

---

# 46. Most Important Differences

## Entity vs Attribute

| Entity              | Attribute             |
| ------------------- | --------------------- |
| Thing/object        | Property of the thing |
| Rectangle           | Ellipse               |
| Example: Student    | Example: Name         |
| Can have attributes | Describes an entity   |

```text
Student → Entity
Name    → Attribute
```

---

## Strong Entity vs Weak Entity

| Strong                     | Weak                     |
| -------------------------- | ------------------------ |
| Has own key                | No own key               |
| Independent identification | Depends on Strong Entity |
| Single rectangle           | Double rectangle         |

---

## Simple vs Composite Attribute

| Simple                    | Composite              |
| ------------------------- | ---------------------- |
| Cannot be further divided | Can be further divided |
| Example: Age              | Example: Name          |
| One unit                  | Can have components    |

Example:

```text
Age
 ↓
Simple
```

```text
Name
 ├── First
 ├── Middle
 └── Last
 ↓
Composite
```

---

## `:1` vs `:M`

```text
1 → One
M → Many
```

Therefore:

```text
1:1 → One to One
1:M → One to Many
M:1 → Many to One
M:M → Many to Many
```

---

# 47. Complete Memory Map

```text
                    ER DIAGRAM
                        │
        ┌───────────────┼────────────────┐
        ↓               ↓                ↓
     ENTITY          ATTRIBUTE       RELATIONSHIP
        │               │                │
   ┌────┴────┐      ┌───┴────┐       Diamond
   ↓         ↓      ↓        ↓
Physical  Conceptual Simple  Composite
                         │
                  ┌──────┼─────────┐
                  ↓      ↓         ↓
               Single   Key     Derived
               Value
                                   ↓
                              Dotted Ellipse

Entity
  │
  ├── Strong → Single Rectangle
  └── Weak   → Double Rectangle

Relationship
  │
  ├── 1:1
  ├── 1:M
  ├── M:1
  └── M:M
```

---

# 48. Four Steps — Final Memory

Whenever you are asked:

> **"How do you draw an ER Diagram?"**

Answer:

```text
Step 1 → Identify Entities
Step 2 → Identify Attributes
Step 3 → Identify Relationships
Step 4 → Identify Cardinality Ratio
```



### Super-easy shortcut:

> **E → A → R → C**

**Entity → Attribute → Relationship → Cardinality**

---

# 49. Interview Questions

### Q1. What is an ER Diagram?

**Answer:**
An ER Diagram is a diagrammatic representation of tables in a database.

### Q2. What is an Entity?

**Answer:**
An entity is anything or any object that exists in the real world.

### Q3. What are the two types of Entity?

**Answer:**

```text
1. Physical Entity
2. Conceptual Entity
```

### Q4. How is an Entity represented?

**Answer:**
Using a rectangular box.

### Q5. What is an Attribute?

**Answer:**
An attribute is a property that describes an entity.

### Q6. How is an Attribute represented?

**Answer:**
Using an ellipse.

### Q7. What is a Key Attribute?

**Answer:**
A Key Attribute represents the primary key and helps uniquely identify each row.

### Q8. How is a Key Attribute represented?

**Answer:**
Using an ellipse with the attribute text underlined.

### Q9. What is a Derived Attribute?

**Answer:**
An attribute derived from another attribute.

### Q10. How is a Derived Attribute represented?

**Answer:**
Using a dotted ellipse.

### Q11. What is a Weak Entity?

**Answer:**
An entity that does not have its own key attribute and depends on a Strong Entity.

### Q12. How is a Weak Entity represented?

**Answer:**
Using a double rectangular box.

### Q13. What is a Strong Entity?

**Answer:**
An entity that has its own key attribute.

### Q14. What is a Relationship?

**Answer:**
An association between two entities.

### Q15. How is a Relationship represented?

**Answer:**
Using a rhombus/diamond.

### Q16. What are the four types of Relationship?

**Answer:**

```text
1. One-to-One       (1:1)
2. One-to-Many      (1:M)
3. Many-to-One      (M:1)
4. Many-to-Many     (M:M)
```

### Q17. What are the steps to draw an ER Diagram?

**Answer:**

```text
1. Identify Entities
2. Identify Attributes
3. Identify Relationship
4. Identify Cardinality Ratio
```

---

# 50. One-Minute Revision

```text
ER DIAGRAM
    ↓
Picture of database design
    ↓
ENTITY
    ↓
Rectangle
    ↓
ATTRIBUTE
    ↓
Ellipse
    ↓
KEY
    ↓
Underlined Ellipse
    ↓
DERIVED
    ↓
Dotted Ellipse
    ↓
WEAK ENTITY
    ↓
Double Rectangle
    ↓
RELATIONSHIP
    ↓
Diamond
    ↓
CARDINALITY
    ↓
1:1 / 1:M / M:1 / M:M
```

### The five shapes/rules you should never forget:

```text
Rectangle       → Entity
Double Rectangle→ Weak Entity
Ellipse         → Attribute
Dotted Ellipse  → Derived Attribute
Diamond         → Relationship
```

### And the four drawing steps:

```text
E → A → R → C

Entity
Attribute
Relationship
Cardinality
```
