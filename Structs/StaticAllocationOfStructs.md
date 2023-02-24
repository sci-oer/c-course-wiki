---
title: StaticAllocationOfStructs
description: 
published: 1
date: 2023-02-24T17:50:22.708Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:35:10.495Z
---

## Static Allocation of Structures 

Structures can be statically allocated (from the stack) just like other variable types.

First define the structure such as the following definition of  a Date.
```c
    struct Date
    {
      int day;
      int month;
      int year;
    };
```
Then one can use the struct as a variable type and static memory allocation is the same as for any other type of variable.

```c
int main(void){

      /*structure allocation- static (because there is no malloc) */
      struct Date birthday;
      birthday.day = 15;
      birthday.month = 11;
      birthday.year = 1800;
      printf("Your birthday is the \%d day of the \%d month in \%d\n", birthday.day, birthday.month, birthday.year);
      return(0);
    }
````