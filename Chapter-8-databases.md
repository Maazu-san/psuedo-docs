# Chapter 8 - Databases (AS Level Computer Science 9618)

---

# 8.1 Database Concepts

## What is a Database?

A **database** is an organised collection of related data that can be easily accessed, managed and updated.

Example:

| StudentID | Name | Class |
|------------|------|-------|
| 1001 | Ali | AS1 |
| 1002 | Sara | AS2 |

A **Database Management System (DBMS)** is software used to create, manage and manipulate databases.

Examples:
- MySQL
- Microsoft Access
- Oracle
- PostgreSQL
- SQLite

---

# File-Based Systems

A **file-based system** stores data in separate files.

Example:

Students.txt

```
1001 Ali AS1
1002 Sara AS2
```

Teachers.txt

```
T01 Ahmed Physics
T02 Bilal CS
```

Each file is managed separately.

---

# Limitations of File-Based Systems

## 1. Data Redundancy

The same data is stored multiple times.

Example:

Student address stored in:
- Admissions file
- Fees file
- Exam file

Problems:
- Wastes storage
- Difficult to update

---

## 2. Data Inconsistency

When one copy is updated but another isn't.

Example:

Admissions File:

```
Ali
Karachi
```

Exam File:

```
Ali
Lahore
```

Now both files disagree.

---

## 3. Data Isolation

Information is spread across many files.

Finding complete information becomes difficult.

---

## 4. Difficult Data Access

Complex searches require searching multiple files manually.

---

## 5. Poor Security

Hard to control who can access individual files.

---

## 6. Poor Data Integrity

Duplicate or incorrect data can easily be entered.

Example:

One file:

```
Ali
```

Another:

```
Aly
```

---

## 7. No Relationships

Files cannot automatically connect related information.

---

# Advantages of Relational Databases

Relational databases solve most file-based problems.

Advantages:

- Reduces duplication
- Improves consistency
- Easier searching
- Better security
- Supports relationships
- Faster queries
- Better data integrity

---

# Database Terminology

---

## Entity

A real-world object being stored.

Examples:

- Student
- Teacher
- Car
- Book

---

## Table

A collection of related records.

Example:

Students Table

| StudentID | Name | Class |
|------------|------|-------|

---

## Record (Tuple)

One complete row in a table.

Example:

|1001|Ali|AS1|

This entire row is one record.

---

## Field (Attribute)

One column in a table.

Example:

Name

or

StudentID

Each column stores one type of information.

---

## Attribute

Another word for a field.

Field = Attribute

---

## Primary Key

A field that uniquely identifies every record.

Rules:

- Unique
- Cannot be NULL
- Only one primary key per table

Example:

| StudentID | Name |
|------------|------|
|1001|Ali|
|1002|Sara|

StudentID is the primary key.

---

## Candidate Key

A field that **could** become the primary key.

Example:

| StudentID | Email |
|------------|-------|

Both are unique.

Either one could become the primary key.

---

## Secondary Key

A field used for searching but not unique.

Example:

| Class |
|-------|
|AS1|
|AS1|
|AS2|

Searching by Class is useful.

---

## Foreign Key

A primary key from another table.

Used to create relationships.

Example:

Students

|StudentID|Name|
|----------|----|
|1001|Ali|

Marks

|StudentID|Marks|
|----------|-----|
|1001|90|

StudentID in Marks is a foreign key.

---

# Relationships

---

## One-to-One (1:1)

One record matches one record.

Example:

Person ↔ Passport

One person has one passport.

---

## One-to-Many (1:M)

One record matches many records.

Example:

Teacher → Students

One teacher teaches many students.

Each student has one teacher.

---

## Many-to-Many (M:N)

Many records relate to many others.

Example:

Students ↔ Subjects

One student studies many subjects.

One subject has many students.

Usually solved using a linking table.

Example:

StudentSubject

|StudentID|SubjectID|

---

# Referential Integrity

Ensures foreign keys always match an existing primary key.

Bad:

Students

|StudentID|
|----------|
|1001|

Marks

|StudentID|
|----------|
|9999|

9999 doesn't exist.

Database rejects it.

---

# Indexing

An index speeds up searching.

Think of it like the index in a textbook.

Instead of checking every page, you jump directly to the required information.

Advantages:

- Faster searching
- Faster sorting

Disadvantage:

- Uses extra storage

---

# Entity Relationship (E-R) Diagrams

Used to design databases.

Example:

```
Student
---------
StudentID (PK)
Name

        1
        |
        |
        ∞

Marks
---------
MarkID (PK)
Score
StudentID (FK)
```

---

# Normalisation

Normalisation removes unnecessary duplication.

Benefits:

- Reduces redundancy
- Improves consistency
- Saves storage
- Easier maintenance

---

# First Normal Form (1NF)

Rules:

- No repeating groups
- Atomic values (one value per field)

❌ Not 1NF

|Name|Subjects|
|----|----------|
|Ali|Math, CS|

✅ 1NF

|Name|Subject|
|----|--------|
|Ali|Math|
|Ali|CS|

---

# Second Normal Form (2NF)

Requirements:

- Already in 1NF
- No partial dependency

Every non-key field depends on the whole primary key.

Usually applies to composite keys.

---

# Third Normal Form (3NF)

Requirements:

- Already in 2NF
- No transitive dependency

Non-key fields must depend only on the primary key.

Bad:

|StudentID|TeacherID|TeacherName|

TeacherName depends on TeacherID.

Move TeacherName into a Teacher table.

