---
title: StructuresWithPointersAsElements
description: 
published: 1
date: 2023-02-23T01:26:27.317Z
tags: 
editor: markdown
dateCreated: 2023-02-23T00:26:29.439Z
---


## Structures with Pointers as elements 

When a structure contains an element that is a pointer, that element must always be dynamically allocated before it can be used. This is true even if the structure itself is statically allocated.

```c
/*structure definition-no allocation happening here */
    struct Student
    {
      char * firstName;
      char * surname;
      int studentID;
      int GPA;
    };
```

```c
    int main(void){
      int bufSize = 50;

      /*structure allocation- static */
      struct Student myFirstStudent;
      myFirstStudent.firstName = malloc(sizeof(char)*bufSize);
      myFirstStudent.surname = malloc(sizeof(char)*bufSize);
      strcpy(myFirstStudent.firstName, "Pebbles");
      strcpy(myFirstStudent.surname, "Flintstone");
     
      /*structure allocation- dynamic */
      struct Student * mySecondStudentPtr;
      mySecondStudentPtr = malloc(sizeof(struct Student));
      mySecondStudentPtr->firstName = malloc(sizeof(char)*bufSize);
      mySecondStudentPtr->surname = malloc(sizeof(char)*bufSize);
      strcpy(mySecondStudentPtr->firstName, "Bam Bam");
      strcpy(mySecondStudentPtr->surname, "Rubble");

      /*printing */
      printf("The first student is: %s %s\n", myFirstStudent.firstName, myFirstStudent.surname);
      printf("The second student is: %s %s\n", mySecondStudentPtr->firstName, mySecondStudentPtr->surname);
      return(0);
    }
```