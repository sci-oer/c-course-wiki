---
title: Programming Projects
description: Introduction to reasonable directory structures for C projects
published: 1
date: 
tags: 
editor: markdown
dateCreated: 
---

## Programming Projects {#programming-projects .unnumbered}

University assignments tend to be very small when compared to projects
that result in programs that the general population uses. Have a look at
the source code for VLC (the media player) for an example of a
relatively small program. Look through the folders and files to get a
sense of just how many lines of code go into that sort of a program.

A project of any size will require multiple source code files, and
programmers must learn to manage larger projects. Tool that is commonly
used to manage programming projects is a program called make.

Make is installed by default on nearly every \*nix operating system.
Make works by parsing a file (called a makefile) and executing the
commands it finds in the makefile. The makefile must be written in a
particular format, and when it is properly written any command known to
the operating system can be executed.

Make is used to primarily to manage the building of software because its
use ensures that t the same set of tasks will be done in the same order
all of the time. A makefile consists of at least two lines:

    target: dependencies
    [tab]system command

A makefile **should** be named Makefile, but other names can be used. In
my classes I require that students use the name *Makefile*. The target
can be any word. The first target in the makefile is the one that will
execute by default. A makefile is executed via the command line by
typing *make* on the command line from the directory that contains the
makefile. Makefiles can have multiple targets and you can execute a
specific target by typing *make targetname*. It is very important to use
a single *tab* instead of spaces in a makefile. An example makefile for
a simple c program might look like this:

    all:
        gcc -Wall -std=c99 -pedantic src/tictactoe.c src/tictactoefunctions.c -Iinclude -o bin/runMe -lncurses

The makefile above compiles two .c files (one of which has a main),
tells the compiler to look in the include folder for .h files, puts the
resulting executable in a bin folder, and tells the compiler that it
will need to use the ncurses library.

A methodical approach to organizing files along with proper use of
makefiles will greatly reduce the amount of time spent managing software
projects. The file-folder structure that I impose on my classes is shown
in Figure 3.

![I require that my students use the folder structure shown in this
image. Source code files must be in the src directory. Header files (.h
files) must be in the include directory. Executables must be in the bin
directory. doc and lib directories are added when documentation or
library files are included in the student
submission.](/img/fileFolderStructure.jpg)