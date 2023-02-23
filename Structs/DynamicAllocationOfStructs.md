---
title: DynamicAllocationOfStructs
description: 
published: 1
date: 2023-02-23T01:04:35.906Z
tags: 
editor: markdown
dateCreated: 2023-02-23T00:26:20.128Z
---



## Dynamic Allocation of Structures 

Structures are allocated dynamically using malloc. The elements (members) of the structure are accessed using the `-> ` operator when the structure has been allocated dynamically.

```
/*structure definition- does not allocate any variables */
       struct Date
       {
           int day;
           int month;
           int year;
       };
    int main(void)
    {
       /*structure allocation- dynamic allocation with malloc and a pointer*/
       struct Date * datePtr;
       datePtr = malloc(sizeof(struct Date));
       datePtr->day = 15;
       datePtr->month = 11;
       datePtr->year = 1800;
       printf("Your birthday is the %d day of the %d month in %d", datePtr->day, datePtr->month, datePtr->year);
        return(0);
     }
```

Don't be tempted to calculate the size of the structure for malloc by summing the parts, the size usually isn't an exact sum of the parts. Let malloc calculate the size on its own.
