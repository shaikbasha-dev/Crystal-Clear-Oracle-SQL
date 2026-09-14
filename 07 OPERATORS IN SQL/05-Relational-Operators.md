# 05-Relational-Operators

## What are Relational Operators?

**Relational operators** are used to **compare one value with another value**.

In very simple words:

> We use relational operators when we want to ask Oracle a comparison question.

For example:

```text id="w7f1py"
Is salary greater than 30000?
```

In SQL:

```sql id="yq8f3e"
WHERE salary > 30000
```

Here `>` is the relational operator.

Oracle checks every row and asks:

```text id="3y0b3j"
Is this employee's salary > 30000?
```

If the condition is satisfied, that row is included in the result.

---

# Relational Operators

The relational operators are:

```text id="7f2p4e"
=       Equal to
>       Greater than
<       Less than
>=      Greater than or equal to
<=      Less than or equal to
!=      Not equal to
<>      Not equal to
```

The notes list these seven forms. 

---

# 1. Equal To `=`

The `=` operator means:

> **Is this value equal to that value?**

Suppose:

```text id="6x9j7m"
f_name = 'Akash'
```

We are asking:

> "Is the employee's first name equal to Akash?"

### Query

```sql id="qv6j6e"
SELECT *
FROM emp
WHERE f_name = 'Akash';
```

### How Oracle thinks

For every employee:

```text
Akash       = Akash    → YES → display
Prabhakaran = Akash    → NO
DEEP        = Akash    → NO
...
```

So the matching employee is displayed. 

### Remember

```text id="3js8w0"
=  → Equal to
```

---

# 2. Greater Than `>`

The `>` operator means:

> **Is the value greater than this value?**

### Query

```sql id="jyq0kt"
SELECT *
FROM emp
WHERE dept_id > 30;
```

This means:

> "Display employees whose department ID is greater than 30."

For example:

```text id="8fj1n4"
dept_id = 21 → 21 > 30 → NO
dept_id = 22 → 22 > 30 → NO
dept_id = 110 → 110 > 30 → YES
```

So employees from departments such as `110` are displayed. 

### Remember

```text id="cc7a5q"
>  → Greater than
```

---

# 3. Less Than `<`

The `<` operator means:

> **Is the value smaller than this value?**

### Query

```sql id="8s3wzv"
SELECT *
FROM emp
WHERE salary < 10000;
```

This means:

> "Display employees whose salary is less than 10000."

Suppose:

```text id="2g98jb"
salary = 9500
```

Oracle checks:

```text id="8vl0kf"
9500 < 10000
      ↓
     YES
```

So that employee is displayed.

In the data used here, the employee with salary `9500` satisfies the condition. 

### Remember

```text id="h3b1m6"
<  → Less than
```

---

# 4. Greater Than or Equal To `>=`

The `>=` operator means:

> **Greater than OR exactly equal to.**

### Query

```sql id="b6k3n2"
SELECT email, phone_number
FROM emp
WHERE commission_pct >= 5;
```

This asks:

> "Is the commission percentage 5 or greater than 5?"

So both are accepted:

```text id="4h4a4m"
5       → YES
6       → YES
10      → YES
```

But:

```text id="a1x8cz"
4.9 → NO
```

The query in the material produces no data with the supplied data. 

### Remember

```text id="f3myx6"
>=  → Greater than OR equal to
```

---

# 5. Less Than or Equal To `<=`

The `<=` operator means:

> **Less than OR exactly equal to.**

### Query

```sql id="p8r0xq"
SELECT email, f_name, l_name
FROM emp
WHERE salary <= 34000;
```

This means:

> "Display employees whose salary is 34000 or less."

For example:

```text id="0kz5oz"
salary = 34000 → YES
salary = 30000 → YES
salary = 12000 → YES
salary = 35000 → NO
```

The supplied data includes employees satisfying this condition. 

### Remember

```text id="p0k7qh"
<=  → Less than OR equal to
```

---

# 6. Not Equal To `!=`

The `!=` operator means:

> **Not equal to.**

### Query

```sql id="sj5g1a"
SELECT *
FROM emp
WHERE job_id != 'ST_CLERK';
```

This means:

> "Display employees whose job ID is NOT `ST_CLERK`."

For example:

```text id="yq5yjp"
AD_PRES   != ST_CLERK → YES
IT_PROG   != ST_CLERK → YES
SA_REP    != ST_CLERK → YES
ST_CLERK  != ST_CLERK → NO
```

So employees having `ST_CLERK` are excluded. 

### Remember

```text id="xwhc6v"
!=  → Not equal to
```

