---
title: UsingHeaderFiles
description: 
published: 1
date: 2023-02-24T17:38:17.250Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:34:47.791Z
---


## Using header files 

Header files (`.h` files) contain function prototypes (and sometimes other information like struct definitions). Source files contain the function definitions, main, and sometimes macros for the preprocessor.

For example, suppose I was writing a program called myprog. In `myprog.h` I would prototype a function.

```c
int myFunct(int);
```
In `myprog.c` I would define the function completely. Use the same naming convention for .h files and `.c` files so that it is always obvious which `.h` file belongs with which `.c` file.
```c
    int myFunct(int myVar){
       return(myVar + 10);
    }
```
Now I can use the function I defined in myprog.c in a program. In the file with main (`myMain.c` for lack of a better name) I would first include the `.h` file and then define main.
```c
    #include "myprog.h"

    int main(){
      int someVariable;
      
       someVariable = 8;
       someVariable = myFunc(someVariable);
       printf("%d \n", someVariable);
       return(0);
     }
```
The use of header files eliminates the problem of the c compiler needing definitions for functions that will be compiled in subsequent files.  Without header files it is nearly impossible to create large, multi-file c programs.
