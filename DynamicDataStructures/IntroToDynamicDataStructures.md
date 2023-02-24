---
title: IntroToDynamicDataStructures
description: 
published: 1
date: 2023-02-24T19:14:58.313Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:34:49.585Z
---

##  Intro to Dynamic Data Structures 

Usually when we write programs we don't know how many records or data items will be available to the program. Frequently that number isn't known even when data is entered into the program. Data storage structures like arrays are inconvenient because the length must be known in order to allocate memory for the structure before data can be entered.

A second disadvantage of arrays as data structures is seen when trying to keep an array sorted as elements are added.  It can be a complicated and time consuming operation to resort the array each time an element is added.

Linked Data structures solve this problem by allocating exactly enough memory for a single data item, filling the item, linking the new item to the growing data structure and then repeating the process.  This process is repeated for however many items there are.

Such data structures are called **dynamic data structures**. Don't confuse this term with dynamic memory allocation- the word dynamic simply means that it happens as the program is executing, and does not imply that they are the same term. For this course we will limit our discussion of dynamic data structures to linked lists.

##### Pseudocode

Many of the examples in this section will be given in pseudo code that could be used as the outline for a program in nearly any programming language, or in c. The pseudocode format is as follows:

-   function and procedures are defined with a name that begins with a lower case
-   parameters are included as types only
-   if there is a return value, it appears at the end of the function definition after a colon
-   no ending punctuation is used for lines
-   indentation is used rather than parentheses

For example a pseudocode function could be defined as :
```
    calculateComplicateValue(int, String): int
```
If the same function were actually written in a C header file it would look something like this:
```c
     int calculateComplicateValue(int intVal, char * stringVal);
```