---

# Quick Normalisation Checklist

1NF

✔ Atomic values

✔ No repeating groups

---

2NF

✔ In 1NF

✔ No partial dependencies

---

3NF

✔ In 2NF

✔ No transitive dependencies

---

# 8.2 Database Management Systems (DBMS)

A DBMS is software used to manage databases.

Examples:

- MySQL
- Oracle
- PostgreSQL
- Microsoft Access

---

# Features of a DBMS

---

## Data Management

Stores and updates data efficiently.

---

## Data Dictionary

Stores information about the database.

Contains:

- Table names
- Field names
- Data types
- Constraints

Not user data.

---

## Data Modelling

Designing tables and relationships before creating the database.

---

## Logical Schema

The blueprint of the database.

Shows:

- Tables
- Fields
- Relationships

---

## Data Integrity

Ensures data is accurate and valid.

Examples:

- Primary keys
- Foreign keys
- Validation rules

---

## Data Security

Protects data.

Methods:

- Passwords
- User accounts
- Encryption
- Access rights

---

## Backup Procedures

Creates copies of the database.

Purpose:

Recover data after:

- Hardware failure
- Human error
- Virus attack

---

## Access Rights

Different users have different permissions.

Example:

Admin

- Read
- Write
- Delete

Teacher

- Read
- Update

Student

- Read only

---

# Software Tools inside a DBMS

---

## Developer Interface

Used to:

- Design tables
- Create relationships
- Write SQL
- Build forms

---

## Query Processor

Reads SQL commands.

Optimises them.

Returns requested data.

---

# 8.3 DDL and DML

---

# Data Definition Language (DDL)

Used to create or change the database structure.

Commands:

- CREATE DATABASE
- CREATE TABLE
- ALTER TABLE

Think:

DDL = Designing the database

---

# Data Manipulation Language (DML)

Used to work with the data inside tables.

Commands:

- SELECT
- INSERT
- UPDATE
- DELETE

Think:

DML = Managing the data

---

# SQL

Structured Query Language

The standard language used by almost every DBMS.

---

# SQL Data Types

|Type|Purpose|
|----|--------|
|CHARACTER|Single character|
|VARCHAR(n)|Variable length text|
|BOOLEAN|True or False|
|INTEGER|Whole numbers|
|REAL|Decimal numbers|
|DATE|Date|
|TIME|Time|

---

# CREATE DATABASE

```sql
CREATE DATABASE School;
```

---

# CREATE TABLE

```sql
CREATE TABLE Students (
    StudentID INTEGER,
    Name VARCHAR(30),
    Age INTEGER
);
```

---

# PRIMARY KEY

```sql
CREATE TABLE Students (
    StudentID INTEGER,
    Name VARCHAR(30),
    PRIMARY KEY (StudentID)
);
```

---

# FOREIGN KEY

```sql
CREATE TABLE Marks (
    StudentID INTEGER,
    Score INTEGER,
    FOREIGN KEY (StudentID)
    REFERENCES Students(StudentID)
);
```

---

# ALTER TABLE

Add a column

```sql
ALTER TABLE Students
ADD Email VARCHAR(50);
```

---

# SELECT

Display data.

```sql
SELECT Name
FROM Students;
```

---

# WHERE

Filter rows.

```sql
SELECT *
FROM Students
WHERE Age > 17;
```

---

# ORDER BY

Sort data.

Ascending:

```sql
ORDER BY Name;
```

Descending:

```sql
ORDER BY Name DESC;
```

---

# GROUP BY

Groups rows together.

```sql
SELECT Class,
COUNT(*)
FROM Students
GROUP BY Class;
```

---

# INNER JOIN

Combines matching records.

```sql
SELECT Students.Name,
Marks.Score
FROM Students
INNER JOIN Marks
ON Students.StudentID = Marks.StudentID;
```

---

# SUM

Adds values.

```sql
SELECT SUM(Score)
FROM Marks;
```

---

# COUNT

Counts records.

```sql
SELECT COUNT(*)
FROM Students;
```

---

# AVG

Calculates the average.

```sql
SELECT AVG(Score)
FROM Marks;
```

---

# INSERT INTO

Adds new data.

```sql
INSERT INTO Students
VALUES (1001,'Ali',17);
```

---

# UPDATE

Changes existing data.

```sql
UPDATE Students
SET Age = 18
WHERE StudentID = 1001;
```

---

# DELETE

Deletes records.

```sql
DELETE FROM Students
WHERE StudentID = 1001;
```

---

# SQL Execution Order (Useful for Exams)

1. FROM
2. WHERE
3. GROUP BY
4. SELECT
5. ORDER BY

---

# Exam Tips

## Know the Difference

|DDL|DML|
|---|---|
|Changes structure|Changes data|
|CREATE|SELECT|
|ALTER|INSERT|
||UPDATE|
||DELETE|

---

## Remember

Primary Key:
- Unique
- Cannot be NULL

Foreign Key:
- References another table's primary key

1NF:
- Atomic values

2NF:
- Remove partial dependency

3NF:
- Remove transitive dependency

---

# Common Exam Questions

Be able to:

- Explain why databases are better than file-based systems.
- Identify primary and foreign keys.
- Draw simple E-R diagrams.
- Convert tables into 1NF, 2NF and 3NF.
- Explain referential integrity.
- Write simple SQL statements.
- Identify whether SQL is DDL or DML.
- Explain the purpose of indexes.
- Explain DBMS features.
- Interpret SQL queries involving up to two tables.

---
