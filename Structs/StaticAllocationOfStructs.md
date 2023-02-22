
---
title: Static Allocation of Structures
description: 
published: true
date: 2022-10-28T20:52:17.559Z
tags: 
editor: markdown
dateCreated: 2022-10-28T20:52:17.559Z
---

## Static Allocation of Structures {#static-allocation-of-structures .unnumbered}

Structures can be statically allocated (from the stack) just like other
variable types.

    struct Date
    {
      int day;
      int month;
      int year;
    };

    int main(void)
    {

      /*structure allocation- static (because there is no malloc) */
      struct Date birthday;
      birthday.day = 15;
      birthday.month = 11;
      birthday.year = 1800;
      printf("Your birthday is the \%d day of the \%d month in \%d\n", birthday.day, birthday.month, birthday.year);
      return(0);
    }
