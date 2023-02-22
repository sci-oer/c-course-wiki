
---
title: Create Functions for Structs
description: 
published: true
date: 2022-10-28T20:52:17.559Z
tags: 
editor: markdown
dateCreated: 2022-10-28T20:52:17.559Z
---

## Create Functions for Structs {#create-functions-for-structs .unnumbered}

A common oversimplification of how memory is allocated and deallocated
is that all the variables used within a function were deallocated when
the function finished. That is only sort of true. The real situation
requires that you understand the difference between the 'heap' and the
'stack'. The heap and the stack are two different pots of memory that
can be used by your program.

Stack memory is allocated every time you allocate a non-pointer
variable, such as int i, char letter, or struct musicRecord theRecord,
or when you declare a pointer itself without malloc, such as int \*
intPtr;

Heap memory is allocated every time you malloc memory for a pointer
variable such as int \*intPtr = malloc(sizeof(int));, char \*theWord =
malloc(sizeof(char)\*10); or struct musicRecord \*theRecord=
malloc(sizeof(struct musicRecord);

When a function finishes execution, all of the **variables allocated
from the stack** are destroyed and the memory is returned to the stack.
The **heap allocations are not deallocated**. This means that you can
write functions that create, and initialize a struct- doing all of the
mallocing, and just return a pointer to the newly allocated memory. The
value of the pointer will be returned- and the memory will not be freed
because it is on the heap, not the stack.

An create function for the student struct might look like this:


    struct Student * createStudent(char * first, char * last,  int ID, int gradePoint)
    {
     struct Student * newStudent = malloc(sizeof(struct Student));
     newStudent->firstName = malloc(sizeof(char)*(strlen(first)+1));
     newStudent->surname = malloc(sizeof(char)*(strlen(last)+1));
     strcpy(newStudent->firstName, first);
     strcpy(newStudent->surname, last);
     newStudent->studentID = ID;
     newStudent->GPA = gradePoint;
     return(newStudent);
    }
