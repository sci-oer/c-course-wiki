---
title: Realloc
description: 
published: 1
date: 2023-02-24T00:07:26.788Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:35:01.647Z
---




# Realloc 

- Interactive tutorial for this topic: [Realloc Tutorial](http://localhost:8888/lab/tree/tutorials/PointersAndDynamicMemory/Realloc.ipynb)

It is possible to increase or decrease the size of allocated memory using realloc. The format of the function call is `realloc(pointerToExistingMemory, NewSizeInBytes);`

Its important to note that the new size is the total size desired, not just the additional size.
```c
    char * ptr;
    char * largerPtr;
    ptr = malloc(sizeof(char) * 10);
    strcpy (ptr, "dinosaurs"); /*the string is now full- lets say we wanted to add  " are extinct" */
    largerPtr = realloc(ptr, sizeof(char) *22);  /* now there is room for the rest of the words*/
    strcpy largerPtr ("dinosaurs are extinct");
```
You can also just reuse the original pointer so that your code looks like this:
   ` ptr = realloc(ptr, sizeof(char) *22);` 

In this case the original value of ptr is overwritten with the new value from realloc. This is almost always the desired outcome. 
Realloc returns NULL if there is an error condition. How would that affect the previous snippet of code?

Realloc does one of three things:
-   if there is enough space to simply expand the current block of memory, the additional memory is allocated and realloc returns the original value of myPtr;
-   if there is enough memory, but not in the current location, a new block of memory is allocated elsewhere, the data is copied from the old block to the new block, the old block of memory is freed and the address of the new block of memory is returned.
-   if there is not enough memory, realloc returns a null pointer, but does not free the memory from the original block. (you can accidentally overwrite a pointer this way)

If you send a NULL to realloc as the first argument, it acts like malloc
`otherPtr = realloc(NULL, sizeof(char) * 100);`.

If you send a 0 to realloc as the second parameter, the memory is freed and NULL is returned `otherPtr = realloc(otherPtr,0);` Generally it is better practice to use the function for its purpose and not overload it to do something that other functions are meant to do.

