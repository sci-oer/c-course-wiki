
---
title: Intro to Strings
description: 
published: true
date: 2022-10-28T20:45:39.331Z
tags: 
editor: markdown
dateCreated: 2022-10-28T20:45:39.331Z
---

## Intro To Strings

A string is just an array of characters in C declared by *char \*
stringVar*. You have to allocate memory for a string. *stringVar =
malloc(sizeof(char)\*lengthYouWant);* Figure
 [\[str1\]](#str1){reference-type="ref" reference="str1"} shows a char
\* pointer (stringVar) pointing at some allocated memory. The actual
values of the characters in the string would be stored in that allocated
memory. The final element of the string array is always a *null
terminator* which is indicated by placing a '\\0' as the last character
of the string.

![image](/img/strings1.jpg) []{#str1 label="str1"}

Any number of pointers can point to the same string in memory. Assigning
one pointer to be equal to another pointer simply gives the two pointers
the same address. In Figure [\[stri2\]](#stri2){reference-type="ref"
reference="stri2"} you can see two pointers that are both pointing to
the same location in memory. This could have been accomplished by an
assignment statement something like *str2 = stringVar;*. If a change is
made to the string, the change is reflected in both variables.

![image](/img/strings2.jpg) []{#stri2 label="stri2"}
