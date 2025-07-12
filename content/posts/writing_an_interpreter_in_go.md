---
title: Writing An Interpreter In Go
date: 2025-07-10
tags: [interpreter]
---

## Chapter 1

### Lexical Analysis

- Breaking the raw code into meaningful units called tokens.
  - Splitting a sentence into words and punctuation [구두] marks.

### Token

- A token is a piece of the code that has a meaning in the programming language.
- Each token has a type:
  -  Keyword: if, while, return
  - Identifier: variable names like x
  - Literal: numbers like 3, strings like "apple"
  - Operator: +, -, *, ==
  - Punctuation: ;, (, {

### Example of Lexical Analysis

``` c
int x = 5 + 2;
```

```
[Keyword: "int"]
[Identifier: "x"]
[Operator: "="]
[Literal: "5"]
[Operator: "+"]
[Literal: "2"]
[Punctuation: ";"]
```

### Terms

| **Component** | **Role**                     | **Input**            | **Output**                     |
|---------------|------------------------------|----------------------|--------------------------------|
| Lexer         | Tokenizes source code        | Source code (text)   | Tokens                         |
| Parser        | Builds syntax tree           | Tokens               | AST (Abstract Syntax Tree)     |
| Compiler      | Translates entire program    | AST                  | Machine code / Bytecode        |
| Interpreter   | Executes directly            | AST or Bytecode      | Program runs                   |

### Whitespace Sensitivity

- In Python, indentation (spaces/tabs at the start of a line) is syntactically significant.
- The lexer must recognize this and often emits special tokens like INDENT.
- If you mix tabs and spaces, Python will raise an error.
- Languages like C, Java, JavaScript ignore most whitespace — it just separates tokens.