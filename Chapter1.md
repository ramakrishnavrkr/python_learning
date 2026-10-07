# Chapter 1 — Python Environment & First Principles

> **Python for AI Engineering — Chapter 1**

This chapter builds the mental model required before moving into Python data types, functions, OOP, APIs, and AI development.

The goal is not just to memorize Python syntax, but to understand **what Python is doing when your code runs**.

---

## Learning Objectives

By the end of this chapter, you should understand:

- What Python is
- What the Python interpreter does
- What the Python REPL is
- The difference between a Python script and the REPL
- How a `.py` file is executed
- Expressions vs statements
- Python variables and names
- Assignment and rebinding
- `type()`
- `id()`
- The basic relationship between names and objects
- How to experiment with Python interactively

---

# 1. What Is Python?

Python is a:

- Programming language
- Runtime environment
- Ecosystem of libraries and tools

At a simplified level:

```text
Python source code
       ↓
Python interpreter
       ↓
Execution
       ↓
Result
```

For example:

```python
print("Hello Python")
```

When Python executes this code, the interpreter understands the Python instructions and performs the requested operation.

---

# 2. Python Compared With PHP

If you already know PHP, Python is easier to understand by comparing the two.

### PHP

```php
<?php

$name = "Ravi";

echo $name;
```

Run it:

```bash
php test.php
```

### Python

```python
name = "Ravi"

print(name)
```

Run it:

```bash
python test.py
```

A few basic differences:

| PHP | Python |
|---|---|
| `.php` | `.py` |
| `php file.php` | `python file.py` |
| `echo` | `print()` |
| `$name` | `name` |
| Composer | pip / uv |
| `{ }` commonly used for blocks | Indentation defines blocks |

The important point is:

> Both PHP and Python require a runtime/interpreter to execute their source code.

---

# 3. The Python Interpreter

The **Python interpreter** is the program responsible for processing Python code and executing it.

For example, if you create:

```text
hello.py
```

with:

```python
print("Hello")
```

and run:

```bash
python hello.py
```

the Python interpreter reads and executes the Python source code.

Conceptually:

```text
hello.py
   │
   ▼
Python Interpreter
   │
   ▼
print("Hello")
   │
   ▼
Hello
```

You don't normally communicate directly with the computer's CPU using Python instructions.

Instead:

```text
Your Python Code
       ↓
Python Interpreter
       ↓
Operating System
       ↓
Computer Hardware
```

The exact implementation details are more complicated, and we'll study those later when we discuss Python's execution model.

---

# 4. Checking Your Python Installation

From a terminal:

```bash
python --version
```

On some systems:

```bash
python3 --version
```

Example:

```text
Python 3.x.x
```

You can also start Python interactively:

```bash
python
```

You may see something similar to:

```text
Python 3.x.x ...
>>>
```

The:

```text
>>>
```

is the Python interactive prompt.

---

# 5. What Is the Python REPL?

REPL stands for:

> **Read → Evaluate → Print → Loop**

It is an interactive environment where you enter Python code and immediately see the result.

Example:

```text
>>> 5 + 8
13
```

Conceptually:

```text
Read
  ↓
Evaluate
  ↓
Print
  ↓
Loop
  ↺
```

You enter something:

```python
5 + 8
```

Python evaluates it:

```text
13
```

Then it waits for your next instruction.

---

# 6. Why Is the REPL Useful?

The REPL is extremely useful for:

- Learning Python
- Testing small pieces of code
- Checking how a function behaves
- Experimenting with expressions
- Debugging simple problems
- Quickly checking Python syntax

For example:

```text
>>> 100 / 4
25.0
```

You don't need to create a file just to test a simple expression.

For AI engineering, this becomes useful when experimenting with:

- Python libraries
- API responses
- Data transformations
- JSON
- LLM libraries
- Embeddings
- Regular expressions
- Small algorithms

---

# 7. Python Scripts

A **Python script** is normally a `.py` file containing Python source code.

Example:

```text
hello.py
```

Contents:

```python
print("Hello")
print("Welcome to Python")
```

Run it:

```bash
python hello.py
```

Output:

```text
Hello
Welcome to Python
```

Unlike the REPL, a script allows you to save your program and run it repeatedly.

### REPL vs Script

