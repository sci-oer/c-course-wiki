---
title: ThePreprocessor
description: 
published: 1
date: 2023-02-24T17:36:32.320Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:34:46.892Z
---


## The Preprocessor 
- Mini Lecture(video) [The Preprocessor](http://localhost:8000/lectures/PreProcessor/PreProcessor_Conceptual/)
- Mini Lecture(video) [Preprocessor Example](http://localhost:8000/lectures/PreProcessor/PreProcessor_Example/)

The preprocessor is a program that runs BEFORE the compiler. The preprocessor can be used for three different tasks- all of which are essentially search/replace text.

1. **macro processing.** Macros are defined values or operations that are substituted into the text. It is  a strict text substitution that can be used to make your code a bit more readable and means that if you have to change the definition, you do it in one place- but you don't have to define functions. 

For example, if the macro `#define LOONIE 100` is added to a source file,  all occurrences of LOONIE will be replaced by 100. By convention macros are capital letters. The \# sign is
the signal that a macro is being defined.

- place macros at the top of a file, after the \#includes
    - `#define SQUARE(a) ((a)\*(a))`
    - `#define MAX(a,b) ((a)\<(b)?(b):(a))`
    - its a good idea to completely parenthesize
2.  **including header files** `#include` is actually a call to the preprocessor. When `#include` is encountered, the preprocessor gets the referenced files and copies the contents into that spot in the source code.

`#include` uses two different paths when looking for files. The choice is determined by the way a file is annotated.
    - #include \"filename.h\" means look in current directory for a file named filename.h
    - #include \<filename.h\> means look in library directories for a file named filename.h
 
 Typically system headers are included with `<>` and programmer defined headers are included with `""`  

3.  **conditional compilation** Conditional compilation lets you tell the compiler whether or
not to include parts of the code. This use of preprocessor commangs can be very useful for debugging.


```c
//near the top of the file
#define DEBUG 0 (0 is false)
... //somewhere else in the code
#if DEBUG 
 //print debugging information

#endif //must include this
```
A defined constant for DEBUG can make it really easy to turn on/off debugging statements. You can also define the value of a preprocessor macro on command line with the -D flag to gcc. 
`gcc lab0.c -o lab0 -DDEBUG = 1`

```c
    #define DEBUG 1
    //.... code.....
    if(DEBUG){
        printf("Removing from list: %d %s\n", getTime(patron),%getID(patron));
    }
```


As your code gets to be more complicated, you'll notice that header files will need to include other header files, and soon you'll have things declared multiple times. This is especially a problem if you are defining constants or structs in your header files. Use preprocessor commands as include guards to solve the problem
```c
    #ifndef SOME_UNLIKELY_COMBO_OF_WORDS
    #define SOME_UNLIKELY_COMBO_OF_WORDS
    // put your code here
    #endif  
```
You can define constants (usually in a header file) that are then available for all programs.

```c
    #define PI 3.14
    #define BAKERSDOZ (12+1)
    #define LIST_H
```

If your constant is a calculation, use parenthesis, else you risk getting unwanted results. 

In the example below, p will evaluate to 17. Make sure you understand why that is the case.

```c
#define BAKERSDOZ 12+1
p = BAKERSDOS*5
```
Macros are a way of writing quick, inline code and making your code more readable. They are also an easy way to introduce bugs. Use with caution.

```c
    #define PLUSONE(x) x++
    #define MULT(x,y) x*y
```
A macro is cut/paste EXACTLY into your code at the point that the macro label is placed. So if you write `int z = PLUSONE(y);` your code will
compile with `int z= y++);` It is  important to remember that macros are cut/paste in EXACTLY.

```c
    #define MULT(x,y) x*y
    MULT(x+1, y+1);
```
The call to MULT expands to `x + 1*y + 1'` which is not what was likely wanted. `#define MULT((x)(y))` is more robust.
