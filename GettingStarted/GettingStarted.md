# The Ground Rules {#the-ground-rules .unnumbered}

Everyone has their favourite conventions for computer programs. This
book is written with the assumption that you are following (or at least
aware of) the conventions that I impose on my programming students.

All examples are written with clarity for the reader as the primary
objective. This means that variables are declared first and initialized
in a separate step. It means that shorthand notation for operations is
never used. It means that everything is parenthesized, even when it
might not have to be. Examples are written to compile with gcc, using
-ansi -Wall flags. All of the examples will also compile with -std=c99
-Wall.

Short examples often make it tricky to tell what the expectations are
for coding conventions. I require that students prototype functions in a
.h file and that functions are defined in a file separate from the file
containing *main*. Each function prototype must have a preceding comment
that describes the function's purpose and usage (The comment belongs in
the .h file). Comments in implementation files are limited to
explanations of complicated bits of logic or algorithm.

Project files must be organized so that the main project directory has
subdirectories for *src*, *bin*, *include* and *doc*. Source code (.c
files) go in the *src* subdirectory. Header files (.h files) go in the
*include* subdirectory. Documentation and testing files belong in the
*doc* directory, and the *bin* directory is used by the build process as
a place to put executables. If your program uses images or save files,
those should be in a separate subfolder called *resource* This book has
been written primarily for University of Guelph students. We require
that students have a thorough understanding of the Academic Integrity
issues associated with sharing source code and with reusing things found
on the internet. We require that every submission for grading contains a
statement declaring that the work is the student's own work. I require
that the integrity statement is placed as a head comment in each .c file
that is submitted.

-   Academic Integrity statement at beginning of each .c file

-   main in its own file

-   functions in separate file(s)

-   function prototypes in .h file(s)

-   variable and function names meaningful and in camelCase

-   function purpose and usage described in header file comment

-   algorithms are explained in implementation comments

-   .h and .c files are well organized

I also require that every programming assignment is accompanied by a
README file. An example of one acceptable readme format is below:

    Your Name             Your Student Number
    CIS 2500               Assignment One
    *************
    compiling the program
    *************
    To compile this program type ...

    *************
    running the program
    *************
    To run the program type... 
    Use the arrow keys....

    *********
    known limitations
    ********
    The program will ...
