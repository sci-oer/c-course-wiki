---
title: Make
description: 
published: 1
date: 2023-02-24T17:27:37.559Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:34:46.008Z
---


# Using Make
- Mini Lecture(video) [What is Make](http://localhost:8000/lectures/MakeFiles/Make_Conceptual/)
- Mini Lecture(video)[A simple makefile](http://localhost:8000/lectures/MakeFiles/Make_SimpleExample/)
- Mini Lecture(video)[More Advanced Makefiles](http://localhost:8000/lectures/MakeFiles/Make_ComplexExample/)


A project of any size will require multiple source code files, and programmers must learn to manage larger projects. One tool that is commonly used to manage programming projects, especially c and c++ programs is `make`.

Make is installed by default on nearly every version of unix operating system. Make works by parsing a file (a makefile) and executing the commands it finds in the makefile. The makefile must be written in a particular format.  Any command known to the operating system can be executed.

Make is used to primarily to manage the building of software because its use ensures that the same set of tasks will be done in the same order all of the time. A makefile consists of at least two lines:

```make
target: dependencies
[tab]system command
```
A makefile **should** be named `Makefile`, but other names can be used.  The target can be any word. The first target in the makefile is the one that will execute by default. A makefile is executed via the command line by typing `make` on the command line from the directory that contains the makefile. 

Makefiles can have multiple targets.  A specific target can be executed by typing *make targetname*. It is very important to use a single `tab` instead of spaces in a makefile. An example makefile for a simple c program might look like this:

```make
    all:
        gcc -Wall -std=c99 -pedantic src/tictactoe.c src/tictactoefunctions.c -Iinclude -o bin/runMe -lncurses
```

The makefile above compiles two `.c` files (one of which has a main),
tells the compiler to look in the `include` folder for `.h` files, puts theresulting executable in a `bin` folder, and tells the compiler that it will need to use the `ncurses` library.

A methodical approach to organizing files along with proper use of
makefiles will greatly reduce the amount of time spent managing software projects. A suggested file-folder structure  is shown in the figure below.

![ Source code files must be in the src directory. Header files (.h files) must be in the include directory. Executables must be in the bin directory. doc and lib directories are added when documentation or
library files are part of the repository](/img/fileFolderStructure.jpg =60%x)
