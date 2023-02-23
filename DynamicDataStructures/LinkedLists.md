

## Linked Lists {#linked-lists .unnumbered}

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

## Adding Elements to a Linked List 

Elements can be added to a linked list either in the middle, the beginning or at the end of the list. The decision about where to add the element usually depends on whether or not the list is sorted as elements are added.

One of the advantages to dynamic data structures is the easy ability to keep the data sorted at all times. [This site has an excellent animation showing the insertion of elements into a sorted list](http://courses.cs.vt.edu/csonline/DataStructures/Lessons/OrderedListImplementationView/linkedlist.html)

The algorithm for inserting an element at the end of an unordered list is as follows.

   1. allocate memory for the new list element
   1. put the desired data into the new element
   1. until end of list is reached //when you find a NULL next pointer
      - move to the next element in the list
   1. set the next pointer of the last element to point to the new element
   1. set the next pointer of the new element to NULL //the last pointer in the list should be NULL

Another way to insert elements into an unsorted list is to put them at the beginning of the list, which eliminates the need for the walk through the list to get to the end.

The algorithm for inserting an element into a sorted list is nearly the same.

1. allocate memory for the new list element
1. put the desired data into the new element until the next pointer  points to a larger element than the element to be added, or the end of the list is reached
   - move to the next element in the list
1. set the next pointer of the new element to be equal to the next pointer of the current element
1. set the next pointer of the current element  to point to the new element

As you can see, the programmer must keep careful track of the pointers, but it is quite simple to add elements to the list. You need to keep track of the newElement, and the element that is one less than the new element (for a sorted list) or the lastElement for an unsorted list. Here is some pseudo code for setting the pointers
```c
    newElement->next = currentElement->next (sets the new pointer equal to the one that is one larger)
    currentElement->next = newElement   //assuming newElement is a pointer
```

## Removing Elements from a List 

To remove an element from a linked list you must first find the element that is pointing to the one to be removed. This means you are looking for the element that is **one before** the element that will be removed.

Then you set the next pointer of the one-before element to point at the one-after element, and then delete the one that is no longer needed.
```c
    temp = head
    while (temp->next is not pointing at the one to be removed)
        temp = temp->next
    toberemoved = temp->next //this will be the one to free
    temp->next = *(temp->next)->next
    freeStruct(toeberemoved)  //freeStruct isn't a built in function
    instead of freeing the struct you could do things with the values first, and then free it, or add it to another list, or....
```

## Freeing a List 

To free an entire linked list, you simply start at the root node of the list and free each element (saving the location of the*next* pointer) until you reach the end of the list. If the element of the list is a struct, you should call the free function that is (hopefully) supplied with the struct, or at least ensure that all the members of the struct are freed properly.
```c
    while(head != NULL)
         temp = head
         head = temp->next
         freeStruct(temp)  // freeStruct is not a built in function
```
## Useful list handling functions 

When working with lists, programmers will frequently write functions for tasks that are common. Some of those common functions include:

-   finding the length of a list. Typically returns an int and takes the head of the list as a parameter. 
   - `int listLength(struct intStruct * head)`

- finding an element of a list. This function usually just returns a pointer to the element in the list, without removing the element from the list. It needs a search criteria and the list as parameters, and returns a struct pointer. 
   - `struct intStruct * find(int searchParam, struct intStruct \* head);`

- printing a list. Ideally this function returns a `char *` that
    represents a nicely formatted printout of the list elements.
