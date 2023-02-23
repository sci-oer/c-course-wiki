 

### Abstract Data Types 

Remember that specification (i.e. \"what\") and implementation (i.e. \"how\") are two separate things. For example, if you are writing functions in your code, the specification is the function header + pre/post conditions and the implementation is the local variables + body of subroutine. 

When you are writing abstract data types, the specification is the definition of data type + operations defined on that type. The implementation is the program needed to effect those operations. In C the specification is usually a header file containing type and function declarations together with a .c file in which they are implemented. 

Abstract data types are organized into modules. Each module contains the variable definitions (structures) and operations required to meet the specification of the ADT. 

The module exports a 'type', such as list or tree or stack that a programmer can use to declare variables. The variables can then be manipulated using the operations defined within the ADT. 

The most important part of this process is that the user of the variable types only needs to know WHAT is possible, but has no need to know HOW it is implemented. The type is abstract from the point of view of the user. 

An abstract data type is usually provided to the developer in the form of a library or module. 

Some operations are common to most ADT specifications. In particular, pretty much all ADT modules need to provide mechanisms for the following operations: 

- Creating the ADT (initialization of internal variables/allocation of     dynamic structures) 
- Destroying the ADT (management of de-allocation of dynamic     resources) 
- Adding data to the ADT 
- Removing data from the ADT 
- Getting the value of data in the ADT 

The details of how those operations behave vary in the different kinds of ADTs, but the core purpose of the operation remains constant. 

### Worked Example: The Fraction ADT 

Suppose you were writing a program that required a representation of fractions. It is not always sufficient to convert fractions to decimals, sometimes fractions need to stay as fractions. A fraction ADT that allowed the programmer to declare a variable of type fraction would be extremely useful. 

First, we need a definition of what a fraction is. Fraction: A fraction is a number a/b where a,b are integers, b is non-zero. 

#### Operations 

The first step in designing an ADT is to imagine what operations are required. In addition to the core operations of create, insert, read, destroy the fraction ADT will need: 

- add (subtraction is just adding with negative numbers) 
- multiply (really just repeated adding, but would be nice to have it as a separate operation) 

ADT specification for Fraction 

```
    ADT specification for Fraction

    create_fraction(numerator, denominator): Fraction
        preconditions: none
        postconditions: a fraction is created with the appropriate numerator 
                        and denominator
    get_numerator(Fraction): number
        preconditions: an initialized Fraction is given as the parameter
        postconditions: none
    get_denominator(Fraction): number
        preconditions: an initialized Fraction is given as the parameter
        postconditions: none
    destroy_fraction(Fraction)
        preconditons: the parameter Fraction is initialized
        postconditions: the fraction is destroyed and memory released if necessary
    add(Fraction, Fraction): Fraction
        preconditions: two initialized fractions are passed in as parameters
        postconditions: the two fractions are added together and the result is 
                        placed in a new Fraction variable that is returned to the 
                        calling procedure
```
The ADT could have many other operations as well. For example, it could have a function to display/print a fraction or the ability to create a fraction type from a string representation of the fraction (i.e. \"one half\" or \"three fifths\"). 

#### Example Code 

Here's an example of what some of the fraction code might look like in C. First, the .h file contains the definition of the struct as well as the prototypes for the functions that operate on that struct. 
```c
     /**
     * @file fraction.h
     * @author Judi McCuaig
     * @date January 2017
     * @brief API for a fraction ADT
     */
    #ifndef _JRM_FRACTION
    #define _JRM_FRACTION

    fraction.h

    typedef struct {
      int integer;
      int numerator;
      int denominator;
    } Fraction;

    /** Creates a fraction from an integer numerator and denominator
    *@return NULL if the creation is unsuccessful
    *@param integer value for the numerator
    *@param integer value for the denominator
    **/
    Fraction * create_fraction(int numer, int denom);

    /** Adds two fractions and returns a new fraction that is the result of the addition
    *@return NULL if the addition is unsuccessful
    *@param Pointer the first Fraction operand
    *@param Pointer to the second Fraction operand
    **/
    Fraction * add ( Fraction *fractOne, Fraction *fractTwo );

    #endif
```
The `.c `file doesn't need to redefine the struct because the `.h` file is included. The .c file is used to flesh out the implementation of the
functions.

```
    /**
     * @file fraction.c
     * @author Judi McCuaig
     * @date January 2017
     * @brief implementation of fraction ADT
     */
    #include "fraction.h"

    Fraction * create_fraction(int numer, int denom){
      Fraction * temp = malloc(sizeof(Fraction)*1);
      temp->numerator = numer;
      temp->denominator = denom;
      return(temp)
    }

    Fraction * add ( Fraction *fractOne, Fraction *fractTwo ){
      Fraction result= malloc(sizeof(Fraction)*1);
      int largeCommonDenominator;
      int part1, part2, numeratorResult;
      hcd = fractOne->denominator * fractTwo->denominator;
      part1 = fractTwo->denominator * fractOne->numerator;
      part2 = fractOne->denominator * fractTwo->numerator;
      numeratorResult = part1 + part2;
      result->numerator = numeratorResult;
      result->denominator = largeCommonDenominator;
      return result;
    }
```

The fraction ADT can be used by simply including the .h file in the c program that needs the ADT and then compiling the fraction.c program in with the application.c program. 

```c
    /**
     * @file application.c
     * @author Judi McCuaig
     * @date January 2017
     * @brief use of Fraction ADT
     */
    #include "fraction.h"

    int main(void){
      Fraction * myFraction = create_fraction(1,2);
      Fraction * myOtherFraction = create_fraction(3,4);
      Fraction * theAnswer = add(myFraction, myOtherFraction);
    }    } 
```
## Information Hiding (Encapsulation) 

Information Hiding is one way to achieve abstraction. The details of the library implementation are hidden by providing functions to perform operations on the data structure instead of allowing programmers to work directly with the attributes of the data structure. The user of the ADT must use ONLY the interface (the available operations) of the ADT and must resist the temptation to go 'under the hood' and use the component parts. 

Information Hiding is also called encapsulation. Encapsulation helps to prevent errors when a library of functions is updated. For example, suppose you were using a String ADT that provides a `stringLength(String)` operation to return the length of the string. Suppose further that you knew that the length of the string was stored as an integer in the ADT because you had looked at the source code. If, in your code, you write `int size = stringLength(myString);` you are guaranteed (because of preconditions and postconditions) that you will get the length of the string returned. 

However, if you chose to ignore the encapsulation and bypassed the interface, writing the following instead `int size = myString->length` you could end up with code that gave errors. In this situation what would happen if the author of the String library gives you an update that changes the declaration of length in the struct from int to double? Your previously working code will break, because you didn't use the interface. 