---
title: CompilersAndInterpreters
description: 
published: 1
date: 2023-02-24T02:38:54.327Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:34:44.232Z
---


# Compilers and Interpreters 
- Mini Lecture(video) [Compilers vs Interpreters](http://localhost:8000/lectures/Compilers/Compilers_CompilersVsInterpreters/)
- Mini Lecture(video) [Using Gcc](http://localhost:8000/lectures/Compilers/Compilers_GCCExample/)

Compilers know about the details of the operating system that they are being run on and create a program that is suited to that specific operating system.

Compilers convert source code (human readable, text editor) to binary code that is machine readable. You use the compiler program (gcc) to convert your source code into something the computer can run as a program.

To use the `gcc` compiler type `gcc cfilename.c -o whatyouwantyourexecutablecalled`
`-o` means name the output with the name following the -o. Without the `-o` you get `a.out` as your output file

You can send gcc flags that tell it to alter the rules it uses. Many beginner programmers are taught to use `-Wall` and `-std=c99` and `-pedantic` flags because they provide helpful information for beginners.   `-Wall` turns on warning flags about many things including return types, array
bounds, unused variables and functions, implicit definitions, etc.`-stc=c99` makes sure your code conforms to the ISO C99 dialect of C. `-pedantic` tells the compiler to ensure that your code conforms exactly to the ISO standard.

![This figure shows you the compilation process. The compile step creates an output file for each source code file that is named in the compile command. The linking step uses those .o files to create a single executable. You can only have one main function for each compile command.](/img/compilationVis.jpg =50%x)

You can use path names within your gcc commands `gcc src/filename.c -o bin/myexecutable`. This lets you keep your directories organized and tidy. You can compile more than one program at a time like this: `gcc src/filename1.c src/filename2.c src/filename3.c`

**file naming**
- windows keeps track of files types by extensions for the most part. So it knows that a file can be 'run' because the file ends in .exe. 
- Other operating systems don't use that convention.
- you won't  have .exe at the end of the files that are executable when you program in c


#### Interpreters
Interpreters are different than compilers. For example, Java is an interpreted language.

The source code is read by a program that creates  intermediate code which is then 'run' by an intepreter. The interpreter must run every time the program is run.

Interpreted software is useful when you want to have a program that can run on many operating systems. You create the bytecode once, and then only need to have the interpreter available for each operating sytem.


