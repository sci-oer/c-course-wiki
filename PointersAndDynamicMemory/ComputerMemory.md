
---
title: Computer Memory
description: 
published: true
date: 2022-10-28T20:59:34.191Z
tags: 
editor: markdown
dateCreated: 2022-10-28T20:42:21.376Z
---

## Computer Memory {#computer-memory .unnumbered}

Computer memory can be thought of as a huge spreadsheet where every cell
has a unique address If you know the address of the cell, you can find
the value in the cell. You can even 'merge' cells to produce something
that holds longer/larger data. (doubles, strings, floats)

Computer memory is divided into areas( See Figure
 [\[stackheap\]](#stackheap){reference-type="ref"
reference="stackheap"}): the stack, the heap, the text segment and the
data segment. Each part of memory is used slightly differently by
programs.

The text segment is where program instructions are stored during program
execution. The data segment is where things that are known at compiler
time are kept (i.e. globals, literals, things defined with the keyword
'static'). The heap is where dynamically allocated memory is located
(things that you allocate with malloc or calloc), and the stack is where
automatically allocated memory is placed such as variables and
parameters for function calls.

![image](/img/memoryStackHeap.jpg) []{#stackheap label="stackheap"}

C gives you two ways to reserve memory for your program (static and
dynamic).

-   Static Memory (what you have been doing)

    -   int a; char myArray\[\]; double b;

    -   Static memory is reserved by the compiler

    -   your program takes up all the memory even if it doesn't need it

    -   doesn't get any more memory even if it does need it.

    -   int myArray\[100\] means you get 100 ints.. the space for 100
        ints is consumed when your program runs, and if you have 150
        ints, your program can't handle it.

```{=html}
<!-- -->
```
-   Dynamic Memory

    -   reserved by YOU, via your programming

    -   you get exactly as much memory as you need, no waste, no
        overflow

    -   Dynamic memory is allocated while your program runs (run time)

    -   malloc() is the command

    -   You can use a variable to decide how much memory to allocate so
        you get just the right amount.
