---
title: IntroToStructs
description: 
published: 1
date: 2023-02-24T00:04:19.401Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:35:07.332Z
---

## Intro to Structs

Structures are a programmer-defined data type that permit the programmer to group disparate types of data. You use the key word *struct* to indicate the definition of a structure data type.
```
    struct Date
    {
        int day;
        int month;
        int year;
    };
```
> Notice the extra semicolon after the last brace.  It is important.
{.is-info}


Once a structure is defined, variables can be defined to be of the defined data type. The grouped members of the structure are accessed using the *dot* operator (a period), or through the -\> operator if the struct has been dynamically allocated.

The contents of a structure can be any valid C data type.

    struct Student
    {
      char * firstName;
      char * surname;
      int studentID;
      int GPA;
     };

When the members (elements) of a structure are pointers, those elements must be dynamically allocated before being used.
