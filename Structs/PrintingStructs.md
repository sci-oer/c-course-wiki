---
title: PrintingStructs
description: 
published: 1
date: 2023-02-24T17:55:38.139Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:35:09.618Z
---

## Printing 

When writing print functions, it is better to write a function that returns a formatted string than to actually do the printing. That allows the programmer who is using your module to decide whether the output is printed to stdout or someplace else, and it lets the programmer decide how to embed your string into other output.

When writing a print function for a struct, try to keep decorations to a minimum and just provide a nicely formatted printing of the information in the struct. Let the programmer using the struct add the decoration. (Or provide two functions, one with and one without decoration).

A print function using sprintf for the student struct might look something like this:


``` c  
    char * printStudent(struct Student * toPrint)
    {
    /*first find out how much space you need I used +30 so I could have some labels and the id and GPA */
       int length = strlen(toBePrinted->firstName) + strlen(toBePrinted->surname) + 30;
       /*I am mallocing memory in a function- which means it needs to be freed someplace else */
      char * printBuf = malloc(sizeof(char)*length);
      sprintf(printBuf, "%s, %s (%d) GPA: %d", toBePrinted->surname, toBePrinted->firstName,  toBePrinted->studentID, toBePrinted->GPA);
      return(printBuf); /* the code calling this print routine needs to free up the memory I am sending a pointer to */
     }
```