---
title: StructuresInArrays
description: 
published: 1
date: 2023-02-24T17:59:00.757Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:35:12.258Z
---

## Structures in Arrays  

Structures can be used as the type of a statically declared array. You declare the array with the structure type instead of something like int or char.

Given the following struct defintiion:
```c
    struct Student
    {
      char * firstName;
      char * surname;
      int studentID;
      int GPA;
    };
```
We can make a statically allocated array of students as shown below.
```c
int main(void){
    int CLASS_SIZE = 180;
    int i;
    struct Student listOfStudents[CLASS_SIZE];
    for(i=0; i<CLASS_SIZE; i++){
        loadStudentRecord(&listOfStudents[i], "lastname", "firstname", 10, 4);
       }
```
Structures can also be used as the data type for a dynamically declared
array.
```c
 int main(void){
    int CLASS_SIZE = 180;
    int i;
    struct student * dynamicListofStudents = malloc(sizeof(struct student)*CLASS_SIZE);
    for(i=0; i<CLASS_SIZE; i++){
        loadStudentRecord(&dynamicListofStudents[i], "lastname", "firstname", 10, 4);   
    }
} 
```
> note that both of these code samples assign the same values to all records.   That isn't a useful behaviour for a real program.
{.is-warning}

