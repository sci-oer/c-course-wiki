
## Random Access Files  

A random access file is a file that can be read (or written) from any
position in the file. The user of a random access file does not need to
read or write the file from beginning to end, rather the file can be
created and edited in any order desired.

In order to understand how random access files work, its important to
understand the general mechanics of using files in a C program. When you
open a file with fopen(), it returns a pointer to the address of the
beginning of the file. The file considered to be an address space in
much the same fashion that computer memory is an address space.

Each operation you use to read data from the file (fgets or fscanf)
moves the file pointer to the spot in the file that is immediately after
the last data you read. C even provides tools for moving around the file
without reading data. You can use *fseek* and *rewind* to reset the file
pointer to a specific position in a text file.

Files are really just persistent pieces of memory but file access is
slower than memory access, so you don't want to use files as working
memory. You can treat a file pointer much like any other pointer, which
means you can assign address values to it. A file pointer simply holds a
position (address) within the file. *fseek* essentially adds and
subtracts from the value of the pointer (doing pointer math), which
causes the pointer to contain a different address within the file.
