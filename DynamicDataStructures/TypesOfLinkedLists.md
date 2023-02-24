---
title: TypesOfLinkedLists
description: 
published: 1
date: 2023-02-24T20:10:00.501Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:34:51.409Z
---

## Variations on Linked Lists

A linked list can be constructed in several different ways.The differences between the construction is in the number and purpose of the pointers in the node structure. 

Sometimes all that is needed is a simple list, where the first item in the list leads to the second item which leads to the third item and so on. This is called a **singly linked list**. A singly linked list provides no mechanism to return to the previous item. Imagine a collaborative story-writing task where each person writes a sentence on paper and then passes the paper to someone else who writes another sentence on the paper. At the end of the task, there is a story on each piece of paper and the last author is holding the list of sentences, but there is no record of who the previous authors were. That is how a singly linked list works. 

The image below shows a singly linked list with five nodes.   The head node has the data value of 3.  The second node has a data value of 't'.  The remaining data values are 4, 9 and 2.   The node containing the value 2 is the tail of the list and has a null pointer because there is no next node.  Each node has a single pointer that contains the address of the next node in the list.


![a singly linked list with five nodes.   The head node has the data value of 3.  The second node has a data value of 't'.  The remaining data values are 4, 9 and 2.   The node containing the value 2 is the tail of the list and has a null pointer because there is no next node.  Each node has a single pointer that contains the address of the next node in the list.](pictures/linked_list.jpg)

A **double linked list** provides a mechanism to identify both the next item on the list as well as the previous item on the list from any position in the list. A double linked list is similar to a group of people standing in line. Any individual person can identify both the person ahead of them in the line and the person behind them.

The image below shows a doubly linked list with five nodes.   The head node has the data value of 3.  The second node has a data value of 't'.  The remaining data values are 4, 9 and 2.   The node containing the value 2 is the tail of the list.  Each node consists of two pointers and a data value.  One of the node's pointers contains the address of the previous node in the list and the other pointer contains the address of the next node in the list.   The head and tail nodes have null values respectively in the previous and next positions.  

![a doubly linked list with five nodes.   The head node has the data value of 3.  The second node has a data value of 't'.  The remaining data values are 4, 9 and 2.   The node containing the value 2 is the tail of the list.  Each node consists of two pointers and a data value.  One of the node's pointers contains the address of the previous node in the list and the other pointer contains the address of the next node in the list.   The head and tail nodes have null values respectively in the previous and next positions](pictures/double_linked_list.jpg)

A **circular linked list** is a list of a fixed size. The last element of the circular list is connected to the first element of the list so that from the last element the program can easily return to the first element. A circular linked list doesn't really have an end point.

The image below shows a circular linked list with five nodes.   The head node has the data value of 3.  The second node has a data value of 't'.  The remaining data values are 4, 9 and 2.   The node containing the value 2 is the tail of the list.  Each node has a single pointer that contains the address of the next node in the list.  The pointer for the tail node contains the address of the head node which gives the list the circular characteristic.

![a circular linked list with five nodes.   The head node has the data value of 3.  The second node has a data value of 't'.  The remaining data values are 4, 9 and 2.   The node containing the value 2 is the tail of the list.  Each node has a single pointer that contains the address of the next node in the list.  The pointer for the tail node contains the address of the head node which gives the list the circular characteristic.](pictures/circular_linked_list.jpg)



## Array implementation for a list

The previous sections of this document have focussed on the list composed of linked data structures (the linked list). A list ADT does not have to be a constructed using linked nodes. An array can be used to construct a List ADT. At its simplest, the array holds the data in the list and each location in the array is one element of the list. The head of the list is at the first position in the array and the tail of the list is wherever the last element is.

The array-based list stores void \* data in the array in the same way that the linked node stored void \* data for the linked data structure. 
The choice of implementation does not change the operations required for the list ADT but it does change some of the implementation details. For example, if the user wished to insert data into the list maintaining a sorted order, the insert operation would require that room is made for the new element by shifting any subsequent elements one position in the array. If a data value was to be deleted from the list, the delete operation must ensure that the space left from the deletion is filled by shifting the tail-end of the array one space towards the head.

Because arrays must be allocated to be a fixed size in C, a new longer array must be constructed and the data copied into it if the list grows longer than the size of the array.

Fortunately, because of information hiding and encapsulation, the user of the the List ADT should never need to know whether the List is implemented as a linked data structure or an array-based list. 
##  Array Lists vs Linked Lists

**Linked Lists**

-   Advantages
     -   Linked lists can be an arbitrary size because the list grows and         shrinks as elements are added. 
    -   Insertion and deletion of data do not require moving other data         elements, so the operations are more efficient than the         comparable operation on an array structure. 
-   Disadvantages
     -   Linked lists are less efficient in situations where the program         must be able to access any element of the data at any point in         the program. This type of accessibility is called **random         access** and is more efficiently implemented with an array.

**Array Lists**

-   Advantages 
    -   Many operations are very fast because the array indices provide         direct access 
    -   functions are simple and easy to debug, making ADT development         simpler

-   Disadvantages
     -   The resizing operations can be processor intensive if the list         is large. There are many different strategies for deciding how         much bigger to make the new array when resizing.
     -   To keep an array sorted, you must shuffle the elements each time         you add another element.

## List Iterator

An iterator is a mechanism that allows navigation of a data structure. An iterator is usually a different structure (or class in the case of object oriented programs) that is fairly tightly coupled with the implementation of the data structure being iterated.

When creating an ADT library in C, iterator functions can be included easily either with, or without the use of additional structures.

List iterator methods permit forwards and backwards navigation of the list. They are extremely useful for accomplishing insertions and deletions because the navigation code is encapsulated within the iterator operation.

Iterator methods for a list might include: 
-   next() 
-   previous() 
-   first() 
-   last() 
-   moveToNth() 
-   getCurrentElement() 
-   setCurrentElement() 
While some of the iterator methods might seem to be duplicates of the basic list functions, an iterator has an important role to play in encapsulation. An iterator can hide the implementation of the list from the user of the library and can provide only the navigational functions to the user.

For example, an iterator for a list could be set up as follows:
```c
    typedef struct Iterator
    {
        List * theList;
        Node * currentListPos;

    }ListIterator;
```
Given this structure, the functions shown above could take a ListIterator as a parameter and provide the user with data that is stored in the list. Of course, the ListIterator would need to be initialized with enough parameters that it could, in turn, initialize the underlying list.

An algorithm for the *next()* function is shown below.
```
    next(ListIterator):DataElement  
    Purpose: To move to the next element in a list and return the value of that element
    Preconditions: The List member of the ListIterator is non-empty
    PostConditions: The currentListPos of the iterator is increased by one and the data stored at that node is returned

    next(ListIterator):DataElement  
        if currentListPos is not the end of the list
           dataToReturn = currentListPos->data
           currentListPos = currentListPos->next
        return (dataToReturn)
```
Some list iterator operations, such as previous() are easier using a double linked list, but all operations are possible regardless of list implementation. The algorithm for other list iterator operations are left as a practice exercise.


