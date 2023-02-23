---
title: TypedefAndStructs
description: 
published: 1
date: 2023-02-23T01:28:06.595Z
tags: 
editor: markdown
dateCreated: 2023-02-23T00:26:30.540Z
---


## Typedef and structs 

It is often convenient to create a typedef as an alias to your structs.
A typedef can be used in place of the struct name and means that the programmer can type only one word instead of two when declaring variables.

A typedef should usually be placed immediately after the structure definition. Once a struct has a typedef the typedef word can be used to declare variables. See the code below for an example of a typedef and a variable declaration using the typedef.

```c
    struct Student
    {
      char * firstName;
      char * surname;
      int studentID;
      int GPA;
    };

    typedef struct Student StudentRec;
```
The typedef can then be used any place the name of the struct would normally be used.
```c
    StudentRec * myStudent = malloc(sizeof(StudentRec));
```