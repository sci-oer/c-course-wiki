---
title: The Preprocessor
description: Discussing the Preprocessor
published: 1
date: 
tags: 
editor: markdown
dateCreated: 
---

## The Preprocessor {#the-preprocessor .unnumbered}

The preprocessor is a program that runs BEFORE the compiler. It does
three things- all of which are essentially search/replace on the text.

1.  **macro processing.** Macros are defined values or operations that
    are substituted into the text. Its just a strict text substitution.
    It makes your code a bit more readable and means that if you have to
    change the definition, you do it in one place- but you don't have to
    define functions. It is sometimes tricky to get right- don't try to
    to get too fancy with it.

    -   #define LOONIE 100

    -   in the source code, all occurrences of LOONIE will be replaced
        by 100. By convention macros are capital letters. The \# sign is
        the key

    -   put macros at the beginning, after the #includes

    -   #define SQUARE(a) ((a)\*(a))

    -   #define MAX(a,b) ((a)\<(b)?(b):(a))

    -   its a good idea to completely parenthesize\... else the
        expansion can bite you.

2.  **including header files**

    -   the #include is actually a call to the preprocessor. It goes
        off, gets the referenced files, and copies the contents into
        that spot in the source code.

    -   #include \"\" means look in current directory

    -   #include \<\> means look in library directories

    -   its important to know where those library paths are. EASY to
        control them on the command line. REALLY HARD on some
        pointy-clickies

3.  **conditional compilation**- lets you tell the compiler whether or
    not to include parts of the code. Really useful for debugging

    -   #define DEBUG 0 (0 is false)

    -   #if DEBUG \... print debugging information

    -   #endif (must include this)

The preprocessor is most often used for one of three things

-   directives (like include)

-   #include is a directive as are all the conditional compilation
    statemets like #ifdef and #ifndef

-   constants

-   macros

As your code gets to be more complicated, you'll notice that header
files will need to include other header files, and soon you'll have
things declared multiple times. This is especially a problem if you are
defining constants or structs in your header files. Use include guards
to solve the problem

    #ifndef SOME_UNLIKELY_COMBO_OF_WORDS
    #define SOME_UNLIKELY_COMBO_OF_WORDS
    // put your code here
    #endif  

You can define constants (usually in a header file) that are then
available for all programs.

    #define PI 3.14
    #define BAKERSDOZ (12+1)
    #define LIST_H

A defined constant for DEBUG can make it really easy to turn on/off
debugging statements. You can also define the value of a preprocessor
macro on command line with the -D flag to gcc. gcc lab0.c -o lab0
-DDEBUG = 1

    #define DEBUG 1
    .... code.....
    if(DEBUG){
        printf("Removing from list: %d %s\n", getTime(patron),
                                    %getID(patron));
    }

If your constant is a calculation, use parenthesis, else you risk
getting unwanted results. In the example below, p will evaluate to 17.
Make sure you understand why that is the case.

    #define BAKERSDOZ 12+1
    p = BAKERSDOS*5

Macros are a way of writing quick, inline code and making your code more
readable. They are also an easy way to introduce bugs. Use with caution.

    #define PLUSONE(x) x++
    #define MULT(x,y) x*y

A macro is cut/paste EXACTLY into your code at the point that the macro
label is placed. So if you write `int z = PLUSONE(y);` your code will
compile with `int z= y++);` It is really important to remember that
macros are cut/paste in EXACTLY.

    #define MULT(x,y) x*y
    MULT(x+1, y+1);

The call to MULT expands to `x + 1*y + 1'` which is not what was likely
wanted. `#define MULT((x)(y))` is more robust.
