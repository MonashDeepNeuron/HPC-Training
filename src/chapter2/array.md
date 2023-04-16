# Arrays & Strings

There are two vital data types we haven't formally looked at yet. These are the string and array data types. These are integral to building collections of data and being able to store large chunks of data in a single variable.

## Strings

What are strings? Strings are a sequence bytes represented as a collection of characters (`char`s) that (typically) end in a null-string-terminator. Strings are the primary type used to interact with any form of IO with all forms of data being serialized to and from strings. C doesn't have a dedicated type for strings. This is because strings are just a collection of `char` and this can simply be represented as a contiguous block of memory interpreted as `char`. To create a block of `char`, use the `[]` initialiser after the variable name. This will create a block that is the same size as its initialiser string. String literals are introduced using double quotes. eg.:

```c
char str[] = "Hello";
```

> Note:
>
> - Unlike some languages; like Python, there is a big difference between single quotes (`''`) and double quotes (`""`). Single quotes are exclusive to character types while strings are always double quotes, even if they only store a single character.
> - If you have intellisense and hover over a string literal you might notice it states its size as one more then the number of characters actually in the string. This is because all string literals have an invisible character `'\0'` called the null-terminator which is used to denote the end.

## Arrays

Strings are not the only collection type; in fact, they are a specialisation of a more generic structure in C called arrays. Arrays represent a contiguous sequence of elements, all of which must be of the same type. Arrays also must have a known size at compile time meaning they cannot be dynamically resized. Elements of an array are accessed using the subscript operator `[]` which takes a 0-based index. Arrays in C are very primitive and are designed to be a close analogy to a machine memory. Array types are any variable name suffixed with `[]`. The size of the array can be explicitly set by passed an unsigned integral constant to the square brackets however, if the initial size is known then the size can be elided. Arrays are initialised using an initialiser list which are a comma separated list of values surrounded in braces (`{}`) with strings being the only exception.

> Note: Because there are no complex types in C, strings are just an array of `char`.

```c
#include <stdio.h>

int main()
{
    int a[] = { 1, 2, 3, 4 };
    char b[5] = { 'H', 'e', 'l', 'l', 'o' };

    printf("{ %d, ", a[0]);
    printf("%d, ", a[1]);
    printf("%d, ", a[2]);
    printf("%d }\n", a[3]);

    printf("\"%c", b[0]);
    printf("%c", b[1]);
    printf("%c", b[2]);
    printf("%c", b[3]);
    printf("%c\"\n", b[4]);

    return 0;
}
```
