---
title: FreeingMemory
description: 
published: 1
date: 2023-02-24T18:44:16.254Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:34:58.091Z
---



# Freeing Memory 
- Interactive tutorial for this topic: [Freeing Memory Tutorial](http://localhost:8888/lab/tree/tutorials/PointersAndDynamicMemory/FreeingMemory.ipynb)

Whenever you allocate memory from the heap, you must also free it. Even if you allocate memory from within a function, it must be freed somewhere. This is only true for heap memory (stuff you allocate with malloc).

You must free memory in the reverse order that you allocate it for arrays of more than one dimension. For example for a 2D array you should do the following:

-   start with the actual elements of the array and free those
-   then free the pointer to the array

Consider the code shown below that reads a list of names from a file.  It allocates memory for an array of `char*` pointers and then proceeds to create a string for each name in the file and assign it a position in the array.

On line 40, the program begins to free the allocated memory.  Notice that it first loops through the array and frees each string, and then finally it frees the memory for the array.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>


int main(void)
{

int i; 
char ** namePtr;
int numOfNames = 10;
int lengthOfNames = 20;
char * name;
FILE *filePointer;

/* opening the file*/
filePointer = fopen("names.txt", "r");
if (filePointer == NULL) 
{
    printf("File not found\n");
    exit(0);
    }
/* allocating memory for the array*/
namesArrayPtr = malloc(sizeof(char *) * numOfNames);

/*reading in each name, allocating memory, copying the name into the new memory*/
for (i = 0; i < numOfNames; i++) 
{
 namesArrayPtr[i] = malloc(sizeof(char)*lengthOfNames);
 if (fscanf(filePointer, "%s", name)!= EOF)
  {
   strcpy(namesArrayPtr[i], name);
  }
  else
  {
    strcpy(namesArrayPtr[i], "placeholder");
   }
 }
 
 /* now free the memory in the reverse order*/
 for (i = 0; i < numOfNames; i++) 
{
 printf("%s\n", namesArrayPtr[i]);
 free (namesArrayPtr[i]);
 namesArrayPtr[i] = NULL; 
 }
free(namesArrayPtr);

return(0);
}
```