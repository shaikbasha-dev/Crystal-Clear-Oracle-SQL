# 16-ESCAPE-with-LIKE

## 1. What is ESCAPE with LIKE?

Normally, `%` and `_` have a **special meaning** in a `LIKE` pattern.

```text
% → zero or more characters
_ → exactly one character
```

But sometimes we want to search for the **actual `%` or `_` character** present in the data.

For that situation, we use the `ESCAPE` clause.

> **ESCAPE tells Oracle which character should be treated as an escape character.**

---

# 2. Why do we need ESCAPE?

Suppose a name is actually stored as:

```text
Sahana_varma
```

Here `_` is an actual character in the name.

But if we write:

```sql
WHERE name LIKE '%_%'
```

Oracle treats `_` as a wildcard.

It does **not** mean "find an actual underscore."

To search for the actual `_`, we can choose `?` as the escape character:

```sql
WHERE name LIKE '%?_%' ESCAPE '?'
```

Here:

```text
?_
```

means:

> Treat `_` as a normal/actual underscore character.

---

# 3. Syntax

```sql
SELECT column_name
FROM table_name
WHERE column_name LIKE 'pattern' ESCAPE 'escape_character';
```

Example:

```sql
SELECT name
FROM college_student
WHERE name LIKE '%?_%' ESCAPE '?';
```

Here:

```text
? → escape character
_ → actual underscore
```

---

# 4. Understanding the ESCAPE Character

In the queries here, `?` is chosen as the escape character.

```sql
ESCAPE '?'
```

means:

> Whenever `?` appears immediately before a special LIKE character, treat that special character literally.

For example:

```text
?_ 
```

means:

```text
actual _
```

And:

```text
?%
```

means:

```text
actual %
```

---

# 5. Table Used for the Examples

The examples create a small table:

```sql id="9nq8xs"
CREATE TABLE college_student (
    id VARCHAR2(54),
    name VARCHAR2(54)
);
```

Then records are inserted:

```sql id="d2g7k4"
INSERT INTO college_student
VALUES ('Kod001', 'Sahana_varma');

INSERT INTO college_student
VALUES ('Kod002', 'Sindhu_sharma');

INSERT INTO college_student
VALUES ('Kod003', 'Swathi%hegde');

INSERT INTO college_student
VALUES ('Kod004', 'Shruthi');
```

Notice that two special characters are actually stored in the `NAME` column:

```text
Sahana_varma
      ↑
      _

Swathi%hegde
      ↑
      %
```

These are the characters we want to search for.

---

# 6. Question 1

### Question

**Write a query to display names containing an actual underscore `_`.**

### Answer / Query

```sql id="s7f1q2"
SELECT name
FROM college_student
WHERE name LIKE '%?_%' ESCAPE '?';
```

---

## 7. How does this query work?

Look carefully at:

```sql id="c3k8v5"
'%?_%'
```

Break it down:

```text
%   → anything before
?_  → actual underscore
%   → anything after
```

So:

```text
%? _ %
   ↑
   |
actual underscore
```

The `?` tells Oracle:

> "Do not treat the following `_` as a wildcard."

Therefore:

```text
Sahana_varma → ✅
Sindhu_sharma → ✅
Swathi%hegde → ❌
Shruthi       → ❌
```

---

# 8. Question 2

### Question

**Write a query to display names containing an actual percentage `%`.**

### Answer / Query

```sql id="e4p9m6"
SELECT name
FROM college_student
WHERE name LIKE '%?%%' ESCAPE '?';
```

---

## 9. How does this query work?

Look carefully at:

```sql id="n2w7c8"
'%?%%'
```

Break it down:

```text
%    → anything before
?%   → actual %
%    → anything after
```

So:

```text
% ? % %
  ↑
  |
actual percentage character
```

The first `%` and last `%` are wildcards.

The `%` immediately after `?` is treated as an **actual percentage character**.

Therefore:

```text
Swathi%hegde → ✅
Sahana_varma → ❌
Sindhu_sharma → ❌
Shruthi       → ❌
```

---

# 10. Why can't we simply use `%` and `_`?

Because `%` and `_` have special meanings in `LIKE`.

### `%`

```text
Zero or more characters
```

### `_`

```text
Exactly one character
```

So if `%` or `_` itself is stored in the data and we want to search for that actual character, we need an escape character.

---

# 11. `%` vs `?%`

This is very important.

### `%`

```text
%
```

means:

> Zero or more characters.

### `?%` with `ESCAPE '?'`

```text
?%
```

means:

> The actual `%` character.

Similarly:

### `_`

```text
_
```

means:

> Exactly one character.

### `?_` with `ESCAPE '?'`

```text
?_
```

means:

> The actual `_` character.

---

# 12. Simple Visual Understanding

Suppose:

```text
Sahana_varma
```

We want to find the actual `_`.

Use:

```sql
LIKE '%?_%' ESCAPE '?'
```

Think:

```text
%     ?_      %
↓      ↓      ↓
anything  actual  anything
          _
```

---

Suppose:

```text
Swathi%hegde
```

We want to find the actual `%`.

Use:

```sql
LIKE '%?%%' ESCAPE '?'
```

Think:

```text
%     ?%      %
↓      ↓      ↓
anything actual  anything
          %
```

---

# 13. Important Rules

### Rule 1

`ESCAPE` is used together with `LIKE` when we need to treat a wildcard character as a literal character.

### Rule 2

The escape character can be chosen by us.

In these examples:

```sql
ESCAPE '?'
```

So `?` is the escape character.

### Rule 3

To search for an actual underscore:

```sql
LIKE '%?_%' ESCAPE '?'
```

### Rule 4

To search for an actual percentage character:

```sql
LIKE '%?%%' ESCAPE '?'
```

### Rule 5

Without `ESCAPE`, `_` and `%` retain their normal wildcard meanings.

---

# 14. Common Confusion

### `_` vs `?_`

Without ESCAPE:

```text
_
```

means:

> Any one character.

With:

```sql
ESCAPE '?'
```

the pattern:

```text
?_
```

means:

> Actual underscore `_`.

---

### `%` vs `?%`

Without ESCAPE:

```text
%
```

means:

> Zero or more characters.

With:

```sql
ESCAPE '?'
```

the pattern:

```text
?%
```

means:

> Actual percentage character `%`.

---

# 15. Interview Questions

### Q1. Why do we use ESCAPE with LIKE?

To search for `%` or `_` as actual characters instead of treating them as wildcards.

### Q2. What does `ESCAPE '?'` mean?

It tells Oracle that `?` is the escape character in that `LIKE` pattern.

### Q3. What does `?_` represent?

With:

```sql
ESCAPE '?'
```

`?_` represents an actual underscore character.

### Q4. What does `?%` represent?

With:

```sql
ESCAPE '?'
```

`?%` represents an actual percentage character.

---

# 16. Complete Questions + Queries

### Question 1

**Write a query to display names containing an actual underscore `_`.**

```sql
SELECT name
FROM college_student
WHERE name LIKE '%?_%' ESCAPE '?';
```

### Question 2

**Write a query to display names containing an actual percentage `%`.**

```sql
SELECT name
FROM college_student
WHERE name LIKE '%?%%' ESCAPE '?';
```

---

## Final Memory Trick

```text
LIKE
 │
 ├── %  → zero or more characters
 │
 ├── _  → exactly one character
 │
 └── ESCAPE → search for % or _ themselves
```

With:

```sql
ESCAPE '?'
```

remember:

```text
?% → actual %
?_ → actual _
```

So the easiest memory line is:

> **ESCAPE = "Don't treat this wildcard as a wildcard."**
