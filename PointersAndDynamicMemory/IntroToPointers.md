---
title: IntroToPointers
description: 
published: 1
date: 2023-02-24T18:15:30.260Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:34:58.962Z
---


## Intro to Pointers

- Interactive tutorial for this topic: [Intro to Pointers Tutorial](http://localhost:8888/lab/tree/tutorials/PointersAndDynamicMemory/IntroToPointers.ipynb)

A pointer is a type of variable in the same way that int or double are a type of a variable. An *int* variable holds a value that is always an integer and the computer knows to allocate the right amount of memory to hold an integer when it sees an int variable. A *char* variable requires enough memory to hold a single character.
A pointer variable holds a memory address, so it needs only to have enough allocated memory to hold an address. This is often less memory that is required for other variable types.
A pointer is declared in the same way as other variables, by stating the type, then the variable name. An asterix (\*) is used to indicate that a variable is of type pointer.
    `int * intPointerVariable;`

Pointers are extremely useful, especially when passing parameters to functions and when sending return values back from functions. Because the C language uses **pass-by-value** as its method of passing parameters, a function only gets a copy of the parameter value and does not have access to the actual parameter.
For example, in the program below, a parameter is passed in to the silly function, but when the value is printed again in main, it will not have changed.
```c
    void sillyFunction(int theParam)
    {
      theParam = theParam + 15;
      printf(``The parameter inside the function %d\n", theParam);
    }
    int main(void){
      int theVariable = 10;
      printf(``The variable before the function call %d\n", theVariable);
      sillyFunction(theVariable);
      printf(``The variable after the function call %d\n", theVariable);
      return(0);
    }
```
If a pointer is added to this program, and the function takes a pointer instead of an integer, the result is much different. Try these two programs for yourself to see what the results are.
```c
    void sillyFunction(int * theParam)
    {
     * theParam = *theParam + 15;
      printf(``The parameter inside the function %d\n", theParam);
    }
    int main(void){
      int * intPtr
      int theVariable = 10;
      printf(``The variable before the function call %d\n", theVariable);
      sillyFunction(intPtr);
      printf(``The variable after the function call %d\n", theVariable);
      return(0);
    }
```
Pointers are declared using the `*` operator. Pointers have values assigned to them by finding the address of the thing that needs pointing to. You can find the address of a thing using the & operator (address of). So, a pointer can be assigned to point at an integer with the following snippet of code:
    `int * integerPointer = & integerVariable;`

For a pointer variable to be useful, it must be possible to work with the value that it is pointing at. To get to the thing being pointed at, you **dereference** the pointer. The `* `operator is also the dereferencing operator. If we wanted to do some mathematical operation on the integer being pointed at in the previous example, it could be done with the following code:
    `integerPointer = *integerPointer + 23 * 12`

To summarize: **If you want to:**

- **Get the value of the thing the pointer is pointing at**
    - `* name`
    - `* intPtr = 5;` sets the value of the variable being pointed at

-  **Get the address of a thing**
    -   `& thing`
-   **Assign a pointer to point at a thing**
    -  `variableType * pointerName = & variable`
    -   `int * intPtr = &intVariable;`
-   **Assign a pointer to point at the same thing as a different pointer**
    -   `pointerName = otherPointerName`
    -   `intPtr = otherIntPtr;`
   
