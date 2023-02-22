
---
title: Freeing Memory
description: 
published: true
date: 2022-10-28T20:59:34.191Z
tags: 
editor: markdown
dateCreated: 2022-10-28T20:42:21.376Z
---

## Freeing Memory {#freeing-memory .unnumbered}

 Whenever you allocate memory from the heap, you must also free it. Even
if you allocate memory from within a function, it must be freed
somewhere. This is only true for heap memory (stuff you allocate with
malloc).

You must free memory in the reverse order that you allocate it for
arrays of more than one dimension. For example for a 2D array you should
do the following:

-   start with the actual elements of the array and free those

-   then free the pointer to the array