
---
title: Structures in Arrays
description: 
published: true
date: 2022-10-28T20:52:17.559Z
tags: 
editor: markdown
dateCreated: 2022-10-28T20:52:17.559Z
---

## Structures in Arrays  {#structures-in-arrays .unnumbered}

Structures can be used as the type of a statically declared array. You
declare the array with the structure type instead of something like int
or char.

    int main(void)
    {
    int CLASS_SIZE = 180;
    int i;
    struct Student listOfStudents[CLASS_SIZE];
    for(i=0; i<CLASS_SIZE; i++)
        loadStudentRecord(&listOfStudents[i], "lastname", "firstname", 10, 4);
       }
    /*note that this code puts the same value in all records, it needs to
    be fixed to be useful*/

Structures can also be used as the data type for a dynamically declared
array.

    int main(void)
    {
    int CLASS_SIZE = 180;
    int i;
    struct student * list = malloc(sizeof(struct student)*CLASS_SIZE);
    for(i=0; i<CLASS_SIZE; i++)
    {
        loadStudentRecord(&list[i], "lastname", "firstname", 10, 4);
       
    }
    } 

    /*note that this code puts the same value in all records, it needs to
    be fixed to be useful*/
