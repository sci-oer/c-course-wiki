---
title: Malloc
description: 
published: 1
date: 2023-02-24T02:04:05.071Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:34:59.859Z
---



# Malloc 

- Mini Lecture(video)[Pointers and Dynamic Memory](http://localhost:8000/lectures/Memory/Memory_MemoryConceptually/)
- Mini Lecture(video)[Malloc and Free](http://localhost:8000/lectures/Memory/Memory_MallocFreeExample/)

Malloc is the tool you use to ask the computer to reserve heap memory for your programs. You must have stdlib included in order to use malloc. The syntax is as follows:
```c
    malloc(size multiplied by how much)
    malloc(sizeof(char)*10);
```
While you can use any numbers in malloc (say, malloc(10)) it is much better to let the computer allocate the proper amount of memory for the architecture by using the *sizeof* operator.
Malloc returns a pointer to the type of variable in the sizeof operator, so to use the memory allocated by malloc you must assign it to a pointer.
```
    char * myCharPointer = malloc(sizeof(char)*15);
```
If a computer runs out of memory, then a call to malloc will fail. While this doesn't happen often, it is still important to build the habit of checking the return value from malloc to ensure that the memory has been properly allocated. If the pointer is a NULL pointer after malloc, then the memory allocation has failed.
```c
    char * myCharPointer = malloc(sizeof(char)*15);
    if (myCharPointer == NULL) {printf("out of memory: exiting"); exit(1);}
```
# Arrays and Dynamic Memory

- Interactive tutorial for this topic: [Dynamic Two Dimensional Arrays Tutorial](http://localhost:8888/lab/tree/tutorials/PointersAndDynamicMemory/TwoDimensionalArrays.ipynb)

An array of anything can be declared with pointers and malloc. 
- The first step is to declare a pointer of the same type as the intended array. 
- The second step is to malloc enough memory to hold the array and assign the first address of the block of memory to the pointer. 
- The third step is to check to make sure malloc returned usable memory. Now you can use your array.
```c
    int main ()
    {
      int myInt;
      int * dynArray;
      int i;
      srand ( time(NULL) );
      printf("Enter an integer number: ");
      scanf("%d", &myInt);
      dynArray = malloc(sizeof(int)*myInt);
      for(i=0; i<=myInt; i++){
        dynArray[i] = rand()%100;
      }
      for(i=0; i< myInt; i++){
        printf("%d, ", dynArray[i]);
      }
      printf("\n");
    }
```
Consider the program shown above. The array *dynArray* is declared to be an `int *` on line 2. On line 7 that array has memory allocated to hold the number of ints that was indicated by the user input at line 6. One of the for loops puts a random number into each element of the array, the other for loop prints the values in the array. Notice that the square bracket array notation is used to access the elements of the array even though the array was dynamically declared.
It is possible to access array elements by incrementing and decrementing the value of the pointer (pointer math) but this practise results in code that is hard to read and frequently results in bugs and errors. Pointer math is not recommended for most tasks.
Strings in C are just arrays of characters. They are declared as character arrays using pointer notation (`char *`) and must have memory allocated for them before they can be used. The code below shows the declaration, allocation of memory, and assignment of value for a string.
Notice that the call to malloc uses strlen +1. Strlen does not count the null terminator for strings, but it is important to have enough memory to hold the null terminator, so one extra space must be added when using strlen as component of the size calculation for malloc.
```c
    char * myString;
    myString = malloc(sizeof(char)*strlen(("Sneezy")+1));
    strcpy(myString, "Sneezy");
```