| REPL | Script |
|---|---|
| Interactive | Saved source file |
| Good for experimentation | Good for applications |
| Immediate feedback | Run whenever needed |
| Temporary unless saved elsewhere | Persistent |
| `>>>` prompt | `.py` file |

Both ultimately involve the Python interpreter.

---

# 8. Expressions

An **expression** is Python code that can be evaluated to produce a value.

Examples:

```python
10 + 20
```

Result:

```text
30
```

Another example:

```python
"Hello"
```

This evaluates to a string object.

Another:

```python
7 * 6
```

Result:

```text
42
```

Another:

```python
10 > 5
```

Result:

```text
True
```

A useful beginner mental model is:

> **Expression → produces/evaluates to a value**

Examples:

```python
5 + 5
```

```python
"Python"
```

```python
100 > 20
```

---

# 9. Statements

A **statement** performs an action or forms an instruction in a Python program.

For example:

```python
name = "Ravi"
```

This is an assignment statement.

It associates the name `name` with the resulting string object.

Another example:

```python
print("Hello")
```

This is a statement-like function call used as an instruction to perform an action.

At this stage, don't worry about every formal distinction in Python's grammar.

Use this mental model:

```text
Expression
    ↓
Produces a value

Statement
    ↓
Performs an instruction/action
```

We'll refine this model later.

---

# 10. Expressions Inside Statements

Python statements can contain expressions.

For example:

```python
total = 100 + 50
```

The right-hand side:

```python
100 + 50
```

is an expression.

Python evaluates it:

```text
150
```

Then the assignment associates `total` with that resulting value.

Conceptually:

```text
100 + 50
   ↓
  150
   ↓
total = 150
```

This is an important concept because Python programs constantly combine expressions and statements.

---

# 11. Variables in Python

Beginners often imagine a variable as a box:

```text
x
┌─────────┐
│   10    │
└─────────┘
```

This model is useful initially, but Python is better understood using **names and objects**.

Consider:

```python
x = 10
```

A better mental model is:

```text
x ───────► 10
          object
```

The name `x` refers to an object.

This distinction becomes very important when learning:

- Assignment
- Mutability
- Lists
- Dictionaries
- Functions
- OOP
- Memory behavior

---

# 12. Python Is Dynamically Typed

Python does not require you to declare a variable's type like some statically typed languages.

For example:

```python
value = 100
```

Later:

```python
value = "Hello"
```

This is valid Python.

The name `value` is now associated with a string object instead of the integer object.

Conceptually:

```text
value ───► 100
```

After:

```python
value = "Hello"
```

it becomes:

```text
value ───► "Hello"
```

The name can be rebound.

---

# 13. Assignment and Rebinding

Consider:

```python
a = 15
b = a
a = 30
```

Let's understand this carefully.

First:

```python
a = 15
```

Conceptually:

```text
a ───► 15
```

Then:

```python
b = a
```

Now:

```text
a ───► 15
b ───► 15
```

Then:

```python
a = 30
```

The name `a` is rebound:

```text
a ───► 30

b ───► 15
```

Therefore:

```python
print(a)
```

produces:

```text
30
```

while:

```python
print(b)
```

produces:

```text
15
```

This is one of the most important beginner concepts in Python.

> Assignment changes what a name refers to. It does not mean that all other names referring to the previous object automatically change.

---

# 14. The `type()` Function

Python provides the built-in function:

```python
type()
```

It tells you the type of an object.

Example:

```python
x = 10
type(x)
```

Result:

```text
<class 'int'>
```

Another:

```python
name = "Python"
type(name)
```

Result:

```text
<class 'str'>
```

Another:

```python
price = 19.99
type(price)
```

Result:

```text
<class 'float'>
```

A useful mental model:

```text
type(x)
   ↓
"What kind of object is x referring to?"
```

---

# 15. The `id()` Function

Python also provides:

```python
id()
```

It returns an integer representing the **identity** of an object during its lifetime.

Example:

```python
x = 10

print(id(x))
```

The exact number is not something you should memorize.

The important concept is:

```text
type(x)
    ↓
What type is the object?

id(x)
    ↓
What is the object's identity?
```

For example:

```python
x = 10

print(type(x))
print(id(x))
```

You may get output similar to:

```text
<class 'int'>
140735...
```

