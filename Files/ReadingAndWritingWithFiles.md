---
title: ReadingAndWritingWithFiles
description: 
published: 1
date: 2023-02-24T00:05:04.748Z
tags: 
editor: markdown
dateCreated: 2023-02-23T20:34:55.371Z
---


## Reading and Writing with files 

- Interactive tutorial for this topic: [Reading and Writing Files Tutorial](http://localhost:8888/lab/tree/tutorials/Files/ReadingAndWritingFiles.ipynb)

One way to work with files is to read or write single characters.
`fgetc()` and `fputc()` are the functions that work with singlecharacters. The syntax for getting characters is `fgetc(filePointer);`
Use `fgetc` to read a single character from the stream.  If fgetc is successful it returns an
unsigned char the character.   `fgetc` returns EOF if there is an error orthe end of the file is reached.

Use `fputc` to write to the file one character at a time. The syntax for
`fputc` is `fputc(character, filePointer)`. The return value for `fputc` is the character written.  `fputc` returns EOF if there is an error.

The code snippet below shows how to use fgetc and fputc to read and write from files. Assume the files have been opened properly.

```c
      char buffer[100];
      char  justRead;
      int fileReadReturn;

      fputc('c', outfile);
      fputc('w', outfile);
     
      justRead = fgetc(infile);
      while(justRead != EOF)
        {
          justRead = fgetc(infile);
          printf("%c\n", justRead);
        }
```

Another way to work with files is to read or write a specific number of characters. `fgets`and `fputs` work with a preset size of buffer.
The syntax for fgets is `fgets(buffer, size, infile);`. `fgets` returns a
`char *`. `fgets` will read a string of the size specified from the file into a preallocated variable and if it is successful it returns a
pointer to the string. The `fgets` function  returns if it reaches the size given or if it encounters a newline. If `fgets` is unsuccessful or reaches the end of the file it returns NULL.

To write a string to the file use fputs. The syntax for fputs is `fputs(char \* string, filePointer);` It will copy in the string up to
the \\0, but does not copy the null terminator to the file. The return value for `fputs` is an a positive int on success. `fputs` returns EOF on error(EOF is an integer value that is defined within the compiler/programming language).

The code snippet below shows how to use fgets and fputs to read andwrite from files.

```c
    char * returnValue;
    returnValue = fgets(buffer, 50, infile);
    while(returnValue != NULL)
       {
        printf("%s\n", buffer);
        returnValue = fgets(buffer, 50, infile);
       }
    fputs("onetwothreefourfive", outfile);
```
Finally you can use `fscanf` and `fprintf` to read and write with files. `fscanf` reads formatted data from the stream. The syntax is:
`fscanf(filepointer,format,pointer to buffer);`. If `fscanf` is successful it returns the number of arguments filled by the call. It returns EOF if there is an error or the end of the file is reached. `fscanf` uses the same format strings as printf which can be constructed to be quite
complex and can act as a parser.

Each method of reading and writing to file is slighty different and it can be difficult to remember the exact syntax. Man pages are very
helpful for such instances.
