---
description: С++
---

# CPP

## Description

One of early OOP languages, C++ invented by __ Bjarne Stroustrup in 80s as a superset of the C language. Low level at a one hand, powerful at a second, still evolutioning at another one.

There are C++03, C++11, C++14, C++17 and C++20 present-day standards, where number means year of acceptance.

C++ provides procedural, objective and build time generic paradigms of coding.

* [C++ reference](https://en.cppreference.com/w/cpp) — free online documentation with offline options :book:
* [Standard C++](https://isocpp.org/) — official site devoted to ISO standard of the lang :globe\_with\_meridians:

## Toolset

* G++ — compiler from the "[GNU Compiler Collection](https://gcc.gnu.org/)"
* [CLang](https://clang.llvm.org/) — popular LLVM based compiler
* [Boost](https://www.boost.org/) — giant libraries collection which is a "semi-standard library"
* [CMake](https://cmake.org/) — modern build system
* [Doxygen](https://doxygen.nl/) — tool to generate documentation with comments and types hierarhies
* [Valgrind](https://valgrind.org/) — anslizys tool with memory leaks detection
* [Ccache](https://ccache.dev/) — compiler cache which can speedup project building dramatically

## Basic syntax

```cpp
#include <iostream>

// Function
void hello_world() {
  // As you can see, code blocks is fenced with curly braces
  std::cout << "Hello, world!" << std::endl;
  // The semicolon splits lexical tokens
  // and also it is a no-op operator
  ;;;
}

// The main function is the entrypoint of code
int main(int argc, char** argv) {
  hello_world();
  return EXIT_SUCCESS;
}
```

## Comments

_Code documentation syntax and agreements._

```cpp
# include <iostream>
# include <string>

// Single line comment

/* Multiline comment
 * <- this asterisk is just for tidiness
 */

// Doxygen styled annotation:
/** @brief Short function description
 *
 *  Print given strign and return it's length
 *  @param str String to print
 *  @return length of string
 */
int hello_world(const std::string& str) {
  std::cout << str << std::endl;
  return str.length();
}
```

## Project model

_Modules, import or including. Major project files, common structure of library and application. Local environment._

## Type system

_\* Dynamic or static_ _\* Strong or weak_ _\* Explicit or implicit_

_Scopes, variables lifecycle, copying and referencing, modificators like constant._

_Generics._

## Base types and data structures

_Built-in types, most common collections._

## Strings

_Standard types to store strings. Tools and practices to splice, search, copy, replace textual data._

## Execution flow statements

_Loops, conditions and jump operator or recursion._

## Subroutines

_Functions, procedures, lambda expressions etc._

## Object model

_Object-oriented programming tools, syntax of classes._

## Exceptions

_Handling exceptions or errors. Major exceptions hierarchy._

## Filesystem

_Most common tools to deal with files and directories._

## Introspection

_Reflection and metaprogramming tools._

## Asyncronous model

_Asyncronous calls, multithreading, multiprocessing._

## Style guides

_Major naming and structuring points._
