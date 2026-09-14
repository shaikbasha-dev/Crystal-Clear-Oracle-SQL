# 15-LIKE-Operator

## 1. What is LIKE?

The `LIKE` operator is used to **search for a particular pattern in a character value**.

In simple words:

> **LIKE means: "Does this text follow this pattern?"**

For example:

```sql
WHERE f_name LIKE 'A%'
```

means:

> Find employees whose first name **starts with `A`**.

---

# 2. Why do we use LIKE?

Sometimes we don't know the complete value.

For example, we may know:

```text
A...
```

but we don't know the complete first name.

It could be:

```text
Akash
Ashwin
Andy
Adam
```

Instead of writing each name separately, we can use:

```sql
WHERE f_name LIKE 'A%'
```

---

# 3. Two Important Wildcards

The `LIKE` operator mainly uses these pattern characters:

| Symbol | Meaning                 |
| ------ | ----------------------- |
| `%`    | Zero or more characters |
| `_`    | Exactly one character   |

These two symbols are very important for understanding all the queries in this topic.

---

## `%` — Zero or More Characters

Example:

```sql
f_name LIKE 'A%'
```

Means:

```text
A
A + anything after A
```

So:

```text
Akash  → matches
Ashwin → matches
Andy   → matches
Adam   → matches
```

---

## `_` — Exactly One Character

Example:

```sql
f_name LIKE '_r%'
```

Here:

```text
_ → exactly one character
r → must be the second character
% → anything after that
```

So the pattern means:

```text
Any first character
+
r
+
anything after it
```

---

# 4. Question 1

### Question

**Write a query to display the details of employees whose first name starts with `A`.**

### Answer / Query

```sql
SELECT *
FROM emp
WHERE f_name LIKE 'A%';
```

### Explanation

Pattern:

```text
A%
```

means:

```text
A + zero or more characters
```

Therefore, names beginning with `A` are selected.

---

# 5. Question 2

### Question

**Write a query to display department id and department name where department name starts with `AC`.**

### Answer / Query

```sql
SELECT dept_id, dept_name
FROM dept
WHERE dept_name LIKE 'AC%';
```

### Explanation

Pattern:

```text
AC%
```

means:

```text
AC + anything after AC
```

So Oracle looks for department names beginning with `AC`.

---

# 6. Question 3

### Question

**Write a query to display manager id whose department id starts with `2`.**

### Answer / Query

```sql
SELECT manager_id
FROM emp
WHERE dept_id LIKE '2%';
```

### Explanation

Pattern:

```text
2%
```

means:

```text
2 + anything after 2
```

So the `DEPT_ID` values beginning with `2` match the pattern.

### Note

`DEPT_ID` is defined as a numeric column in the table, while `LIKE` is a pattern-matching operator generally used with character values. This query relies on Oracle's implicit conversion of the numeric value for the pattern comparison.

---

# 7. Question 4

### Question

**Write a query to display grades from the job grades table where low salary ends with `1`.**

### Answer / Query

```sql
SELECT grade
FROM j_grade
WHERE low_sal LIKE '%1';
```

### Explanation

Pattern:

```text
%1
```

means:

```text
Anything before 1
+
1 at the end
```

Therefore, `LOW_SAL` values ending with `1` are matched.

---

# 8. Question 5

### Question

**Write a query to display details of department whose department name ends with `ng`.**

### Answer / Query

```sql
SELECT *
FROM dept
WHERE dept_name LIKE '%ng';
```

### Explanation

Pattern:

```text
%ng
```

means:

```text
Anything before ng
+
ng at the end
```

So department names ending in `ng` are selected.

For example:

```text
Marketing
Shipping
Contracting
```

match this pattern.

---

# 9. Question 6

### Question

**Write a query to display department id and department name whose manager id ends with `0`.**

### Answer / Query

```sql
SELECT dept_id, dept_name
FROM dept
WHERE manager_id LIKE '%0';
```

### Explanation

Pattern:

```text
%0
```

means:

```text
Anything before 0
+
0 at the end
```

### Note

`MANAGER_ID` is numeric in the table, so this query also relies on implicit conversion for the `LIKE` comparison.

---

# 10. Question 7

### Question

