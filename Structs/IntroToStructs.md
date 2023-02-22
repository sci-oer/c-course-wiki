
---
title: Intro to Structs
description: 
published: true
date: 2022-10-28T20:52:17.559Z
tags: 
editor: markdown
dateCreated: 2022-10-28T20:52:17.559Z
---


## Intro to Structs

Structures are a programmer-defined data type that permit the programmer
to group disparate types of data. You use the key word *struct* to
indicate the definition of a structure data type.

    struct Date
    {
        int day;
        int month;
        int year;
    };
    Notice the extra semicolon after the last brace.  Its important.

Once a structure is defined, variables can be defined to be of the
defined data type. The grouped members of the structure are accessed
using the *dot* operator (a period), or through the -\> operator if the
struct has been dynamically allocated.

The contents of a structure can be any valid C data type.

    struct Student
    {
      char * firstName;
      char * surname;
      int studentID;
      int GPA;
     };

When the members (elements) of a structure are pointers, those elements
must be dynamically allocated before being used.
