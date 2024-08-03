The meow language should use a cat related 
### What is a compiler?

https://en.wikipedia.org/wiki/Compiler

In computing, a compiler is a computer program that translates computer code written in one programming language (the source language) into another language (the target language). The name "compiler" is primarily used for programs that translate source code from a high-level programming language to a low-level programming language (e.g. assembly language, object code, or machine code) to create an executable program.

### How to write a compiler
LLVM - https://www.youtube.com/watch?v=BT2Cv-Tjq7Q
https://en.wikipedia.org/wiki/LLVM
Bjarne Stroustrup - https://www.youtube.com/watch?v=ZQds2aGHwDA

#### Steps
- Install LLVM
- Write a Lexer - scans source code and breaks it into a collection of tokens (literals, identifiers, keywords, operators, etc.)
- Design an AST (Abstract Syntax Tree) - Represents the structure of the code and how different tokens relate to each other. This is accomplished by giving each node its own class.
- Write a Parser - Loops over each token and builds the AST
- Write IR generator - generate the intermediate representation code. Make use of LLVM primitives. Unlike ASM (Assembly) this code is independent of hardware architectures. The LLVM optimizer will optimize the generated IR code over multiple passes. 
  ![[Pasted image 20240803102305.png]]
- Generate machine code - The LLVM back end will then generate the platform specific code.

https://www.youtube.com/watch?v=ZQds2aGHwDA


### Steps to Design and Implement a Compiler

1. **Language Specification**: Define the syntax and semantics of the MEOW language. This includes:
    
    - Keywords and syntax rules
    - Data types and structures
    - Control flow constructs (if, loops, etc.)
    - Functions and procedures
    - Object-oriented features (classes, inheritance, etc.)
    - Memory management rules
2. **Lexical Analysis (Lexer)**: Create a lexer to tokenize the input source code. The lexer reads the raw source code and converts it into a stream of tokens, each representing a syntactic component like keywords, identifiers, operators, and literals.
    
3. **Syntax Analysis (Parser)**: Build a parser to construct an Abstract Syntax Tree (AST) from the token stream. The parser checks for correct syntax according to the language's grammar and generates a hierarchical tree structure representing the code.
    
4. **Semantic Analysis**: Implement semantic analysis to ensure the code adheres to the language rules beyond syntax. This includes type checking, scope resolution, and other context-sensitive checks.
    
5. **Intermediate Representation (IR)**: Translate the AST into an intermediate representation. IR is a lower-level code representation that's easier to optimize and translate into machine code.
    
6. **Optimization**: Apply various optimization techniques to the IR to improve the performance of the generated code.
    
7. **Code Generation**: Generate the target machine code or bytecode from the optimized IR. This involves translating the IR instructions into the specific instructions of the target architecture.
    
8. **Code Emission**: Output the generated code in the appropriate format (executable, library, etc.).

### Choosing the Base Language for the Compiler

Using C++ as the base language for writing your compiler is a good choice because:

- C++ provides low-level memory management capabilities, which can be useful for implementing efficient compilers.
- It has strong support for object-oriented programming, which can help in organizing the compiler components.
- C++ is widely used in the industry for writing compilers (e.g., LLVM).

However, other languages like Rust, Python, and even Java could also be considered depending on your comfort level and specific project requirements.

### Self-Hosting

> Before a system can become self-hosted, another system is needed to develop it until it reaches a stage where self-hosting is possible. When developing for a new computer or operating system, a system to run the development software is needed, but development software used to write and build the operating system is also necessary. This is called a bootstrapping problem or, more generically, a chicken or the egg dilemma. 

Software development using compiler or interpreters can also be self hosted when the compiler is capable of compiling itself.[1]

Since self-hosted compilers suffer from the same bootstrap problems as operating systems, a compiler for a new programming language needs to be written in an existing language. So the developer may use something like assembly language, C/C++, or even a scripting language like Python or Lua to build the first version of the compiler. Once the language is mature enough, development of the compiler can shift to the compiler's native language, allowing the compiler to build itself.
