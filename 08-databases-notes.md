# 8. Databases — AS Level Computer Science (9618)

> Topics covered: 8.1 Database Concepts | 8.2 DBMS | 8.3 DDL & DML (SQL)

---

## 8.1 Database Concepts

### File-Based Approach — Limitations

A file-based approach stores data in separate files, usually one per application/department, each with its own program to access it.

| Problem | Explanation |
|---|---|
| **Data redundancy** | Same data duplicated across multiple files (e.g. a customer's address stored in both the Sales file and the Accounts file). Wastes storage space. |
| **Data inconsistency** | Because data is duplicated, updating it in one file but not another leads to conflicting/contradictory values. |
| **Data isolation** | Data is scattered across different files/formats, making it hard to write programs that need data from multiple files. |
| **Poor data security** | Access rights are hard to apply consistently across many separate files. |
| **Lack of data integrity** | No centralised way to enforce validation rules across files. |
| **Program–data dependence** | Application programs are tightly linked to the file structure — a change in file structure requires rewriting the programs. |
| **Difficult concurrent access** | Multiple users trying to access/update the same file at once can cause conflicts or corruption. |
| **Lack of flexibility** | Producing new/ad-hoc queries or reports is difficult since it requires new programs. |

### How a Relational Database Solves These

- **Centralised data store** — one single repository of data, accessed by all applications → removes data isolation.
- **Data is shared** and structured into related tables → reduces **redundancy** and **inconsistency**.
- **DBMS enforces integrity constraints** (e.g. primary keys, referential integrity) centrally.
- **Data independence** — the logical structure of data is separate from the physical storage and separate from applications, so changes to storage don't require rewriting programs.
- **Centralised security** — access rights can be set at table/field level for users/groups.
- **Query language (SQL)** allows flexible ad-hoc queries without new programs.

---

### Key Terminology

| Term | Definition |
|---|---|
| **Entity** | Something about which data is stored (a person, object, event) — becomes a table, e.g. `Student`. |
| **Table (Relation)** | A collection of related records, organised into rows and columns. |
| **Record (Row / Tuple)** | A single row in a table — one occurrence of the entity. |
| **Field (Column / Attribute)** | A single piece of data in a record — one characteristic of the entity. |
| **Primary Key** | A unique attribute (or combination) that identifies each record in a table. Cannot be NULL or duplicated. |
| **Candidate Key** | An attribute (or set of attributes) that *could* be chosen as the primary key — i.e. it is unique for every record. One candidate key is chosen as the primary key; the others remain candidate keys. |
| **Secondary Key** | A field (not the primary key) used to sort or search records, e.g. Surname. |
| **Foreign Key** | An attribute in one table that is the primary key in another table — used to link/relate two tables. |
| **Relationship** | An association between two entities/tables. |
| **Referential Integrity** | A rule ensuring that a foreign key value must either match an existing primary key value in the related table, or be NULL — prevents "orphan" records. |
| **Indexing** | Creating a separate lookup structure on a field to speed up searching/sorting, without physically reordering the table. |

---

### Types of Relationship

| Relationship | Symbol | Example |
|---|---|---|
| **One-to-One (1:1)** | `1 — 1` | A `Person` has one `Passport`; a `Passport` belongs to one `Person`. |
| **One-to-Many (1:M)** | `1 — M` | A `Department` has many `Employees`; an `Employee` belongs to one `Department`. |
| **Many-to-Many (M:N)** | `M — N` | A `Student` studies many `Courses`; a `Course` has many `Students`. (Resolved using a **link/junction table** in a relational database, since M:N can't be implemented directly.) |

**How relationships are implemented:** the primary key of the "one" side is placed as a **foreign key** in the "many" side table.

---

### Entity-Relationship (E-R) Diagrams

An E-R diagram documents entities and the relationships between them.

- **Entities** → drawn as rectangles, named in the singular (e.g. `Student`, not `Students`).
- **Relationships** → shown as a line connecting two entities, labelled with a verb (e.g. "enrols on").
- **Cardinality** (crow's foot notation) shown at each end of the line:

```
Department ───1                    M─── Employee
   (one Department has many Employees)

Student  ───M                     N─── Course
   (resolved via a link table: StudentCourse)

Person  ───1                       1─── Passport
```

**Crow's foot notation basics:**
- Single bar `|` = one
- Crow's foot `<` = many
- Circle `○` = optional (zero)

**Example (1:M):**

```
[Department] 1 ────────── M [Employee]
```

**Example (M:N resolved with link table):**

```
[Student] 1 ── M [StudentCourse] M ── 1 [Course]
```

---

### Normalisation

Normalisation is a step-by-step process of organising data to **eliminate redundancy** and ensure **data integrity**, by breaking large tables into smaller, related tables.

#### Unnormalised Form (UNF)
Data as originally collected — may contain repeating groups (a field/set of fields with multiple values per record).

#### First Normal Form (1NF)
A table is in 1NF if:
- There are **no repeating groups** (no multi-valued fields).
- Every attribute holds a single (atomic) value.
- There is a primary key.

*Fix:* Remove repeating groups into a new table, carrying the key of the original table as a foreign key.

#### Second Normal Form (2NF)
A table is in 2NF if:
- It is already in **1NF**, **and**
- Every non-key attribute is **fully functionally dependent on the whole primary key** (no *partial dependency*).

> Partial dependency only applies when the primary key is a **composite key** (made of 2+ fields). If the primary key is a single field, and the table is in 1NF, it is automatically in 2NF.

*Fix:* Move attributes that depend on only part of the composite key into a separate table.

#### Third Normal Form (3NF)
A table is in 3NF if:
- It is already in **2NF**, **and**
- There are **no transitive dependencies** — i.e. no non-key attribute depends on another non-key attribute (all non-key attributes depend *only* on the primary key).

*Fix:* Move the transitively dependent attribute(s) into a new table with the attribute they truly depend on as its key.

#### Quick Summary Table

| Normal Form | Removes |
|---|---|
| 1NF | Repeating groups |
| 2NF | Partial dependency (on composite key) |
| 3NF | Transitive dependency (non-key → non-key) |

#### Worked Example

**Unnormalised data:**

```
Order( OrderID, CustomerName, CustomerAddress,
       {ProductID, ProductName, Price, Quantity} )
```

**1NF** — remove repeating group `{ProductID, ProductName, Price, Quantity}`:

```
Order(OrderID, CustomerName, CustomerAddress)
OrderLine(OrderID, ProductID, ProductName, Price, Quantity)
```

**2NF** — `OrderLine` has composite key `(OrderID, ProductID)`. `ProductName` and `Price` depend only on `ProductID` (partial dependency) → move out:

```
Order(OrderID, CustomerName, CustomerAddress)
OrderLine(OrderID, ProductID, Quantity)
Product(ProductID, ProductName, Price)
```

**3NF** — check `Order`: does `CustomerAddress` depend on `CustomerName` (a non-key field) rather than `OrderID`? If a customer's address only depends on who they are, not the order → transitive dependency → move out:

```
Order(OrderID, CustomerID)
Customer(CustomerID, CustomerName, CustomerAddress)
OrderLine(OrderID, ProductID, Quantity)
Product(ProductID, ProductName, Price)
```

#### How to Explain Whether Tables ARE / ARE NOT in 3NF
State clearly, referencing the definitions:
1. Identify the primary key.
2. Check 1NF — any repeating groups? ✅/❌
3. Check 2NF — any non-key attribute dependent on only *part* of a composite key? ✅/❌
4. Check 3NF — any non-key attribute dependent on *another non-key attribute* rather than the primary key? ✅/❌
5. Conclude: "This table **is/is not** in 3NF because ..."

---

## 8.2 Database Management Systems (DBMS)

A **DBMS** is software that allows users to define, create, maintain, and control access to a database.

### Features of a DBMS Addressing File-Based Issues

| Feature | Description |
|---|---|
| **Data management / Data Dictionary** | Stores **metadata** — data about the data (field names, data types, lengths, validation rules, relationships). Ensures consistency and helps enforce standards. |
| **Data modelling** | Allows designers to define entities, attributes, and relationships (e.g. via E-R diagrams) before building the database. |
| **Logical schema** | Describes the overall logical structure of the database (tables, fields, relationships) — independent of how data is physically stored. Provides **data independence**. |
| **Data integrity** | Rules (e.g. validation, referential integrity, constraints) that ensure data is accurate and consistent. |
| **Data security** | Protects data from unauthorised access and loss, including: |
| — Backup procedures | Regular copies of data taken so it can be restored after loss/corruption/disaster. |
| — Access rights | Different permissions (read/write/modify/delete) given to individual users or groups, restricting what data they can see/change. |

### Software Tools within a DBMS

| Tool | Purpose |
|---|---|
| **Developer interface** | Provides tools (forms, wizards, scripting) for developers to design tables, queries, forms, and reports without writing raw SQL — speeds up and simplifies database development. |
| **Query processor** | Accepts a query (e.g. SQL statement), interprets/parses it, optimises it, and executes it against the database, returning the results. |

---

## 8.3 Data Definition Language (DDL) & Data Manipulation Language (DML)

- **DDL** — used to create and modify the **structure** of the database (databases, tables, keys).
- **DML** — used to **query and maintain the data** stored within the tables.
- The industry-standard language for both is **SQL (Structured Query Language)**.

---

### DDL — Data Definition Language

#### Create a Database
```sql
CREATE DATABASE SchoolDB;
```

#### Create a Table
```sql
CREATE TABLE Student (
    StudentID     INTEGER,
    FirstName     VARCHAR(20),
    LastName      VARCHAR(20),
    DateOfBirth   DATE,
    IsRegistered  BOOLEAN,
    GPA           REAL,
    PRIMARY KEY (StudentID)
);
```

**Common Data Types**

| Data Type | Use |
|---|---|
| `CHARACTER(n)` | Fixed-length text of exactly n characters |
| `VARCHAR(n)` | Variable-length text, up to n characters |
| `BOOLEAN` | True / False value |
| `INTEGER` | Whole number |
| `REAL` | Number with a decimal point |
| `DATE` | Date value (e.g. YYYY-MM-DD) |
| `TIME` | Time value (e.g. HH:MM:SS) |

#### Alter a Table
```sql
-- Add a new column
ALTER TABLE Student ADD Email VARCHAR(50);

-- Remove a column
ALTER TABLE Student DROP COLUMN Email;
```

#### Add a Primary Key
```sql
ALTER TABLE Student
ADD PRIMARY KEY (StudentID);
```

#### Add a Foreign Key
```sql
CREATE TABLE Enrolment (
    EnrolmentID  INTEGER,
    StudentID    INTEGER,
    CourseID     INTEGER,
    PRIMARY KEY (EnrolmentID),
    FOREIGN KEY (StudentID) REFERENCES Student(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Course(CourseID)
);
```

---

### DML — Data Manipulation Language

#### SELECT — Queries

**Basic select:**
```sql
SELECT FirstName, LastName
FROM Student;
```

**With condition (WHERE):**
```sql
SELECT * FROM Student
WHERE GPA > 3.5;
```

**Sorting (ORDER BY):**
```sql
SELECT LastName, FirstName
FROM Student
ORDER BY LastName ASC;
```

**Grouping (GROUP BY) with aggregate functions:**
```sql
SELECT CourseID, COUNT(StudentID) AS NumStudents
FROM Enrolment
GROUP BY CourseID;
```

**Aggregate functions:**

| Function | Purpose |
|---|---|
| `SUM(field)` | Total of numeric values |
| `COUNT(field)` | Number of records/values |
| `AVG(field)` | Average of numeric values |

```sql
SELECT AVG(GPA) FROM Student;
```

**Joining two tables (INNER JOIN):**
```sql
SELECT Student.FirstName, Student.LastName, Course.CourseName
FROM Student
INNER JOIN Enrolment ON Student.StudentID = Enrolment.StudentID
INNER JOIN Course ON Enrolment.CourseID = Course.CourseID;
```

> ⚠️ Syllabus scope: DML queries only need to cover **at most two tables**.

**Combining clauses:**
```sql
SELECT Student.LastName, COUNT(Enrolment.CourseID) AS Courses
FROM Student
INNER JOIN Enrolment ON Student.StudentID = Enrolment.StudentID
WHERE Student.IsRegistered = TRUE
GROUP BY Student.LastName
ORDER BY Courses DESC;
```

---

#### Data Maintenance

**INSERT INTO — add a record:**
```sql
INSERT INTO Student (StudentID, FirstName, LastName, DateOfBirth, IsRegistered, GPA)
VALUES (101, 'Ali', 'Khan', '2007-05-14', TRUE, 3.8);
```

**UPDATE — modify existing records:**
```sql
UPDATE Student
SET GPA = 3.9
WHERE StudentID = 101;
```

**DELETE FROM — remove records:**
```sql
DELETE FROM Student
WHERE StudentID = 101;
```

> ⚠️ Always use a `WHERE` clause with `UPDATE`/`DELETE` — omitting it applies the change to **every** record in the table.

---

## Quick Revision Checklist

- [ ] Can list 5+ limitations of file-based systems
- [ ] Can explain how a relational DB fixes each limitation
- [ ] Know all key terms (PK, candidate key, secondary key, FK, referential integrity, indexing)
- [ ] Can draw an E-R diagram with correct cardinality notation
- [ ] Can normalise a table from UNF → 1NF → 2NF → 3NF
- [ ] Can justify whether a table is/isn't in 3NF
- [ ] Know DBMS features: data dictionary, data modelling, logical schema, integrity, security
- [ ] Know developer interface vs query processor
- [ ] Can write CREATE DATABASE / CREATE TABLE / ALTER TABLE with PRIMARY KEY & FOREIGN KEY
- [ ] Can write SELECT queries with WHERE, ORDER BY, GROUP BY, INNER JOIN, SUM, COUNT, AVG
- [ ] Can write INSERT INTO, UPDATE, DELETE FROM statements
