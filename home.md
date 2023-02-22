---
title: Programming in the C programming language
description: 
published: true
date: 2022-10-28T23:07:08.523Z
tags: 
editor: markdown
dateCreated: 2022-10-28T18:53:21.221Z
---

 # C Language and Development Tools
 
 #### Contents

-  [Compilers and Programming Tools](CompilersAndProgrammingTools)
- [Strings](Strings)
- [Structs](Structs)
- [Files](Files)
- [Pointers and Dynamic Memory](PointersAndDynamicMemory)
- [Data Structures](DynamicDataStructures)
- [Function Pointers](FunctionPointers)



#### About this Resource

Everyone has their favourite conventions for computer programs. This resource is written with the assumption that you are following (or at least aware of) the conventions that I impose on my programming students.

All examples are written with clarity for the reader as the primary objective. This means that variables are declared first and initialized in a separate step. It means that shorthand notation for operations is never used. It means that everything is parenthesized, even when it might not have to be. Examples are written to compile with `gcc`, using `-ansi -Wall` flags. All of the examples will also compile with `-std=c99
-Wall`.

Short examples often make it tricky to tell what the expectations are for coding conventions. Functions should be prototyped in a `.h` file and defined in a file separate from the file containing `*main*`. Each function prototype must have a preceding comment that describes the function's purpose and usage (The comment belongs in the .h file). Comments in implementation files are limited to explanations of complicated bits of logic or algorithm.

Project files should be organized so that the main project directory has subdirectories for *src*, *bin*, *include* and *doc*. 
- Source code (.c files) go in the *src* subdirectory. 
- Header files (.h files) go in the *include* subdirectory. 
- Documentation and testing files belong in the *doc* directory, 
- the *bin* directory is used by the build process as a place to put executables. 
- If your program uses images or save files, those should be in a separate subfolder called *resource* or*assets* 