---
title: Two Dimensional Arrays
description: 
published: true
date: 2022-10-28T23:43:34.835Z
tags: 
editor: markdown
dateCreated: 2022-10-28T19:00:47.729Z
---

## Two Dimensional Arrays {#two-dimensional-arrays .unnumbered}

One common application for two dimensional arrays in C is an array of
words.

A two dimensional array is a set of pointers to arrays, or an array of
pointers.

In figure  [\[2d2\]](#2d2){reference-type="ref" reference="2d2"} you can
see the declaration and memory allocation for an array of array
pointers. Because the contents of the array will be pointers, the type
given to malloc is *char \** and the type of the variable
*listOfNamesPtr* is char \*\*. The result of the statement shown in the
figure is an array of pointers, but none of the pointers are pointing to
allocated memory yet.

![image](/img/twoDArray2.jpg) []{#2d2 label="2d2"}

In Figure  [\[2d1\]](#2d1){reference-type="ref" reference="2d1"} you can
see the declaration and memory allocation for a char \* variable called
stringPtr. The pointer holds the memory address of the first piece of
memory that was allocated by malloc.

![image](/img/twoDArray1.jpg) []{#2d1 label="2d1"}

    char ** nameArray;
    nameArray = malloc(sizeof(char *)*numberOfNames);
    if(nameArray == NULL){printf("Out of memory: exiting\m"); exit(1);}
    for(i = 0; i<numberOfNames; i++){
      nameArray[i]=malloc(sizeof(char)*stringSize);
      if(nameArray[i] == NULL){printf("Out of memory: exiting\m"); exit(1);}
    }

In Figure  [\[2d3\]](#2d3){reference-type="ref" reference="2d3"} you see
illustrated the listOfNamesPtr elements, each pointing to memory that
was allocated specifically for that row. The memory for each row of the
2d array must be allocated, usually by using a for-loop. An example is
shown below. It is important to remember that the array has no data in
it after the memory is allocated, it simply has memory ready to be used.
The code sample shows one way to allocate memory for a 2D string array.

![image](/img/twoDArray3.jpg) []{#2d3 label="2d3"}