The actual `id()` value can vary between runs and Python implementations.

---

# 16. `type()` vs `id()`

This distinction is important.

| Function | Purpose |
|---|---|
| `type(x)` | Tells you the object's type |
| `id(x)` | Gives the object's identity value |
| `print(x)` | Displays the value |

For example:

```python
x = 42

print(x)
print(type(x))
print(id(x))
```

Think:

```text
print(x)
   ↓
"What value?"

type(x)
   ↓
"What type?"

id(x)
   ↓
"Which object identity?"
```

---

# 17. A Useful Experiment

Try this in the Python REPL:

```python
x = 10
type(x)
```

Then:

```python
x = "Python"
type(x)
```

Notice that the same name can refer to objects of different types.

Then:

```python
id(x)
```

This allows you to inspect the identity of the current object referenced by `x`.

---

# 18. Important Mental Model

The most important mental model from Chapter 1 is:

```text
             object
               ▲
               │
             name
```

For example:

```python
language = "Python"
```

Think:

```text
language ───────► "Python"
                   │
                   └── object
```

Then:

```python
language = "PHP"
```

Now:

```text
language ───────► "PHP"
```

The name has been **rebound**.

This mental model will become extremely important when we study:

- Lists
- Dictionaries
- Mutability
- Functions
- Function arguments
- OOP
- References
- Shallow/deep copies
- Memory behavior

---

# 19. Practical Exercise

Create a file:

```text
chapter1.py
```

Write a small program containing:

- Your name
- Your years of programming experience
- Your current learning goal

For example:

```python
name = "Your Name"
experience = 10
goal = "AI Engineering"

print(name)
print(experience)
print(goal)

print(type(name))
print(type(experience))
print(type(goal))
```

Then run:

```bash
python chapter1.py
```

---

# 20. Bonus Exercise

Add `id()` for each variable:

```python
print(id(name))
print(id(experience))
print(id(goal))
```

Observe the output.

Don't worry about memorizing the actual numbers.

The purpose is to understand that Python objects have identities.

---

# 21. Things You Should Be Able to Explain

Before moving to Chapter 2, you should be able to explain these concepts **without looking at your notes**:

### Python Interpreter

What does the Python interpreter do?

### REPL

What does REPL stand for, and why is it useful?

### Script

What is a `.py` file?

### Expression

What is an expression?

Give two examples.

### Statement

What is a statement?

### Variable

What does a Python name/variable refer to?

### Assignment

What happens when you write:

```python
x = something
```

### Rebinding

What happens when the same name is assigned another value?

### `type()`

What does:

```python
type(x)
```

tell you?

### `id()`

What does:

```python
id(x)
```

tell you?

---

# 22. Common Beginner Mistakes

### Mistake 1 — Thinking Python variables are fixed boxes

Instead of:

```text
x = box containing 10
```

develop the mental model:

```text
x ───► object
```

---

### Mistake 2 — Thinking assignment copies everything

For example:

```python
a = 15
b = a
a = 30
```

does **not** mean:

```text
a = 30
b = 30
```

Instead:

```text
a ───► 30

b ───► 15
```

---

### Mistake 3 — Confusing `type()` and `id()`

Remember:

```python
type(x)
```

asks:

> What type is the object?

while:

```python
id(x)
```

asks:

> What is the object's identity value?

---

### Mistake 4 — Thinking REPL and scripts are completely different Python systems

They both use the Python interpreter.

The difference is mainly **how you provide the Python code**:

```text
REPL
Python code → interactive interpreter

Script
.py file → Python interpreter
```

---

# 23. Complete Chapter 1 Assessment

This assessment is designed to verify that you can **understand, reason about, and apply** the concepts from Chapter 1.

It is intentionally broader than a normal multiple-choice quiz.

## Assessment Structure

| Section | Skill | Questions | Suggested Weight |
|---|---|---:|---:|
| A | Core concepts | 8 | 16% |
| B | Code reasoning | 6 | 24% |
| C | Names, objects & assignment | 4 | 20% |
| D | Practical coding | 2 | 20% |
| E | Interview preparation | 5 | 20% |
| **Total** | | **25** | **100%** |

### Suggested Passing Score

**80% or higher**

However, the most important requirement is that you can correctly explain the concepts involving:

- Interpreter
- REPL
- Expression vs statement
- Assignment
- Rebinding
- Names and objects
- `type()`
- `id()`

---

## Section A — Core Concepts

### Question 1

What is the primary role of the Python interpreter?

A. Store Python programs permanently  
B. Process and execute Python source code  
C. Convert Python into HTML  
D. Manage database tables  

---

### Question 2

What does REPL stand for?

A. Read, Execute, Print, Language  
B. Read, Evaluate, Print, Loop  
C. Run, Execute, Process, Loop  
D. Read, Edit, Parse, Load  

---

### Question 3

Which environment is best suited for quickly experimenting with a small Python expression?

A. Python REPL  
B. Database server  
C. HTML document  
D. Package repository  

---

### Question 4

Which statement best describes a Python script?

A. A saved Python source file that can be executed  
B. A special type of Python variable  
C. Only one Python expression entered at a time  
D. A Python package manager  

---

### Question 5

Which is the best beginner-level description of an expression?

A. Code that always changes a variable  
B. Code that can be evaluated to produce a value  
C. A file containing Python code  
D. A command used only from the terminal  

---

### Question 6

Which operation is most directly associated with assignment?

A. Associating a name with a resulting object  
B. Displaying documentation  
C. Checking Python's installed version  
D. Starting the operating system  

---

### Question 7

What does `type()` allow you to determine?

A. The object's identity value  
B. The Python type of an object  
C. The source file's size  
D. The current terminal directory  

---

### Question 8

What does `id()` provide?

A. The object's identity value  
B. The object's human-readable name  
C. The Python source code  
D. The object's file path  

---

# Section B — Code Reasoning

For each question, reason about the code **before executing it**.

### Question 9

What is the final value associated with `status`?

```python
status = "pending"
status = "complete"
```

---

### Question 10

What will this program display?

```python
first = 7
second = first
first = 11

print(first)
print(second)
```

---

### Question 11

What type is the object currently referenced by `amount`?

```python
amount = 25.75
```

---

### Question 12

Consider:

```python
language = "Python"
type(language)
```

What information does the second line request?

---

### Question 13

Consider:

```python
x = 100
y = x
```

Does the assignment to `y` make the name `y` permanently fixed to that object?

Explain your answer.

---

### Question 14

Consider:

```python
count = 5
count = "five"
```

Is this valid Python?

Explain what happened to the name `count`.

---

# Section C — Names, Objects and Assignment

### Question 15

Explain the difference between:

```text
name → object
```

and the beginner mental model:

```text
variable = box containing value
```

Why is the first model more useful for learning Python?

---

### Question 16

Consider:

```python
a = 20
b = a
```

Draw a simple diagram showing the relationship between `a`, `b`, and the object.

---

### Question 17

Now add:

```python
a = 50
```

Draw the new relationship.

What happened to `b`?

---

### Question 18

In your own words, explain **rebinding**.

Try to explain it without using the phrase:

> "The variable changes."

Instead, describe what happens to the **name and object relationship**.

---

# Section D — Practical Coding Assessment

## Question 19 — Mini Program

Create a file named:

```text
chapter1_assessment.py
```

Create three variables:

- `developer_name`
- `years_experience`
- `learning_goal`

Give them appropriate values.

Then display:

1. Each value
2. Each value's type
3. Each value's identity

Your program should demonstrate:

```python
print()
type()
id()
```

### Expected skills

Your program should demonstrate that you understand:

- Variables/names
- Values/objects
- `print()`
- `type()`
- `id()`

---

## Question 20 — Rebinding Experiment

Create a Python program that demonstrates rebinding.

Your program must:

1. Create a name referring to one value.
2. Assign another name to the first name.
3. Rebind the first name to a different value.
4. Print both names.
5. Print the type of both names.

Example structure:

```python
# Your solution here
```

### Expected result

You should be able to demonstrate that changing one name's association does not automatically rebind another name.

---

# Section E — Interview Preparation

Answer these verbally or in writing as if you were in a technical interview.

### Question 21 — Beginner

**What is the Python interpreter?**

A strong answer should explain:

- What it processes
- What it does with Python source code
- How it relates to executing a Python program

---

### Question 22 — Beginner

**What is the Python REPL, and when would you use it?**