**Write a query to display details of employee whose first name contains `an`.**

### Answer / Query

```sql
SELECT *
FROM emp
WHERE f_name LIKE '%an%';
```

### Explanation

Pattern:

```text
%an%
```

means:

```text
Anything
+
an
+
anything
```

So `an` can occur **anywhere inside the first name**.

For example:

```text
Prabhakaran
Daniel
Meghana
Madavan
```

contain `an`.

---

# 11. Question 8

### Question

**Write a query to display details of employees whose last name contains `am`.**

### Answer / Query

```sql
SELECT *
FROM emp
WHERE l_name LIKE '%am%';
```

### Explanation

Pattern:

```text
%am%
```

means:

```text
Anything
+
am
+
anything
```

So Oracle searches for `am` anywhere in `L_NAME`.

---

# 12. Question 9

### Question

**Write a query to display details of employees whose first name has `r` as the second character.**

### Answer / Query

```sql
SELECT *
FROM emp
WHERE f_name LIKE '_r%';
```

### Explanation

Pattern:

```text
_r%
```

Break it down:

```text
_ → first character can be anything
r → second character must be r
% → anything can come after it
```

So:

```text
First character → anything
Second character → r
Remaining       → anything
```

---

# 13. Question 10

### Question

**Write a query to display details of employees whose email has any two characters before `@`.**

### Answer / Query

```sql
SELECT *
FROM emp
WHERE email LIKE '__@%';
```

### Explanation

Pattern:

```text
__@%
```

Break it down:

```text
_ → first character
_ → second character
@ → @ must come next
% → anything after @
```

So the pattern represents:

```text
2 characters + @ + anything
```

---

# 14. Question 11

### Question

**Write a query to display details of employees whose last name ends with three characters after `n`.**

### Answer / Query

```sql
SELECT *
FROM emp
WHERE l_name LIKE '%n___';
```

### Explanation

Pattern:

```text
%n___
```

Break it down:

```text
%  → anything before n
n  → n
_  → one character
_  → one character
_  → one character
```

So the last name must have:

```text
anything + n + exactly 3 characters
```

---

# 15. Question 12

### Question

**Write a query to display phone numbers where the phone number has any characters before the last three-character pattern beginning after the `%`.**

### Answer / Query

```sql
SELECT phone_number
FROM emp
WHERE phone_number LIKE '%3__';
```

### Explanation

Pattern:

```text
%3__
```

means:

```text
% → anything before 3
3 → character 3
_ → exactly one character
_ → exactly one character
```

So the pattern ends with:

```text
3 + two characters
```

### Note

`PHONE_NUMBER` is a numeric column in the table. This query therefore relies on implicit conversion for the `LIKE` comparison.

---

# 16. Question 13

### Question

**Write a query to display last name and salary of employees whose last name contains exactly five characters.**

### Answer / Query

```sql
SELECT l_name, salary
FROM emp
WHERE l_name LIKE '_____';
```

### Explanation

There are **five underscores**:

```text
_ _ _ _ _
```

Each `_` represents exactly **one character**.

Therefore:

```text
_____ 
```

means:

> Exactly 5 characters.

For example:

```text
Singh → 5 characters
```

---

# 17. Understanding the `%` Wildcard

| Pattern  | Meaning        |
| -------- | -------------- |
| `'A%'`   | Starts with A  |
| `'%ng'`  | Ends with ng   |
| `'%an%'` | Contains an    |
| `'AC%'`  | Starts with AC |
| `'%1'`   | Ends with 1    |

### Easy memory

```text
A%    → STARTS with A
%ng   → ENDS with ng
%an%  → CONTAINS an
```

---

# 18. Understanding the `_` Wildcard

| Pattern   | Meaning                     |
| --------- | --------------------------- |
| `'_'`     | Exactly 1 character         |
| `'__'`    | Exactly 2 characters        |
| `'_____'` | Exactly 5 characters        |
| `'_r%'`   | `r` is the second character |
| `'__@%'`  | Two characters before `@`   |

### Easy memory

> **One `_` = One character**

```text
_     → 1 character
__    → 2 characters
___   → 3 characters
```

---

# 19. `%` vs `_`

This is one of the most important differences.

