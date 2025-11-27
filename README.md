# Custom MYLET Language Interpreter

![Language](https://img.shields.io/badge/Language-Racket-A01F35?style=flat-square&logo=racket)
![Course](https://img.shields.io/badge/Course-COMP301-blue?style=flat-square)
![Status](https://img.shields.io/badge/Status-Completed-success?style=flat-square)

> **MYLET** is a custom programming language interpreter built using **Racket** and the **EOPL** (Essentials of Programming Languages) framework. It extends the classic `LET` language with powerful features like rational number arithmetic, list processing, and multi-condition control flow.

---

## 📖 Table of Contents
- [Features](#-features)
- [Syntax & Examples](#-syntax--examples)
- [Project Structure](#-project-structure)
- [Setup & Usage](#-setup--usage)

---

## ✨ Features

This interpreter goes beyond basic variable binding. It supports:

* **🔢 Advanced Arithmetic:** Handles both **Integers** and **Rational Numbers** (fractions).
    * Supports `+`, `*`, `/`, and `-` via a unified `op` expression.
    * Includes a `simpl()` operator to simplify fractions (e.g., converts `10/4` to `5/2`).
* **⛓️ List Processing:**
    * Create lists: `create-new-list()`.
    * Construct lists: `cons 5 to list`.
    * Aggregate operations: `multiplication(list)` and `min(list)`.
* **🔀 Control Flow:**
    * `if-then-elif-else` structures for complex decision making.
    * `zero?()` predicate for both numbers and rationals.
* **📦 Environment Management:**
    * Stateful environment handling with `x`, `y`, and `z` pre-initialized.

---

## 🛠️ Syntax & Examples

Here is how you write code in **MYLET**:

### 1. Rational Numbers & Operations
MYLET stores rational numbers as pairs `(num . den)`.

```racket
% Add 5/2 and 3/5 (Op code 1 = Addition)
op((5/2), (3/5), 1) 
% Result: (31 . 10)

% Simplify a fraction
simpl((10 / 4))
% Result: (5 . 2)
```

### 2. List Operations
Lists in MYLET currently support numeric values.

```racket
% Create a list and find the minimum value
let mylist = cons 8 to cons 13 to cons 5 to create-new-list()
in min(mylist)
% Result: 5

% Multiply all elements in a list
multiplication(cons 6 to cons 5 to create-new-list())
% Result: 30
```

### 3. Conditional Logic
Unlike standard `LET`, MYLET supports `elif`.

```racket
if zero?(0) 
then 1 
elif zero?(3) 
then 2 
else 3
% Result: 1
```

---

## 📂 Project Structure

| File | Description |
| :--- | :--- |
| `lang.rkt` | **The Grammar.** Defines the lexical specifications and syntax rules (Scanner/Parser). |
| `interp.rkt` | **The Brain.** Contains the `value-of` function that evaluates expressions. |
| `data-structures.rkt` | **The Data.** Defines `ExpVal` (Numbers, Rationals, Lists) and Environment types. |
| `environments.rkt` | **The Scope.** Manages variable bindings (`init-env`, `extend-env`, `apply-env`). |
| `tests.rkt` | **The Verification.** Contains test cases to ensure language stability. |

---

## ⚙️ Setup & Usage

### Prerequisites
1.  Download and install **[Racket](https://racket-lang.org/)**.
2.  Install the **EOPL** package via DrRacket or command line:
    ```bash
    raco pkg install eopl
    ```

### Running the Interpreter
1.  Clone this repository.
2.  Open `interp.rkt` or `tests.rkt` in DrRacket.
3.  Run the file. You can test specific MYLET strings in the REPL:

```racket
(run "let x = 5 in op(x, 2, 2)")
;; Output: #(struct:num-val 10)
```

---
