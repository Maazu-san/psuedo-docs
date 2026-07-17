# Chapter 9 - Algorithm Design and Problem Solving (AS Level Computer Science 9618)

---

# 9.1 Computational Thinking Skills

Computational thinking is the process of solving problems in a way that a computer can understand and execute.

The four main computational thinking skills are:

- Abstraction
- Decomposition
- Pattern Recognition *(not required in detail for this chapter)*
- Algorithm Design

---

# Abstraction

## Definition

**Abstraction** is the process of removing unnecessary details and focusing only on the important information needed to solve a problem.

Think of it as:

> Ignore what doesn't matter. Keep only what is essential.

---

## Purpose of Abstraction

Abstraction is used to:

- Simplify complex problems
- Reduce unnecessary information
- Make solutions easier to design
- Allow programmers to focus on important details

---

## Benefits of Abstraction

- Makes problems easier to understand
- Reduces complexity
- Speeds up program development
- Makes debugging easier
- Makes programs easier to maintain

---

## Example 1

Real Car

Contains:

- Engine
- Steering wheel
- Colour
- Tyres
- Fuel level
- Radio
- Air conditioning
- Number plate

Driving Simulator

Needs only:

- Speed
- Steering angle
- Gear
- Brake
- Acceleration

Everything else can be ignored.

---

## Example 2

Student Database

Real student information:

- Name
- Student ID
- Favourite colour
- Height
- Shoe size
- Marks

Exam system only needs:

- Student ID
- Name
- Marks

Everything else is unnecessary.

---

# Abstract Model

An **abstract model** is a simplified version of a real-world system that contains only the essential details.

Example:

Online Shopping System

Instead of storing:

- Product image size
- Warehouse lighting
- Employee uniforms

The abstract model stores:

- Product ID
- Product Name
- Price
- Stock Quantity

---

# Decomposition

## Definition

**Decomposition** is breaking a large problem into several smaller, easier-to-solve problems.

Instead of solving one huge problem, solve many small problems.

---

## Why Use Decomposition?

- Easier to understand
- Easier to test
- Easier to debug
- Easier to divide work among programmers
- Makes programs reusable

---

## Example

Create a Library System

Instead of writing one huge program:

Break it into modules:

```
Library System

├── Login
├── Search Books
├── Borrow Book
├── Return Book
├── Calculate Fine
└── Logout
```

Each module solves one small task.

---

# Program Modules

A **module** is a small section of a program designed to perform one specific task.

Modules are usually written as:

- Procedures
- Functions

---

## Procedure

A procedure performs a task.

It may not return a value.

Example:

```
DisplayMenu()
```

---

## Function

A function performs a task **and returns a value**.

Example:

```
CalculateAverage()
```

Returns the calculated average.

---

# Comparison

| Procedure | Function |
|-----------|----------|
| Performs a task | Performs a task |
| Usually returns nothing | Returns a value |
| Used for actions | Used for calculations |

---

# 9.2 Algorithms

# What is an Algorithm?

An **algorithm** is a step-by-step sequence of instructions used to solve a problem.

A good algorithm must be:

- Correct
- Clear
- Finite (must eventually stop)
- Efficient

---

# Characteristics of a Good Algorithm

- Clear instructions
- Correct solution
- Logical order
- Ends after a finite number of steps
- Easy to understand

---

# IPO Model (Input → Process → Output)

Almost every algorithm follows this structure.

```
Input
   ↓
Process
   ↓
Output
```

---

## Example

Find the area of a rectangle.

Input

```
Length
Width
```

Process

```
Area ← Length × Width
```

Output

```
Area
```

---

# Identifier Names

An **identifier** is the name given to a variable, constant, array, procedure or function.

Good identifiers should:

- Be meaningful
- Describe their purpose
- Be easy to read

Good examples:

```
StudentName
TotalMarks
Average
Counter
Price
```

Poor examples:

```
x
abc
number1
thing
temp2
```

---

# Identifier Table

An identifier table describes every variable used in an algorithm.

Example:

| Identifier | Data Type | Description |
|------------|----------|-------------|
| Name | STRING | Student's name |
| Age | INTEGER | Student's age |
| Average | REAL | Average marks |
| Passed | BOOLEAN | Pass or fail |

---

# Pseudocode

Pseudocode is a human-readable way of writing an algorithm.

It is **not** a programming language.

---

# Basic Structure

```
INPUT

PROCESS

OUTPUT
```

---

# Sequence

Sequence means instructions execute one after another.

Example:

```
INPUT Length
INPUT Width

Area ← Length * Width

OUTPUT Area
```

Execution order:

1. Read Length
2. Read Width
3. Calculate Area
4. Display Area

---

# Selection

Selection allows decisions.

Uses:

```
IF

ELSE

CASE
```

Example:

```
IF Marks >= 50 THEN
    OUTPUT "Pass"
ELSE
    OUTPUT "Fail"
ENDIF
```

