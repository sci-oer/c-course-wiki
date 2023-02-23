
## Intro To Files

Files are a great way to permanently store data that your program needs to have each time it runs. You can keep almost any kind of data in a file including saved states for the program (like game save files, data, and startup parameters.

A file is a type of *stream*. Streams are just a set of input (might be character, might be binary) that has no identified endpoint. You don't know how long a stream is when you start using it.

There are four steps to using files in C"

1.  **Declare**: You must declare a `FILE *` variable for use with the file. `FILE * infile;`
2.  **Open**: Use the function `fopen` to open a file. Files can be opened in *read (r), write (w) or append (a)* mode.
3.  **I/O** You use i/o operations such as *fgetc, fputc, fgets, fputs,and fscanf* to read and write with the file.
4.  **Close** You must close the file when you are finished with it. Use `fclose` to do that.

## Opening Files 

The syntax for opening a file is `fopen(filename, mode)`. There are three possible modes: 'r', 'w', 'a'. 'w' opens the file for writing and starts at the beginning of the file and writes a new file- erasing anything that was in the file previously. 'a' opens the file in append
mode and adds things to the end of the file. 'r' opens the file for reading only. The call to fopen will return a pointer of type `FILE *`. You must use that pointer to write or read data to/from the file.

The call to fopen must be made with a *relative pathname*. This means that you give the path as if you were starting from where the program is executing. For example:
- `fopen("input.txt");` looks for a file in the current directory
- `fopen("src/input.txt");` looks for a file in the src subdirectory of the current directory
-  `fopen("/input.txt");` looks for a file at the root of the entire file system

The code below shows how to open a file for reading and how to open a file for writing. Always include the check to make sure the file pointer isn't NULL.

```c
      FILE * infile;
      FILE * outfile;
      infile = fopen("testread.txt","r");
      outfile = fopen("testwrite.txt","w");
      if (infile == NULL) {printf ("error opening file\n"); exit(0);}
      if (outfile == NULL) {printf ("error opening file\n"); exit(0);}
```
It is always best not to hard code file names in production code, but it is  important to understand how to construct a path to the desired file.
