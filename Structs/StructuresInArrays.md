---
title: StructuresInArrays
description: 
published: 1
date: 2023-02-23T01:24:53.553Z
tags: 
editor: markdown
dateCreated: 2023-02-23T00:26:28.256Z
---



## Structures in Arrays  

Structures can be used as the type of a statically declared array. You declare the array with the structure type instead of something like int or char.

```c
int main(void){
    int CLASS_SIZE = 180;
    int i;
    struct Student listOfStudents[CLASS_SIZE];
    for(i=0; i<CLASS_SIZE; i++){
        loadStudentRecord(&listOfStudents[i], "lastname", "firstname", 10, 4);
       }
```
Structures can also be used as the data type for a dynamically declared
array.
```c
 int main(void){
    int CLASS_SIZE = 180;
    int i;
    struct student * list = malloc(sizeof(struct student)*CLASS_SIZE);
    for(i=0; i<CLASS_SIZE; i++){
        loadStudentRecord(&list[i], "lastname", "firstname", 10, 4);   
    }
} 
```
> note that the above code puts the same value in all records, it needs to be fixed to be useful
{.is-warning}

