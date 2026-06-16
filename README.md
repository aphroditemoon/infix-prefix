<div align="center">

# Infix Prefix Expression Converter in C

### A simple, stack-based C program for converting arithmetic expressions between **infix** and **prefix** notation.

<br>

![C](https://img.shields.io/badge/Language-C-blue?style=for-the-badge&logo=c)
![Data Structure](https://img.shields.io/badge/Data%20Structure-Stack-orange?style=for-the-badge)
![Concept](https://img.shields.io/badge/Concept-Expression%20Conversion-purple?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

</div>

---

## 📌 Project Overview

This project is a console based program written in **C** that demonstrates how a **stack data structure** can be used to convert mathematical expressions.

The program provides a simple menu that allows users to:

- Convert an **infix expression** into another expression format through the program’s conversion logic
- Convert a **prefix expression** back into infix notation
- Practice stack operations using a linked list based implementation

It is designed as a beginner friendly data structure project for understanding how stacks work behind expression parsing and conversion.

---

## ✨ Features

- Menu driven console program
- Stack implementation using a linked list
- Dynamic memory allocation with `malloc()` and `free()`
- Supports operators such as `+`, `-`, `*`, `/`, and `^`
- Supports parentheses in expressions
- Handles alphanumeric operands such as `A`, `B`, `C`, `1`, `2`, and `3`
- Includes basic validation for invalid prefix expressions
- Clean and easy-to-follow C structure

---

## 🧠 Concepts Used

This project covers several important programming and data structure concepts:

| Concept | Description |
|---|---|
| `struct` | Used to define stack nodes |
| Linked List | Used as the base structure for the stack |
| Stack | Used to store operators and operands during conversion |
| Pointer | Used to connect nodes dynamically |
| `malloc()` | Allocates memory for new stack nodes |
| `free()` | Releases memory after a node is removed |
| Operator Priority | Determines which operator should be processed first |
| String Handling | Uses C string functions to process expressions |

---

## 🏗️ Program Structure

The stack is built using a linked list. Each node stores a string value and a pointer to the next node.

```c
#define MAKS 200

typedef struct Node {
    char data[MAKS];
    struct Node *next;
} Node;

typedef struct {
    Node *top;
} Stack;
```

---

## ⚙️ Main Functions

| Function | Purpose |
|---|---|
| `initStack()` | Initializes an empty stack |
| `isStackEmpty()` | Checks whether the stack is empty |
| `push()` | Adds a new value to the top of the stack |
| `pop()` | Removes the top value from the stack |
| `peek()` | Reads the top value without removing it |
| `isOperator()` | Checks whether a character is an operator |
| `isAlphanumeric()` | Checks whether a character is a valid operand |
| `reverseString()` | Reverses a given string |
| `getPriority()` | Returns the precedence level of an operator |
| `convertInfixToPrefix()` | Processes an infix expression using stack logic |
| `convertPrefixToInfix()` | Converts a prefix expression back into infix notation |

---

## 🖥️ Program Menu

When the program runs, users will see the following menu:

```text
Pilihlah operasi yang diinginkan:
1. Konversi Infix ke Prefix
2. Konversi Prefix ke Infix
3. Keluar
Masukkan pilihan anda:
```

---

## 🔍 Example Usage

### Prefix to Infix

Input:

```text
+A*BC
```

Output:

```text
(A+(B*C))
```

This shows how the program reads a prefix expression from right to left and rebuilds it into a readable infix expression using stack operations.

---

## 🚀 How to Run

### 1. Clone the Repository

```bash
git clone https://github.com/aphroditemoon/infix-prefix.git
cd infix-prefix
```

### 2. Compile the Program

Run this by using : 

```bash
gcc File.c -o infix_prefix
```

### 3. Run the Program

For Windows:

```bash
infix_prefix
```

For macOS or Linux:

```bash
./infix_prefix
```

---

## 📂 Repository Structure

```text
infix-prefix/
│
├── File.c
└── README.md
```

## 📊 How the Stack Works

A stack follows the **LIFO** principle:

```text
Last In, First Out
```

Example stack behavior:

```text
Push A  -> Top: A
Push B  -> Top: B
Push C  -> Top: C
Pop     -> Removes C first
```

This behavior makes stacks very useful for expression conversion, especially when handling operators, operands, and parentheses.

---

## 🎯 Project Goal

The goal of this project is to strengthen the understanding of:

- Stack data structures
- Linked-list-based stack implementation
- Expression conversion logic
- Operator precedence
- Dynamic memory management in C
- Basic compiler and console program workflow

This project is especially useful for students who are learning data structures and want to see how stacks are applied in a real programming case.

---

## 👨‍💻 Author

**Erlangga Mahardika**  
Repository: `infix-prefix`

---

<div align="center">

### ⭐ Thanks for checking out this project! ⭐

If this project helped you, consider giving the repository a star.

</div>
