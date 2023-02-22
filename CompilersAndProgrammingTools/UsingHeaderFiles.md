---
title: Header Files
description: What Header files are and how to use them
published: 1
date: 
tags: 
editor: markdown
dateCreated: 
---

## Using header files {#using-header-files .unnumbered}

Header files (.h files) contain function prototypes (and sometimes other
information like struct definitions). Source files contain the function
definitions, main, and sometimes macros for the preprocessor.

For example, suppose I was writing a program called myprog. In myprog.h
I woud prototype a function.

    int myFunct(int);

In myprog.c I would define the function completely. Use the same naming
convention for .h files and .c files so that it is always obvious which
.ht file belonts with which .c file.

    int myFunct(int myVar){
       return(myVar + 10);
    }

Now I can use the function I defined in myprog.c in a program. In the
file with main (myMain.c for lack of a better name) I would first
include the .h file and then define main.

    #include "myprog.h"

    int main(){
      int someVariable;
      
       someVariable = 8;
       someVariable = myFunc(someVariable);
       printf("%d \n", someVariable);
       return(0);
     }

It really isn't difficult to keep your source files organized, and it
makes it much easier to manage larger projects if you have good work
habits already.