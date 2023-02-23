---
title: FreeingMemoryFromStructs
description: 
published: 1
date: 2023-02-23T01:07:00.312Z
tags: 
editor: markdown
dateCreated: 2023-02-23T00:26:21.284Z
---


## Freeing Memory from Structures 

When freeing memory used by structures you must pay attention to how many times malloc was called and remember to free that much memory. In the case of the student structure, there are two char\* elements that are malloced when the structure is loaded. This means that before the pointer to the structure is freed, you must free the pointers to last name and first name.

```
int main(void)
     {
        struct student * studentPtr;
        studentPtr = malloc(sizeof(struct student));
        loadStudentRecord(studentPtr, "Pebbles", "Flintstone", 12345, 5);
        printStudentRecord(studentPtr);
        free(studentPtr->firstName); /*must do this before freeing studentPtr */
        free(studentPtr->surname);
        free(studentPtr);
     }
```
It is good practise to write a function that frees all the memory for a struct. That way the programmer using your struct doesn't have to manually free each member. A free function is simple to write, just remember to free member memory before freeing the struct itself. An example for the student struct is below.

```
void freeStudent(struct Student * toBeFreed)
    {
      free(toBeFreed->firstName);
      free(toBeFreed->surname);
      free(toBeFreed);
     }
```