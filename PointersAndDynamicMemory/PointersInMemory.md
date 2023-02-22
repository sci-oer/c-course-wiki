
---
title: Pointers in Memory
description: 
published: true
date: 2022-10-28T20:59:34.191Z
tags: 
editor: markdown
dateCreated: 2022-10-28T20:42:21.376Z
---

## Pointers in memory {#pointers-in-memory .unnumbered}

For the next few examples, refer to the following small program.

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

When a program is run, space is allocated in memory for the different
components of the program. When this program is loaded, space is
allocated for the function *reverseString()* and for *theString* and
*theReversedString*. See Figure  [\[mem1\]](#mem1){reference-type="ref"
reference="mem1"}.

![image](/img/memoryPic1.jpg) []{#mem1 label="mem1"}

When the program gets to the point that the function is called, memory
must be allocated for the variables that are part of the function. The
parameter passed in to the function is copied into the appropriate
variable. In this case an address is passed in and copied to a pointer.
See Figure  [\[mem2\]](#mem2){reference-type="ref" reference="mem2"}.

![image](/img/memoryPic2.jpg) []{#mem2 label="mem2"}

During the function call, memory is allocated and a pointer is set to
point at that memory. Notice that the memory does not have a variable
name directly associated with it, only a pointer pointing at it. See
Figure  [\[mem3\]](#mem3){reference-type="ref" reference="mem3"}.

![image](/img/memoryPic3.jpg) []{#mem3 label="mem3"}

When the function returns a value to the main program, what is the value
returned? What variable in the main program holds that value?
