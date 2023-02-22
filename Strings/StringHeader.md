
---
title: The String Header File
description: 
published: true
date: 2022-10-28T20:45:39.331Z
tags: 
editor: markdown
dateCreated: 2022-10-28T20:45:39.331Z
---

## string.h {#string.h .unnumbered}

The string library for C has many very useful functions that help you
work with strings.

If you need a copy of a string, you should use strcpy **syntax:
strcpy(char \* target, char \* source)** Strcpy copies the entire string
including the \\0 at the end. You MUST ensure that the **target** for
strcpy has enough memory to holde the string you copy into it.

Recall that an ealier example used strlen to find the size of memory to
malloc. **syntax: strlen(char \* theString)** Strlen returns the length
of the string, without the \\0 When you malloc, you must include room
for the \\0, so you add one to the return value from strlen.

*strcat* concatentates two strings into one string. **syntax:
strcat(string1, string2)** Strcat copies the contents of string2 onto
the end of string1. String1 needs to have enough memory allocated to
hold all the extra characters. Strcat adds the null terminator to the
string (\\0) and returns a pointer to the concatenated string (string1).

Strings are compared using the strcmp function. **syntax: strcmp(char \*
str1, char \* str2)** The return value for strcmp is important.

-   \>0 means that str1 is larger

-   0 means that they are equal

-   \<0 means that str2 is larger

For strings, 'larger' means that it comes later in the alphabet, so
Sneezy is 'larger' than Doc. In fact, strcmp compares based on
**lexicographical order**. This is also known as *alphabetical order*
and *dictionary order*.

-   Upper case is not the same as lower case which means that *Sneezy*
    and *sneezy* are not the same word.

-   Numerals are not "numbers" in a string, they are characters and have
    an order

-   Symbols, including the space, have a value and affect the order

Below is one possible implementation for strcmp. Trace through it so
that you understand how the function is working.


    int  strcmp (char *str1, char * str2) { 
       char char1, char2; 
    do { 
       char1 = *str1++; 
       char2 = *str2++; 
       if (char1 == '\0') 
       return char1 - char2; 
        } while (char1 == char2); 
     return char1 - char2; 
    } 

A common string processing application is to break a string up into
smaller parts.Usually the string is *delimited*, which means that there
is one symbol in the text that signifies the end of one unit of text and
the beginning of another. Commas and spaces are common delimiters for
text as are semi-colons and tabs. Each unit of text is called a *token*

For example, if the string was *Snow White, Sleepy, Doc Watson, Happy*,
it would into 4 tokens if a comma was the delimiter, but 6 tokens if the
space was the delimiter.

**strtok** is a string function for C that can be used to tokenize a
string. strtok takes a pointer to the string, and the delimiter as
parameters. strtok returns a pointer to the next token in the string
strtok uses a static local variable to keep track of which token is the
next one to be returned, which means that strtok can only work with one
string at at time. If you call it with a new string, you will lose the
tokens in the old string. strtok returns NULL when it runs out of tokens
**syntax: char \* nextToken = strtok(theString, ",");**

It is important to remember that strtok alters the string that is given
as a parameter. This can sometimes cause errors and seg faults in code
if the programmer forgets that the string has been altered. Figure
[\[strtok1\]](#strtok1){reference-type="ref" reference="strtok1"} shows
a string in memory before strtok is called.

The first time strtok is called, it is sent the pointer to a string and
the delimiter to be used. Strtok replaces the first instance of the
delimiter with a null terminator and then stores the beginning of the
rest of the string in its static variable. Finally it returns the
pointer to the first token in the string. Figure
[\[strtok2\]](#strtok2){reference-type="ref" reference="strtok2"} shows
the string in memory after the first call to strtok.

![image](/img/strtok1.jpg) []{#strtok1 label="strtok1"}

![image](/img/strtok2.jpg) []{#strtok2 label="strtok2"}

Subsequent calls to strtok (for the same string) are made with a NULL
parameter instead of the string. Strtok continues to replace a delimiter
with the null terminator each time a call is made, store the next
starting point in its static variable and return a pointer to the most
recent token. It returns NULL when it runs out of tokens.

![image](/img/strtok3.jpg) []{#stri2 label="stri2"}