| Symbol | Meaning                 |
| ------ | ----------------------- |
| `%`    | Zero or more characters |
| `_`    | Exactly one character   |

Example:

```sql
WHERE f_name LIKE 'A%'
```

`A%` can match:

```text
A
Akash
Ashwin
Andy
Adam
```

But:

```sql
WHERE f_name LIKE 'A_'
```

means:

```text
A + exactly one character
```

---

# 20. LIKE Pattern Memory

Remember these four patterns:

```text
A%       → starts with A

%an%     → contains an

%ng      → ends with ng

_r%      → r is second character
```

This makes most `LIKE` questions easy to understand.

---

# 21. Common Mistakes

### Mistake 1 — Confusing `%` and `_`

```text
% → zero or more characters
_ → exactly one character
```

---

### Mistake 2 — Forgetting quotes

Correct:

```sql
WHERE f_name LIKE 'A%';
```

Because `A%` is a character pattern.

---

### Mistake 3 — Using `=` for pattern matching

❌

```sql
WHERE f_name = 'A%';
```

This does not perform wildcard pattern matching.

✅

```sql
WHERE f_name LIKE 'A%';
```

---

# 22. Interview Questions

### Q1. What is LIKE?

`LIKE` is used for pattern matching in SQL.

### Q2. What are the two important wildcards?

```text
% → zero or more characters
_ → exactly one character
```

### Q3. What does `LIKE 'A%'` mean?

The value starts with `A`.

### Q4. What does `LIKE '%an%'` mean?

The value contains `an`.

### Q5. What does `LIKE '%ng'` mean?

The value ends with `ng`.

### Q6. What does `LIKE '_r%'` mean?

The second character must be `r`.

### Q7. What does `LIKE '_____'` mean?

The value contains exactly five characters.

---

# 23. Complete Queries for LIKE

### Question 1

**Display details of employees whose first name starts with `A`.**

```sql
SELECT *
FROM emp
WHERE f_name LIKE 'A%';
```

### Question 2

**Display department id and department name where department name starts with `AC`.**

```sql
SELECT dept_id, dept_name
FROM dept
WHERE dept_name LIKE 'AC%';
```

### Question 3

**Display manager id whose department id starts with `2`.**

```sql
SELECT manager_id
FROM emp
WHERE dept_id LIKE '2%';
```

### Question 4

**Display grades where low salary ends with `1`.**

```sql
SELECT grade
FROM j_grade
WHERE low_sal LIKE '%1';
```

### Question 5

**Display details of departments whose department name ends with `ng`.**

```sql
SELECT *
FROM dept
WHERE dept_name LIKE '%ng';
```

### Question 6

**Display department id and department name whose manager id ends with `0`.**

```sql
SELECT dept_id, dept_name
FROM dept
WHERE manager_id LIKE '%0';
```

### Question 7

**Display details of employees whose first name contains `an`.**

```sql
SELECT *
FROM emp
WHERE f_name LIKE '%an%';
```

### Question 8

**Display details of employees whose last name contains `am`.**

```sql
SELECT *
FROM emp
WHERE l_name LIKE '%am%';
```

### Question 9

**Display details of employees whose first name has `r` as the second character.**

```sql
SELECT *
FROM emp
WHERE f_name LIKE '_r%';
```

### Question 10

**Display details of employees whose email has two characters before `@`.**

```sql
SELECT *
FROM emp
WHERE email LIKE '__@%';
```

### Question 11

**Display details of employees whose last name has `n` followed by three characters at the end.**

```sql
SELECT *
FROM emp
WHERE l_name LIKE '%n___';
```

### Question 12

**Display phone numbers matching the pattern `%3__`.**

```sql
SELECT phone_number
FROM emp
WHERE phone_number LIKE '%3__';
```

### Question 13

**Display last name and salary of employees whose last name has exactly five characters.**

```sql
SELECT l_name, salary
FROM emp
WHERE l_name LIKE '_____';
```

### Final memory

```text
LIKE
 │
 ├── % → Zero or more characters
 │
 └── _ → Exactly one character
```

```text
A%       → starts with A
%an%     → contains an
%ng      → ends with ng
_r%      → r is second character
_____    → exactly 5 characters
```
