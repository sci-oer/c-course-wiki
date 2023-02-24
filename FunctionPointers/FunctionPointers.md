---
title: FunctionPointers
description: 
published: 1
date: 2023-02-24T19:09:29.094Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:34:56.271Z
---


# Function Pointers
- Interactive tutorial for this topic: [Function Pointers Tutorial](http://localhost:8888/lab/tree/tutorials/FunctionPointers/FunctionPointers.ipynb)

Functions have addresses in the same way that variables do.  In this section we'll explore how to use the address of a function to reduce duplicate code and make more extensible software.

Everything about a computer program has an address in the computer's memory. Think back to our discussion of computer memory. One of the sections of computer memory is called the text area, and it is where program instructions are kept. Since all areas of memory can be addressed, you can find the address of any function in memory and assign a pointer to it.
This gives us an alternative to rewriting the sort for each type of data. We can to tell the sort function where to look for the right compare function. Instead of providing the NAME of the function, provide the address in such a way that we can change the address when necessary. This use case is one of the common uses for function pointers.

The steps to using a function pointer are straightforward. The syntax in C is a bit tricky, but once mastered, function pointer use is quite simple.

1.  Write the function that will be pointed to
2.  Make a pointer to it- The pointer has a declaration that looks like the function.
3.  Assign a value to the pointer
4.  Use the pointer

Below is an example of those four steps. Notice the syntax of the second step. The parentheses are important.

1. Write function: `void myfunction (int z, char \* y);`
2. Make pointer: `void (\* fPtr) (int, char \*);`
3. Assign value: `fPtr =&myfunction;`
4. Use pointer: `fPtr(4, \"funny\");`

## Use Case One: Passing in a formatting function

The code shown defines a struct to store information about a student and declares  functions to manipulate the struct.   This code would normally be found in a header file.

```c
struct student {
  char * firstName;
  char * calledName;
  char * surname;
  float GPA;
  int studentID;
};
typedef struct student Student;


Student ** loadSomeData();
void printReversed(Student * toPrint);
void printCalledName(Student * toPrint);
void printInitials(Student * toPrint);
```
The next declaration is for a function that prints an entire set (array) of student records.  This function declaration takes a function pointer as a parameter that is intended to be the method by which the student record will be output.

```c
void printSet(Student ** theArray, int length, void (* prtPtr)(Student *));
```
The definitions for each of these functions is shown in the next code segment.  Normally this code would be found in a file separate from the main function.   

```c
void printSet(Student ** theArray, int length, void (* prtPtr)(Student *))
{
  int i;
  for (i=0; i<length; i++)
  {
    prtPtr(theArray[i]);
  }

}

void printInitials(Student * toPrint)
{
  printf("%c.%c.\n", toPrint->firstName[0], toPrint->surname[0]);

}
void printCalledName(Student * toPrint)
{

  printf("%s\n", toPrint->calledName);
}

void printReversed(Student * toPrint)
{
	printf("%s,%s\n", toPrint->surname, toPrint->firstName);
}
```
Finally, we have the main method that shows how this set of functions can be used.  The `loadSomeData()` function just loads some hard coded data into the array for the purposes of demonstration.  It is shown after the main function.  Trace through this code to see if you can predict what the output will be at lines 9, 11, and 13.  Notice that the addresses of the methods are sent in as parameters to the printSet function call.

```c
int main(void)
{

  Student * * myList;

  myList = loadSomeData();
  printCalledName(myList[0]);
  printf("\n\n");
  printSet(myList, 3, &printReversed);
  printf("\n\n");
  printSet(myList, 3, &printCalledName);
  printf("\n\n");
  printSet(myList, 3, &printInitials);
 
 

return(0);
}
```

```c
Student ** loadSomeData(){
  Student ** newList = malloc(sizeof(Student*)*3);
  
  newList[0] = malloc(sizeof(Student));
  newList[0]->studentID = 1;
  newList[0]->firstName = malloc(sizeof(char)*(strlen("Fredrick")+1));
  strcpy(newList[0]->firstName, "Fredrick");
    newList[0]->calledName = malloc(sizeof(char)*(strlen("Fred")+1));
  strcpy(newList[0]->calledName, "Fred");
    newList[0]->surname = malloc(sizeof(char)*(strlen("Flintstone")+1));
  strcpy(newList[0]->surname, "Flintstone");
newList[0]->GPA = 3.7;


  newList[1] = malloc(sizeof(Student));
  newList[1]->studentID = 2;
  newList[1]->firstName = malloc(sizeof(char)*(strlen("Barnard")+1));
  strcpy(newList[1]->firstName, "Barnard");
    newList[1]->calledName = malloc(sizeof(char)*(strlen("Barney")+1));
  strcpy(newList[1]->calledName, "Barney");
    newList[1]->surname = malloc(sizeof(char)*(strlen("Rubble")+1));
  strcpy(newList[1]->surname, "Rubble");
newList[1]->GPA = 3.2;

  newList[2] = malloc(sizeof(Student));
  newList[2]->studentID = 3;
  newList[2]->firstName = malloc(sizeof(char)*(strlen("Persephone")+1));
  strcpy(newList[2]->firstName, "Persephone");
    newList[2]->calledName = malloc(sizeof(char)*(strlen("Pebbles")+1));
  strcpy(newList[2]->calledName, "Pebbles");
    newList[2]->surname = malloc(sizeof(char)*(strlen("Flintstone")+1));
  strcpy(newList[2]->surname, "Flintstone");
newList[2]->GPA = 4.0;


 return (newList);
}
```



## Use Case: Sorting Data 

Sorting data is a very common programming task that is a common use case for function pointers in C.   Sorting is so common that there are names given to the different approaches to sorting and there are well known algorithms that are studied and analyzed carefully to determine just how efficient the algorithms are. A few of the best known algorithms are listed below.
-   Bubble Sort
-   Selection Sort
-   Quick Sort
-   Merge Sort
-   Heap Sort
-   Shell Sort

Selection sort is simple to understand, but not terribly efficient. Selection sort is our example to help with understanding function pointers.
-   Selection Sort works by finding the biggest item (or smallest) and
    putting it in place.
-   it then finds the next item, and puts it in place.
-   the sort is easy to understand, but not very efficient
-   Like all sorts, it only works on data that can be compared
-   Must have the ability to identify **greater than**, **less than**,and **equal** for data in order to sort it

Making comparisons for numbers is easy. For other types of data the comparison operation requires more work. Usually the programmer has to write an operation to compare the data.
-   \>\<and equal come free for numbers
-   you can simulate them for letters by using string functions and ascii values
-   For all other kinds of data you must define your own comparisons

Consider a datatype that represents time duration in hours/min/sec. How would you sort a list of structs that represent time?
```c
    struct time { 
       int hours; 
       int min; 
       int sec;
     }; 
```
-   longest duration to shortest?1
-   shortest to longest?
-   rounded off to just hours?
-   the number of minutes after the hour?
-   You could convert it to seconds and just use math operators, but sometimes that just isn't a good solution
-   You likely would have to write your own comparison operator for it.


Start by defining how the comparison operator will communicate the results of the comparison. Convention is to use the same return values as strcmp for comparison operators.

-   `compare (struct time first, struct time second)`
-   needs a return value to indicate the results of the comparison
-   negative return value means first \<second
-   positive return value means first \>second
-   zero means first == second
-   Inside the compare function, we'd need some if statements to check on the size
    -   if first-\>hours bigger than second-\>hours AND minutes and seconds are bigger, return positive number
    -   if second-\>hours bigger than first- \>hours AND all others are also bigger return negative number
    -   if hours are bigger but not minutes then some subtraction might required to see if there is an hour difference
    -   etc

You can use the compare function to tell which of two time variables(represented as time structs) is larger. See the listing below for an example. The compare function is called at the bottom of the listing. What value would the whoIsBigger variable have at the end of execution?
```c
    struct time { 
        int hours; 
        int min; 
        int sec;};
    typedef struct time timedata;
    int compare (timedata *first, timedata*second);
```
```c
    int main(void){
    int whoIsBigger;
    struct time * firstTime = malloc(sizeof(timedata));
    struct time * secondTime = malloc(sizeof(timedata));
    firstTime->hours = 24;
    firstTime->min = 12;
    firstTime->sec = 4;
    secondTime->hours = 24;
    secondTime->min = 3;
    secondTime->sec = 2;
    whoIsBigger = compare(firstTime, secondTime);
    }
```
The next step is to use compare in a sort function You could write your own sort and call the compare function The selection sort with a compare function is shown below.
```c
    for(i=0; i<numberOfThingToSort; i++)
        {
            biggest = &arrayForSorting[i];
            for(j=i; j<numberOfThingToSort; j++) 
                {
                if (compare(arrayForSorting[j], * biggestNum) > 0)
                    biggestNum = &arrayForSorting[j];
                }
                if (biggestNum != &arrayForSorting[i])
                    mySwap(biggestNum, &arrayForSorting[i]);
        
        }
```
This approach has a bit of a downside. Each time you need to sort a different type of data you need to rewrite the compare function to reflect the type of data or you need to write a new compare function and rewrite the sort to call the correct function. In C you can't have a function with the same name as any other function, so you can't simply have a bunch of functions called compare with different data types as parameters.




In the listing below you can see a declaration of a variable called functionPtr that has been given the address of the compare function as its value. That function pointer is then used in the call in the sorting loop.
```c
    int (*functionPtr) (struct time*, struct time*) = &compare;

    for(i=0; i<numberOfThingToSort; i++)
        {
            biggest = &arrayForSorting[i];
            for(j=i; j<numberOfThingToSort; j++) 
                {
                if (functionPtr (arrayForSorting[j], * biggestNum) > 0)
                    biggestNum = &arrayForSorting[j];
                }
                if (biggestNum != &arrayForSorting[i])
                    mySwap(biggestNum, &arrayForSorting[i]);
        
        }
```
A more general way to use function pointers in sorting is to provide the function pointer as a parameter to the sort function. C has a built in sort called qsort that requires a function pionter.

```c
    void qsort(void *base, size_t num_elements,
         size_t element_size, int
         (*compare)(void const *, void const *)); 
```
-   void \* base is the array for sorting
-   num_elements is how long the array is
-   element_size is how "big" the individual elements are
-   sizeof(struct time) for the running example
-   compare.. is a pointer to a compare function
-   it doesn't have to be called compare, because you are sending thepointer

The listing below shows a call to qsort when sorting the time struct variables. Several different compare functions could be written and a different one sent to qsort depending on the desired sorting behaviour.
```c
    int compare( struct time *first, struct time *second);

    int main(void){
    struct time ** timelist = malloc(sizeof(struct time *)*2);
    struct time * firstTime = malloc(sizeof(struct time));
    struct time * secondTime = malloc(sizeof(struct time));
    firstTime->hours = 24;
    firstTime->min = 12;
    firstTime->sec = 4;
    secondTime->hours = 24;
    secondTime->min = 3;
    secondTime->sec = 2;
    timelist[0] = firstTime;
    timelist[1] = secondTime;
    qsort(timelist, 2, sizeof(struct time), compare);

    }
```
