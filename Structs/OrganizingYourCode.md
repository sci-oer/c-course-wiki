---
title: OrganizingYourCode
description: 
published: 1
date: 2023-02-24T17:49:51.941Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:35:08.437Z
---

## Organizing your Code 

Generally, you should define structures in the header files of your programs. A structure goes in the header file for the source code that provides the functions for operating on the structure.

For example, the structure definition for the student structure might be found in a student.h file, while the `loadStudentRecord` and `printStudentRecord` functions would be in a students.c file. Other functions that provided ways to operate on that same structure would be found in the same file (such as a `sortRecords` function and a `calculateGPA ` function)

Structs can be used as a variable type anywhere it is valid to have a type. Structs can be parameters to functions. A pointer to a struct can be a return type. Structs can be placed in arrays (and trees, and heaps, and stacks, and lists, and all other data types). Structs can make your code much more maintainable and readable.



**student.h**
```c
    struct Student
    {
      char * firstName;
      char * surname;
      int studentID;
      int GPA;
    };


    int printStudentRecord(struct Student * studentPtr);
    int loadStudentRecord(struct Student * studentPtr, char * first, char * last, int id, int gpa);
```

**student.c**
```c
    #include <string.h>
    #include <stdlib.h>
    #include <stdio.h>
    #include "student.h"

    int printStudentRecord(StudentRec * studentPtr)
     {
      printf ("%s, %s (%d): %d\n", studentPtr->surname, studentPtr->firstName, studentPtr->studentID, studentPtr->GPA);
      }
      
    int loadStudentRecord(StudentRec * studentPtr, char * first, char * last, int id, int gpa)
    {
     studentPtr->firstName = malloc(sizeof(char)*(strlen(first)+1));
     studentPtr->surname = malloc(sizeof(char)*(strlen(last)+1));
     strcpy(studentPtr->firstName, first);
     strcpy(studentPtr->surname, last);
     studentPtr->studentID = id;
     studentPtr->GPA = gpa;
     }
```

The code given shows the code for loading and printing students rearranged into the proper file structure. As you can see, the main file becomes far more readable once the functions are used.

**main.c**
```c
    #include <stdlib.h>
    #include "student.h"
     
    int main(void)
    {
    struct Student * studentPtr;
    studentPtr = malloc(sizeof(struct Student));
    loadStudentRecord(studentPtr, "Pebbles", "Flintstone", 12345, 5);
    printStudentRecord(studentPtr);
    }
```