A strong answer should explain:

- REPL expansion
- Interactive execution
- Why it is useful
- Difference from a saved script

---

### Question 23 — Intermediate

**What is the difference between an expression and a statement in Python?**

Your answer should include examples and explain the relationship between expressions and statements.

---

### Question 24 — Intermediate

Consider:

```python
a = 10
b = a
a = 20
```

An interviewer asks:

> "Why is `b` not automatically changed to `20`?"

Explain this using Python's **names and objects** model.

---

### Question 25 — Intermediate

An interviewer asks:

> "What is the difference between `type(x)` and `id(x)`?"

Give a clear explanation and a small example.

---

# Assessment Answer Key

> **For learners:** Try the complete assessment before opening this section.

## Section A

| Question | Answer |
|---|---|
| 1 | B |
| 2 | B |
| 3 | A |
| 4 | A |
| 5 | B |
| 6 | A |
| 7 | B |
| 8 | A |

---

## Section B

### Question 9

```text
status = "complete"
```

The second assignment rebinds `status`.

### Question 10

```text
11
7
```

`first` is rebound to `11`, while `second` remains associated with the earlier value.

### Question 11

```text
float
```

### Question 12

It asks Python to determine the type of the object currently referenced by `language`.

### Question 13

No.

Python names can be rebound. An assignment to `y` does not permanently restrict the name to that object.

### Question 14

Yes.

After the second assignment:

```text
count ───► "five"
```

The name `count` has been rebound from the integer object to the string object.

---

## Section C

### Question 15

The names-and-objects model is more accurate because a Python name refers to an object and can later be rebound to another object.

This becomes particularly important when learning:

- Mutability
- References
- Function arguments
- Collections
- OOP
- Copying

### Question 16

Conceptually:

```text
a ───┐
     ├──► 20
b ───┘
```

Both names refer to the same object/value in this simple example.

### Question 17

After:

```python
a = 50
```

the relationship becomes:

```text
a ───► 50

b ───► 20
```

`b` remains associated with the earlier object/value.

### Question 18

**Rebinding** means changing which object a name refers to through assignment.

---

# Practical Coding — Evaluation

## Question 19

A complete solution should:

- Create all three requested names.
- Assign meaningful values.
- Print each value.
- Use `type()` for each.
- Use `id()` for each.
- Run without errors.

There are many valid implementations.

---

## Question 20

A complete solution should demonstrate:

```text
name A ───► original object
name B ───► original object

after rebinding:

name A ───► new object
name B ───► original object
```

The exact values and variable names may differ.

---

# Interview Answer Guide

## Question 21

A strong answer:

> The Python interpreter is the program that processes Python source code and executes the instructions. When we run a Python script, the interpreter reads the Python code and performs the operations described by it.

---

## Question 22

A strong answer:

> REPL stands for Read, Evaluate, Print, Loop. It provides an interactive Python environment where I can enter Python code, have it evaluated immediately, see the result, and then enter more code. It's useful for learning, experimentation, debugging and quickly testing small pieces of code.

---

## Question 23

A strong answer:

> An expression is code that can be evaluated to produce a value, such as an arithmetic calculation or comparison. A statement represents an instruction or action in a program, such as assignment. Statements can contain expressions.

---

## Question 24

A strong answer:

> `b = a` makes `b` refer to the object currently referenced by `a`. When `a` is later assigned `20`, the name `a` is rebound. That doesn't automatically change the binding of `b`.

---

## Question 25

A strong answer:

> `type(x)` tells me the Python type of the object currently referenced by `x`. `id(x)` gives me the object's identity value during its lifetime. So `type()` answers "what type?" while `id()` gives information about "which object identity?"

---

# Scoring Guide

| Score | Level | Recommendation |
|---:|---|---|
| 90–100% | Excellent | Ready for Chapter 2 |
| 80–89% | Good | Ready for Chapter 2; review weak areas |
| 70–79% | Developing | Review Chapter 1 before continuing |
| 60–69% | Needs Review | Repeat exercises and assessment |
| <60% | Foundation Gap | Relearn Chapter 1 concepts |

### Important

Don't judge yourself only by the multiple-choice score.

For Python, being able to **explain and write code** is more important than recognizing the correct option.

A learner who scores 90% on MCQs but cannot explain:

