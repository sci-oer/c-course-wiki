
---
title: Structs as Parameters to Functions
description: 
published: true
date: 2022-10-28T20:52:17.559Z
tags: 
editor: markdown
dateCreated: 2022-10-28T20:52:17.559Z
---

## Structs as parameters to functions {#structs-as-parameters-to-functions .unnumbered}

Structs can be used as variables and types anywhere that other types can
be used. If you send a struct as a parameter to functions, it makes code
far more readable in many cases. Consider the function below that prints
a student record, and the one to load values into the structure
variables.

     int printStudentRecord(struct Student * studentPtr)
     {
      printf ("%s, %s (%d): %d", studentPtr->surname, studentPtr->firstName, studentPtr->studentID, studentPtr->GPA);
      }
      
      int loadStudentRecord(struct Student * studentPtr, char * first, char * last, int id, int gpa)
      {
     studentPtr->firstName = malloc(sizeof(char)*(strlen(first)+1));
     studentPtr->surname = malloc(sizeof(char)*(strlen(last)+1));
     strcpy(studentPtr->firstName, first);
     strcpy(studentPtr->surname, last);
     studentPtr->studentID = id;
     studentPtr->GPA = gpa;
     }

Once functions such as these are written, the main code becomes far more
readable.

    int main(void)
    {
    struct Student * studentPtr;
    studentPtr = malloc(sizeof(struct Student));
    loadStudentRecord(studentPtr, "Pebbles", "Flintstone", 12345, 5);
    printStudentRecord(studentPtr);
    }