---

# Iteration (Repetition)

Iteration repeats instructions.

Cambridge pseudocode uses:

```
FOR

WHILE

REPEAT UNTIL
```

---

## FOR Loop

Used when the number of repetitions is known.

```
FOR Count ← 1 TO 5
    OUTPUT Count
NEXT Count
```

Output:

```
1
2
3
4
5
```

---

## WHILE Loop

Repeats **while** a condition is true.

Condition checked first.

```
WHILE Number < 10
    OUTPUT Number
    Number ← Number + 1
ENDWHILE
```

---

## REPEAT UNTIL Loop

Runs at least once.

Condition checked last.

```
REPEAT
    INPUT Password
UNTIL Password = "abc123"
```

---

# Algorithm Documentation

Algorithms can be represented in three common ways.

---

## 1. Structured English

Uses simple English with programming keywords.

Example:

```
Input two numbers

Add them together

Display the answer
```

---

## 2. Pseudocode

```
INPUT A
INPUT B

Sum ← A + B

OUTPUT Sum
```

---

## 3. Flowchart

Uses symbols instead of words.

Common symbols:

| Symbol | Meaning |
|---------|----------|
| Oval | Start / End |
| Rectangle | Process |
| Parallelogram | Input / Output |
| Diamond | Decision |
| Arrow | Flow of control |

---

# Converting Between Representations

In the exam you may need to convert:

- Structured English → Pseudocode
- Structured English → Flowchart
- Flowchart → Pseudocode
- Pseudocode → Flowchart

Practice all four conversions.

---

# Stepwise Refinement

## Definition

Stepwise refinement is the process of starting with a simple solution and gradually adding more detail until it can be programmed.

Think of it as:

```
Big idea
      ↓
More detail
      ↓
Even more detail
      ↓
Finished algorithm
```

---

## Example

Problem:

Calculate a student's average.

High-level solution:

```
Read marks

Calculate average

Display average
```

Refined version:

```
INPUT Mark1
INPUT Mark2
INPUT Mark3

Average ← (Mark1 + Mark2 + Mark3) / 3

OUTPUT Average
```

More detailed version:

```
INPUT Mark1
INPUT Mark2
INPUT Mark3

Total ← Mark1 + Mark2 + Mark3

Average ← Total / 3

OUTPUT "Average = ", Average
```

Each step adds more detail.

---

# Logic Statements

Logic statements make decisions.

They compare values.

Comparison operators:

| Operator | Meaning |
|-----------|---------|
| = | Equal to |
| <> | Not equal to |
| > | Greater than |
| < | Less than |
| >= | Greater than or equal to |
| <= | Less than or equal to |

---

# Logical Operators

Used to combine conditions.

## AND

Both conditions must be true.

```
Age >= 18 AND Citizen = TRUE
```

---

## OR

Only one condition needs to be true.

```
Marks >= 50 OR SpecialPermission = TRUE
```

---

## NOT

Reverses a condition.

```
NOT Finished
```

---

# Example

```
IF Age >= 18 AND Citizen = TRUE THEN
    OUTPUT "Eligible"
ELSE
    OUTPUT "Not Eligible"
ENDIF
```

---

# Algorithm Design Process

A useful approach when solving exam questions:

```
Understand Problem
        ↓
Use Abstraction
        ↓
Use Decomposition
        ↓
Design Algorithm
        ↓
Write Pseudocode
        ↓
Test Algorithm
        ↓
Improve Using Stepwise Refinement
```

---

# Quick Revision Summary

## Abstraction

✔ Removes unnecessary details

✔ Keeps only essential information

---

## Decomposition

✔ Breaks one large problem into smaller problems

✔ Produces modules (procedures/functions)

---

## Algorithm

✔ Step-by-step solution to a problem

---

## IPO

```
Input
↓
Process
↓
Output
```

---

## Three Programming Constructs

### Sequence

Instructions execute one after another.

---

### Selection

Makes decisions.

Uses:

- IF
- ELSE
- CASE

---

### Iteration

Repeats instructions.

Uses:

- FOR
- WHILE
- REPEAT UNTIL

---

## Stepwise Refinement

Start simple.

Gradually add detail until the algorithm is ready to program.

---

## Ways to Represent an Algorithm

- Structured English
- Pseudocode
- Flowchart

---

## Identifier Table

Contains:

- Identifier name
- Data type
- Description

---

# Common Exam Questions

Be able to:

- Define abstraction and explain its benefits.
- Produce a simple abstract model from a real-world system.
- Explain decomposition and identify suitable program modules.
- Explain the difference between procedures and functions.
- Define an algorithm and describe the characteristics of a good algorithm.
- Create and interpret identifier tables.
- Write pseudocode using sequence, selection and iteration.
- Convert between structured English, flowcharts and pseudocode.
- Explain and apply stepwise refinement.
- Use comparison and logical operators correctly in algorithms.

---