```python
a = 10
b = a
a = 20
```

has not fully mastered the chapter.

---

# Chapter 1 Interview Readiness Checklist

You should be able to answer these without notes:

- [ ] What is Python?
- [ ] What is the Python interpreter?
- [ ] What is the REPL?
- [ ] What does REPL stand for?
- [ ] What is a Python script?
- [ ] How do you run a `.py` file?
- [ ] What is an expression?
- [ ] What is a statement?
- [ ] Can a statement contain an expression?
- [ ] What does assignment do?
- [ ] What does rebinding mean?
- [ ] What is a Python name?
- [ ] What does a name refer to?
- [ ] What does `type()` do?
- [ ] What does `id()` do?
- [ ] Why can the same name refer to different types at different times?
- [ ] Why doesn't rebinding one name automatically rebind another name?

---

# Chapter 1 Final Practical Challenge

Without looking at the chapter notes, create:

```text
chapter1_final.py
```

Your program should demonstrate all of these concepts:

```text
1. A variable/name
2. Assignment
3. Rebinding
4. An expression
5. A statement
6. print()
7. type()
8. id()
```

Then explain each part of your program in your own words.

### Challenge requirement

You should be able to explain:

> "What happens inside Python when this program runs?"

rather than simply saying:

> "This line prints something."

That distinction marks the transition from **learning Python syntax** to **understanding Python**.

---

# 24. Interview Preparation

### Beginner

**Q: What is the Python interpreter?**

You should be able to explain that it processes Python source code and executes it.

---

**Q: What is the REPL?**

You should know:

```text
Read
Evaluate
Print
Loop
```

and explain why it is useful.

---

**Q: What is the difference between a Python script and the REPL?**

You should explain that a script is saved source code in a file, while the REPL provides an interactive environment for entering and evaluating code.

---

### Intermediate

**Q: What is the difference between an expression and a statement?**

You should explain that expressions evaluate to values while statements perform instructions/actions, while understanding that statements can contain expressions.

---

**Q: What does assignment mean in Python?**

A strong answer should mention the relationship between a name and an object rather than describing variables only as fixed storage boxes.

---

**Q: What is the difference between `type()` and `id()`?**

You should be able to explain both clearly and give a small example.

---

# 25. Chapter 1 Completion Checklist

- [ ] I understand what Python is
- [ ] I understand the role of the interpreter
- [ ] I can start the Python REPL
- [ ] I understand what REPL means
- [ ] I understand Python scripts
- [ ] I know how to run a `.py` file
- [ ] I understand expressions
- [ ] I understand statements
- [ ] I understand assignment
- [ ] I understand that Python names can be rebound
- [ ] I understand that names refer to objects
- [ ] I can use `type()`
- [ ] I can use `id()`
- [ ] I understand the difference between `type()` and `id()`
- [ ] I can explain these concepts without memorizing definitions

**Chapter status: COMPLETE**

---

# 26. Chapter 1 Final Assessment Result

The interactive Chapter 1 assessment was completed with:

**Score: 5 / 5 — 100%**

Demonstrated understanding:

- Python interpreter — understood
- REPL — understood
- Expressions — understood
- Statements — understood
- Assignment — understood
- Rebinding — understood
- Names and objects — understood
- `type()` — understood

The chapter is therefore considered **complete**.

---

# 27. Key Takeaways

The most important ideas from Chapter 1 are:

```text
Python source code
       ↓
Python interpreter
       ↓
Execution
```

The REPL provides:

```text
Read → Evaluate → Print → Loop
```

Expressions:

```text
Evaluate → produce a value
```

Statements:

```text
Perform an instruction/action
```

Python names:

```text
name ───► object
```

Assignment can change that relationship:

```text
name ───► object A

        ↓ assignment

name ───► object B
```

And:

```python
type(x)
```

helps answer:

> What type is the object?

while:

```python
id(x)
```

provides:

> The object's identity value.

---

# Next Chapter

## Chapter 2 — Python Data Types

In the next chapter we will study Python's core data types in depth:

```text
int
float
bool
str
None
list
tuple
set
dict
```

We will also begin exploring an extremely important Python concept:

> **Mutable vs Immutable objects**

That concept will build directly on the **names → objects → assignment** mental model from Chapter 1.