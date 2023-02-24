---
title: PointersInMemory
description: 
published: 1
date: 2023-02-24T18:25:28.690Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:35:00.756Z
---



# Pointers in memory 
- Interactive tutorial for this topic: [Pointers in Memory Tutorial](http://localhost:8888/lab/tree/tutorials/PointersAndDynamicMemory/PointersInMemory.ipynb)

For the next few examples, refer to the following small program.
```c
    #include <string.h>
    #include <stdio.h>
    #include <stdlib.h>

    /************
    Function Declarations
    *************/
    char * reverseString(char * aString);

    /*****************
    Main Program
    ****************/
    int main (void){
      char theString[50];
      char * theReversedString;
      printf("Enter a string of less than 50 characters followed by return\n");
      scanf("%s", theString);
      printf("Here is the string you entered: %s\n",theString);
      theReversedString = reverseString(theString);
      printf("Your reversed string: %s\n", theReversedString);
     return(0);
    }

    /**************
    Function Definitions
    ****************/
    char * reverseString(char * aString) {

      char * tempStr;
      char * position;
      int length;
      int i;

      
      length = strlen(aString);
      tempStr = malloc(sizeof(char)*length+1);

      for(i=0; i<length; i++)
        {
          tempStr[length-i-1] = aString[i];
        }
      return tempStr;
    }
```
When a program is run, space is allocated in memory for the different components of the program. When this program is loaded, space is allocated for the function *reverseString()* and for *theString* and *theReversedString*.  The image below shows a yellow section representing memory for a statically allocated string array, and a red section for a `char*` pointer called theReversed string.   There is also a green section shown that represents the memory holding the reverseString function.
![a yellow section representing memory for a statically allocated string array, and a red section for a `char*` pointer called theReversed string.   There is also a green section shown that represents the memory allocated in the reverseString function.](/img/memoryPic1.jpg =50%x)

When the program gets to the point that the function is called, memory must be allocated for the variables that are part of the function.  The next image shows a the function variables (aString, tempStr, and position) in blue.  All of them are pointers so they take up very little room on the grid.   The parameter passed in to the function is copied into the appropriate variable which means that the `aString` variable now points to the static memory holding the string. 
![shows a the function variables (aString, tempStr, and position) in blue.  All of them are pointers so they take up very little room on the grid.   The parameter passed in to the function is copied into the appropriate variable which means that the `aString` variable now points to the static memory holding the string. ](/img/memoryPic2.jpg =50%x) 

During the function call, memory is allocated and a pointer is set to point at that memory. The image shows this temporary memory in red.  Notice that the memory does not have a variable name directly associated with it, but the tempStr pointer is holding the memory address of this memory. 

![shows a temporary chunk of memory allocated by the function in red.   the memory does not have a variable name directly associated with it, but the tempStr pointer is holding the memory address of this memory. ](/img/memoryPic3.jpg =50%x) 

Can you complete the memory map exercise?
When the function returns a value to the main program, what is the value returned? What variable in the main program holds that value?