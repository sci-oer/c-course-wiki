
---
title: Typedef and Structs
description: 
published: true
date: 2022-10-28T20:52:17.559Z
tags: 
editor: markdown
dateCreated: 2022-10-28T20:52:17.559Z
---

## Typedef and structs {#typedef-and-structs .unnumbered}

It is often convenient to create a typedef as an alias to your structs.
A typedef can be used in place of the struct name and means that the
programmer can type only one word instead of two when declaring
variables.

A typedef should usually be placed immediately after the structure
definition. Once a struct has a typedef the typedef word can be used to
declare variables. See the code below for an example of a typedef and a
variable declaration using the typedef.


    struct Student
    {
      char * firstName;
      char * surname;
      int studentID;
      int GPA;
    };

    typedef struct Student StudentRec;


    StudentRec * myStudent = malloc(sizeof(StudentRec));
