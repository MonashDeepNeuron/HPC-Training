# Structures

So far we have only been able to to manipulate primitive data types and collections of a single type but what if we want to manipulate and store data that is of different types. This is where structures come in. Structures are used to hold data of different types in a compact format. Structures are created using the `struct` keyword paired with a unique name followed by a brace scope of variable declarations. To then create a variable of the structure type you again use the `struct` keyword and the structures type name followed by a variable name. You can then initialise the fields using a comma separated list, enclosed in braces where each element is the desired value for initialising the field of the structure. The fields are then accessed using the variable and the member access operator (`.`) paired with the field's name.

```c
#include <stdio.h>

struct A
{
    int i;
    double d;
    char* c;
};

int main()
{
    struct A a = { 5, 576.658, "Hello" };
    printf("%d\n", a.i);
    printf("%f\n", a.d);
    printf("%s\n", a.c);

    return 0;
}
```

> Note:
>
> - Structures do not support methods.
> - Elements in a structure a layed out contiguously ie. each element is right next to each other.
