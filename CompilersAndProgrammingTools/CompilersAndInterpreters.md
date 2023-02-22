---
title: Compilers and Interpreters
description: An introduction to the differences between compilers and interpreters
published: 1
date: 
tags: 
editor: markdown
dateCreated: 
---


# Compilers and Interpreters {#compilers-and-interpreters .unnumbered}

-   to call the c compiler (we use gcc) type gcc lab.c -o labExecutable

-   -o means name the output with the name following the -o. Without the
    -o you get a.out as your output default

-   naming conventions\... windows keeps track of files types by
    extensions for the most part. So it knows that a file can be 'run'
    because the file ends in .exe. Other operating systems don't do
    that\.... any file can be 'run' if it is executable\... sometimes
    that gives unpredictable results. But the end of this digression is
    that you don't have .exe at the end of your executables (and
    shouldn't for this class).

-   Compilers know about the details of the operating system that they
    are being run on and create a program that is suited to that
    specific operating system.

Compilers convert source code (human readable, text editor) to binary
code that is machine readable. You use the compiler program (gcc) to
convert your source code into something the computer can run as a
program.

We use gcc as our c compiler. To use it type gcc sourceCodeFileName.c -o
outPutFileName. -o means name the output with the name following the -o.
Without the -o you get a.out as your output default.

You can also send gcc flags that tell it to alter the rules it uses. For
this class you must use -Wall and -std=c99 and -pedantic flags. -Wall
turns on warning flags about many things including return types, array
bounds, unused variables and functions, implicit definitions, etc.
-stc=c99 makes sure your code conforms to the ISO C99 dialect of C.
-pedantic tells the compiler to ensure that your code conforms exactly
to the ISO standard.

![This figure shows you the compilation process. The compile step
creates an output file for each source code file that is named in the
compile command. The linking step uses those .o files to create a single
executable. You can only have one main function for each compile
command.](/img/compilationVis.jpg)

You can use path names within your gcc commands *gcc src/filename.c -o
bin/myexecutable*. This lets you keep your directories organized and
tidy. You can compile more than one program at a time like this: *gcc
src/filename1.c src/filename2.c src/filename3.c*

-   Interpreters are different. (Java is intepreted).

-   The source code goes into a 'compiler' and is turned into
    intermediate code which is then 'run' by feeding it into an
    intepreter. The interpreter is running every time the program is
    running

-   this is useful when you want to have a program that can run on many
    operating systems. You compile it once, and then only need to have
    the interpreter available for each operating sytem.

-   Interpreted programs are sometimes a bit slower than compiled
    programs, they sometimes require more memory to operate, and
    sometimes they don't interface quite as well with hardware devices.