---

# 7. Not Equal To `<>`

`<>` is also used to mean:

> **Not equal to.**

So:

```text id="w3e0x2"
!=
```

and:

```text id="7r6v2q"
<>
```

both represent **not equal to**.

The material lists both forms:

```text id="b6f2nc"
!= or <>
```



---

# Easy Way to Understand All Operators

Imagine the employee salary is:

```text id="2ck9n8"
SALARY = 34000
```

Now ask Oracle different questions:

| Operator | Question                      |
| -------- | ----------------------------- |
| `=`      | Is salary exactly 34000?      |
| `>`      | Is salary greater than 34000? |
| `<`      | Is salary less than 34000?    |
| `>=`     | Is salary 34000 or greater?   |
| `<=`     | Is salary 34000 or less?      |
| `!=`     | Is salary not 34000?          |
| `<>`     | Is salary not 34000?          |

---

# All Queries in This Section

## Query 1 — First name is Akash

```sql id="5b7xms"
SELECT *
FROM emp
WHERE f_name = 'Akash';
```

**Operator:** `=`

Meaning:

> First name must be exactly `Akash`. 

---

## Query 2 — Department ID greater than 30

```sql id="tdx0cw"
SELECT *
FROM emp
WHERE dept_id > 30;
```

**Operator:** `>`

Meaning:

> Department ID must be greater than `30`. 

---

## Query 3 — Salary less than 10000

```sql id="m8k7gk"
SELECT *
FROM emp
WHERE salary < 10000;
```

**Operator:** `<`

Meaning:

> Salary must be less than `10000`. 

---

## Query 4 — Commission percentage greater than or equal to 5

```sql id="x3u9t5"
SELECT email, phone_number
FROM emp
WHERE commission_pct >= 5;
```

**Operator:** `>=`

Meaning:

> Commission percentage must be `5` or more.

The result is **no data** with the supplied table data. 

---

## Query 5 — Salary less than or equal to 34000

```sql id="m8v7bx"
SELECT email, f_name, l_name
FROM emp
WHERE salary <= 34000;
```

**Operator:** `<=`

Meaning:

> Salary must be `34000` or less. 

---

## Query 6 — Job ID not equal to ST_CLERK

```sql id="f9d0km"
SELECT *
FROM emp
WHERE job_id != 'ST_CLERK';
```

**Operator:** `!=`

Meaning:

> Display employees whose job ID is not `ST_CLERK`. 

---

# Very Important: `=` vs `!=`

This is one of the easiest places to get confused.

### `=`

Means:

> **I WANT THIS VALUE**

```sql id="qz9nq4"
WHERE job_id = 'ST_CLERK'
```

Only `ST_CLERK` is wanted.

### `!=`

Means:

> **I DON'T WANT THIS VALUE**

```sql id="3zv6eg"
WHERE job_id != 'ST_CLERK'
```

Everything except `ST_CLERK` is wanted.

---

# Very Important: `>` vs `>=`

### `>`

Does **not** include the given value.

```text id="l2p3k9"
salary > 30000
```

`30000` itself is **not included**.

### `>=`

Includes the given value.

```text id="w8h4bz"
salary >= 30000
```

`30000` **is included**.

---

# Very Important: `<` vs `<=`

### `<`

```text id="c4y3nd"
salary < 30000
```

`30000` is **not included**.

### `<=`

```text id="u8xq7h"
salary <= 30000
```

`30000` **is included**.

---

# Easy Memory Trick

Remember:

```text id="q8ny93"
>   → MORE
<   → LESS

>=  → MORE + SAME
<=  → LESS + SAME

=   → SAME
!=  → NOT SAME
<>  → NOT SAME
```

The easiest trick:

> **When `=` is added to `>` or `<`, the boundary value is also accepted.**

---

# Interview Questions

### What are relational operators?

> Relational operators are used to compare values and specify conditions in SQL.

### What are the relational operators?

```text id="t5m8j1"
=
>
<
>=
<=
!=
<>
```

### What is the difference between `>` and `>=`?

> `>` means greater than, while `>=` means greater than or equal to.

### What is the difference between `<` and `<=`?

> `<` means less than, while `<=` means less than or equal to.

### What is the difference between `!=` and `<>`?

> Both are used to represent not equal to.

---

# One-Line Revision

> **Relational operators are used to compare values in SQL.**

```text id="6f5j8x"
=    → Equal
>    → Greater
<    → Less
>=   → Greater or Equal
<=   → Less or Equal
!=   → Not Equal
<>   → Not Equal
```
