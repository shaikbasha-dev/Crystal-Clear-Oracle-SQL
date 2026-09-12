# 06 Tables Used for Queries

This folder contains the tables and sample data used for the SQL queries in the upcoming topics.

## Files

```text
06 Tables Used for Queries/
│
├── 01-DEPT.sql
├── 02-EMP.sql
├── 03-J_GRADE.sql
└── README.md
````

## 1. DEPT Table

File:

```text
01-DEPT.sql
```

The `DEPT` table contains department information.

Columns:

* `DEPT_ID`
* `DEPT_NAME`
* `MANAGER_ID`
* `LOC_ID`

## 2. EMP Table

File:

```text
02-EMP.sql
```

The `EMP` table contains employee information.

Columns:

* `EMP_ID`
* `F_NAME`
* `L_NAME`
* `EMAIL`
* `PHONE_NUMBER`
* `HIRE_DATE`
* `JOB_ID`
* `SALARY`
* `COMMISSION_PCT`
* `MANAGER_ID`
* `DEPT_ID`

`EMP.DEPT_ID` references `DEPT.DEPT_ID`.

## 3. J_GRADE Table

File:

```text
03-J_GRADE.sql
```

The `J_GRADE` table contains salary-grade information.

Columns:

* `GRADE`
* `LOW_SAL`
* `HIGH_SAL`

## Execution Order

Execute the SQL files in the following order:

```text
01-DEPT.sql
      ↓
02-EMP.sql
      ↓
03-J_GRADE.sql
```

`DEPT` must be created before `EMP` because `EMP.DEPT_ID` is a foreign key referencing `DEPT.DEPT_ID`.

## Purpose

These three tables provide the data required for the SQL query exercises that follow, including queries involving:

* `EMP`
* `DEPT`
* `J_GRADE`

```
```
