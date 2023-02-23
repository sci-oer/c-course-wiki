
## The Preprocessor 

The preprocessor is a program that runs BEFORE the compiler. It does three things- all of which are essentially search/replace on the text.

1. **macro processing.** Macros are defined values or operations that are substituted into the text. Its just a strict text substitution.
It makes your code a bit more readable and means that if you have to change the definition, you do it in one place- but you don't have to define functions. It is sometimes tricky to get right- don't try to to get too fancy with it.

For example, if the macro `#define LOONIE 100` is added to a source file,  all occurrences of LOONIE will be replaced by 100. By convention macros are capital letters. The \# sign is
the signal that a macro is being defined.

- put macros at the beginning, after the \#includes
    - `#define SQUARE(a) ((a)\*(a))`
    - `#define MAX(a,b) ((a)\<(b)?(b):(a))`
    - its a good idea to completely parenthesize
2.  **including header files**
 The \#include is actually a call to the preprocessor. It goes off, gets the referenced files, and copies the contents into that spot in the source code.

    - #include \"\" means look in current directory
    - #include \<\> means look in library directories
    - it is important to know where those library paths are. It is **EASY** to control which library is included when compiling on the command line. It can be challenging if you are using an IDE

3.  **conditional compilation** Conditional compilation lets you tell the compiler whether or
not to include parts of the code. This use of preprocessor commangs can be very useful for debugging.

 `#define DEBUG 0 (0 is false)`
```c
#if DEBUG 
 //print debugging information

#endif //must include this
```

#### Include Guards 

As your code gets to be more complicated, you'll notice that header files will need to include other header files, and soon you'll have things declared multiple times. This is especially a problem if you are defining constants or structs in your header files. Use include guards
to solve the problem
```c
    #ifndef SOME_UNLIKELY_COMBO_OF_WORDS
    #define SOME_UNLIKELY_COMBO_OF_WORDS
    // put your code here
    #endif  
```
You can define constants (usually in a header file) that are then available for all programs.

```c
    #define PI 3.14
    #define BAKERSDOZ (12+1)
    #define LIST_H
```
A defined constant for DEBUG can make it really easy to turn on/off debugging statements. You can also define the value of a preprocessor macro on command line with the -D flag to gcc. 
`gcc lab0.c -o lab0 -DDEBUG = 1`

```c
    #define DEBUG 1
    //.... code.....
    if(DEBUG){
        printf("Removing from list: %d %s\n", getTime(patron),%getID(patron));
    }
```
If your constant is a calculation, use parenthesis, else you risk getting unwanted results. 

In the example below, p will evaluate to 17. Make sure you understand why that is the case.

```c
#define BAKERSDOZ 12+1
p = BAKERSDOS*5
```
Macros are a way of writing quick, inline code and making your code more readable. They are also an easy way to introduce bugs. Use with caution.

```c
    #define PLUSONE(x) x++
    #define MULT(x,y) x*y
```
A macro is cut/paste EXACTLY into your code at the point that the macro label is placed. So if you write `int z = PLUSONE(y);` your code will
compile with `int z= y++);` It is  important to remember that macros are cut/paste in EXACTLY.

```c
    #define MULT(x,y) x*y
    MULT(x+1, y+1);
```
The call to MULT expands to `x + 1*y + 1'` which is not what was likely wanted. `#define MULT((x)(y))` is more robust.
