---
title: IntroToStrings
description: 
published: 1
date: 2023-02-24T02:36:05.100Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:35:02.534Z
---


## Intro To Strings

- Interactive tutorial for this topic: [ Tutorial](http://localhost:8888/lab/tree/tutorials/Strings/IntroToStrings.ipynb)

A string is just an array of characters in C declared by `char * stringVar`. You have to dynamically allocate memory for a string. `stringVar = malloc(sizeof(char)\*lengthYouWant);` The figure below shows a 	`char *` pointer (stringVar) pointing at some allocated memory. The actual values of the characters in the string would be stored in that allocated memory. The final element of the string array is always a *null terminator* which is indicated by placing a `'\0'`  as the last character of the string.

![grid with an arrow pointing at one square that is labelled stringvar. a second arrow points to a different location in the grid.  the second location is labelled 'location of malloc'd memory'](/img/strings1.jpg =50%x)

Any number of pointers can point to the same string in memory. Assigning one pointer to be equal to another pointer simply gives the two pointers the same address. In the next figure you can see two pointers that are both pointing to the same location in memory. This could have been accomplished by an assignment statement something like `str2 = stringVar;`. If a change is made to the string, the change is reflected in both variables.
![same as above image with the addition of a third labeled square called str2. an additional arrow leads from str2 to the section labelled as 'location of malloc'd memory. ](/img/strings2.jpg =50%x) 
