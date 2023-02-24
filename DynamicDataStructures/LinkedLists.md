---
title: LinkedLists
description: 
published: 1
date: 2023-02-24T20:08:11.668Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:34:50.486Z
---



## Linked Lists 

- Interactive tutorial for this topic: [Linked List Tutorial](http://localhost:8888/files/tutorials/DynamicDataStructures/LinkedLists.ipyn)

Elements in a linked list are usually structures. A list structure contains all the members needed for the data that the structure represents, and one extra pointer to the structure type (used for linking the list elements).
```
    struct intListElement
    {
      int viNum
      struct intListElement * next; /*the pointer for the list*/
    };
```
The list is created by setting the value of the 'next' pointer on at the end of the list to point to the new member. 

![image](/img/linkedList.jpg)

The front of the list is called the **head** or **root**, the end of the list is often called the **tail**. The *next pointer* for the tail element is set to NULL so that the end of the list is easily identified.


### Implementation Details

When you write the operations for a linked list, the most challenging aspect is to keep track of the pointers that give access to the adjacent nodes in the list.

The pseudocode below illustrates the process for adding an element to the beginning of the list. This pseudocode assumes that currentElement is the beginning of the list and that newElement has already been allocated and is pointing to the list data. The order of these two lines of code is very important. Can you explain why?
```
           newElement-$>$next = currentElement-$>$next     
           currentElement-$>$next = newElement
```
The following steps are required to add a node to the end of the list:
 1.  Initialize a new element with the desired data. This should be a     separate function call. 
2.  Iterate through until end of list is reached 
3.  Set the *next* attribute of the element at the end of the list to     the new element. 

The most challenging part of this algorithm is Step 2, iterating through the list. This is an operation that you will find yourself doing frequently with linked data structures. The pseudocode for that step is shown below. Draw a list on some paper and work through the algorithm until you understand how to walk through a list to get to the end of the list.

```
    currentElement = firstElementOfList //usually called the head of the list
    while(currentElement->next is not NULL)
        currentElement = currentElement->next
    lastElement = currentElement
```
### Nodes

A node, or element, is the fundamental structure within a list.
Regardless of your choice of implementation for a list, you will need some kind of a node structure to contain the data for the list.

When we take the time to create an ADT, we want it to be truly abstract. That means that the ADT should not be tied to a particular kind of data, since the operations on a list are identical whether it is storing integers, strings, or structs. It is a waste of time and testing to create separate ADT libraries for every possible type of data.

Instead we abstract the data by creating a data structure called a **node**. As a minimum, the node contains a pointer that points to the data being stored, and a pointer to the next node in the list.
```
    typedef struct Node {
        void * data;
        struct Node * next;
    }Node;
```
The type of the data doesn't matter because it is cast to a void pointer (void \*). The data stored in the list might be a string; it might be an integer; or it might be a complex struct that represents a larger data record about some entity.

A linked list ADT should have a function that creates a new node, sets the next pointer to NULL, and assigns the data to the data pointer. Algorithms for working with linked lists assume that the **next pointer** for the tail element is set to NULL so that the end of the list is easily identified. It is very important to ensure that all new nodes have their next pointer initialized to NULL.

The data stored in a linked list is separate from the node definition. A node simply points to the data element. Suppose you were storing addresses in the list. The data representation would then contain elements for name, phone number, mailing address and possibly email address. A struct to represent the data might be given as follows.
```
    typedef struct Address {
        char * name;
        char * telephone;
        char * mailingAddress;
        char * email;
    } Address;
```
### Operations

A list ADT typically provides functions that add elements to the list, remove elements from the list, report how long the list is, and possibly sort the list. It also must provide functions to create and destroy the list.

A minimum set of operations is shown below. The names of the functions can vary, but an operation with comparable functionality is necessary. The parameters given in the pseudcode are also a minimum set of parameters. Implemented functions may need additional parameters.

    ·create(...): List
    ·destroy(List)
    ·insertFront(List,  DataElement):theHead
    ·getFront(List):DataElement
    ·deleteFront(List)



### Adding Elements

Elements can be added into a list at the beginning, in the middle, at some arbitrary location, at the end, etc. Each insert algorithm is slightly different than the others but the basic idea is the same in all cases.

1.  Construct a new list element 
2.  Put the desired data into the new element 
3.  Find the location where the element is supposed to be inserted 
4.  Adjust the other list elements so that the new one is in the right     location and so all existing elements are still part of the list 

Algorithms for inserting an element in the first position and last position are shown below. The pseudocode or algorithm for inserting in a specific location is left as an exercise for you to do.

```
    insertFirst(List, Element):theHead
    Also Known as:addFront, insertFront, addHead, etc
    Purpose: To add an element to the list at the front of the list
    Preconditions: An initialized list is available.  
    PostConditions: The node containing the desired data is added to the front of the list, the length of the list is increased by one, the head of the list is set to point at the newly added element.

    insertFirst(List, Element):theHead
         initialize a new node with the desired data
         set the next pointer of the new node to point at the first nod of the list
         set theHead  of the list to point at  the new node
```
```
    insertLast(List, DataElement):void
    Also Known as: addBack, insertBack, addTail, etc
    Purpose: To add an element to the list at the tail of the list
    Preconditions: An initialized list is available.  The new node has the next pointer initialized to NULL
    PostConditions: The node containing the desired data is added to the end of the list, the length of the list is increased by one.

    insertLast(List, DataElement):void
        initialize a new element with the desired data.  
        walk through until end of list is reached 
        set the next attribute of the element at the end of the list to the new element.    
```
### Deleting Nodes

Deleting nodes in a list uses algorithms that are the reverse of adding nodes. Nodes can be deleted from the front, the back, or any location in the list. The simplest algorithms delete nodes from the front or the back of the list.
```
    deleteFront(List):Element  //often a delete method returns the value it has deleted
    Also Known As: deleteFirst, removeFront, removeFirst
    Purpose: To remove the first element from the list and return it to the calling procedure
    Preconditions: A non-empty list is available
    PostConditions: The first element of the list is removed, the length of the list is decreased by one,  the removed element is returned.

    deleteFirst(List):Element
        set a temporary pointer(temp) to point at the first node in the list
       set the head pointer of the list to point at the second node in the list
       set the next pointer of the temporary node (the former first node)  to be NULL
        return(temp->data)
```
```
    deleteFromBack(List):Element  //often a delete method returns the value it has deleted
    Also Known As: deleteLast, removeBack,  etc
    Purpose: To remove the last element from the list and return it to the calling procedure
    Preconditions: A non-empty list is available
    PostConditions: The last element of the list is removed, the length of the list is decreased by one,  the removed element is returned.

    deleteLast(List):Element
        walk the list to find the second last element //node->next->next == NULL
        set a temporary pointer(temp) to point at the last node in the list
        set the next pointer of the second last element to NULL
       set the next pointer of the temporary node (the former last node)  to be NULL
        return(temp->data)
```
## Freeing a List 

To free an entire linked list, you simply start at the root node of the list and free each element (saving the location of the*next* pointer) until you reach the end of the list. If the element of the list is a struct, you should call the free function that is (hopefully) supplied with the struct, or at least ensure that all the members of the struct are freed properly.
```c
    while(head != NULL)
         temp = head
         head = temp->next
         freeStruct(temp)  // freeStruct is not a built in function
```
Usually the functionality to free the memory in a list is encapsulated in a function.
```
    destroy(List)
    Purpose: To destroy a list, freeing memory if required
    Preconditions: A list exists
    PostConditions: The list is destroyed

    destroy(List)
       for each node in the list
           delete the data in the node using function pointer
           delete the node
       delete the struct holding the list metadata
```
### Other Core List Operations
```
    isEmpty(List):Boolean
    Purpose: To determine if the list has any elements stored in it   
    Preconditions: An initialized list is available
    PostConditions: None

    isEmpty(List):Boolean
        if theHead == NULL and theTail == NULL
        then return (true)
        else return (false)
```
isFull() is a function that is only useful in situations where a list could be full. This might happen in situations where a specific amount of memory has been allocated to the list. In that case when the memory is full, a reallocation must be effected before the list size can be increased by adding another element.
```
    isFull():Boolean
    Purpose:To determine if the list is filled to capacity
    Preconditions: An initialized, non-empty list is available
    PostConditions: None
       
    isFull():Boolean
        if length == maxSize
        then return (true)
        else return (false)
```
```
    create(...): List
    Purpose: Create a new List initialized to be empty
    Inputs: the function pointers for functions to manage the data stored in the list
    Preconditions: None
    PostConditions: A new list is created and is empty

    create(...):List
        create the struct to hold the list metadata (head, tail, function pointers, etc)
        assign NULL to head (and tail if necessary)
        assign function pointers
        return(List)
```

#### Other useful list handling functions 


-  finding the length of a list. Typically returns an int and takes the head of the list as a parameter. 
   - `int listLength(struct intStruct * head)`
- finding an element of a list. This function usually just returns a pointer to the element in the list, without removing the element from the list. It needs a search criteria and the list as parameters, and returns a struct pointer. 
   - `struct intStruct * find(int searchParam, struct intStruct \* head);`
- printing a list. Ideally this function returns a `char *` that represents a nicely formatted printout of the list elements.
   - see the section on 