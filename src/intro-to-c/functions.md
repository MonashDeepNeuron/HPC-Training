# Functions

The final core construction in C is functions. Functions are the most basic form of abstraction in all of computing. They allow us isolate and organise code into a common pattern that we can utilise and execute as we need.

## What is a function?

Functions in C, while called functions, are more like sub-routines, a packaged piece of executable code, almost like a mini program we can use in a larger context. The reason I mention this is because functions in C are not pure functions ie. they are not as sound as mathematical functions, they're more hacky then that. This is largely because functions in C can have side effects and we have actually seen this a lot already. The difference between a pure function and a subroutine is that a function takes some input data called a parameter, argument or point (or tuple of data if multiple input points are needed) and returns another value. There is a clear pipeline of inputs and outputs to a function of this nature; think of an add (`+`) function, two arguments are given and a single value is returned. Side effects are operations which have an effect on something outside the function without communicating that information in its input or output. Be best example of side effects are any IO function like `puts()` or `printf()`. These are functions by the C standard however, notice how we never took into account that we don't capture a return value from `printf()` but it still printed to the screen or even the possibility that `printf()` may have returned something and `printf()` does. In fact it returns the number of characters written to its output stream (standard out - `stdout`) and this is where the issue arises. By the definition of a function we described above, `printf()` is more like a character counter function after formatting as it inputs are just a string and a variable number of additional points and it returns the number of characters of the final formatted stream. Where is the information encoding the interaction is has with the screen? And thats just it, it doesn't. This is called a side effect, behaviour that is not defined or encoding in the information of the function. C functions have the capabilities to be pure but can also have side effects and this is what makes C functions more akin to sub-routines however, while this difference is good to know they are used like functions in other languages.

```c
#include <stdio.h>

int main()
{
    int a = 5;
    double b = 365.57;
    unsigned sz = printf("%d + %f = %f\n", a, b, a + b);
    printf("%u\n", sz);

    return 0;
}
```

## Function Signatures & Definitions

Functions in C have a particular signature. This is used to differentiate functions from each other. The key part of a signature is the functions name. This is used to call or refer to the function. In C there can be no duplicate functions meaning every function name must be unique, at least in the current translation unit (file). This includes name imported from header files (eg. `<stdio.h>`). A functions signature is also made up from the type of its input points and the return type. In general functions are declared first by their return type followed by their name. The points of a function are specified in a comma separated list surrounded in a parenthesis. Each point is a type declaration followed by a name, identical syntax to variable declarations. The body of a function is defined like other C constructions, using braces. Function bodies must contain a `return` statement which returns a value of the same type as the functions return type. Functions are also able to return `void` meaning that the function doesn't return anything. They are also able to take no input points.

```c
int f(int a, double b)
{
    /// ....
}
```

> **Note:**
>
> The declaration (signature) of a function can be declared separately (in a header file) from its definition (signature and body defined in a corresponding source file). If the declaration and definition are separated then the declaration replaces the braced code block with a semicolon `;` at the end of the signature's line. eg:
>
> ```c
> int f(int a, double b);
> ```

## Calling Functions

Functions are called using the functions name suffixed with parenthesis. Within the parenthesis, the arguments are passed in the order they were declared in to the function. The data passed to a function will always copy the data to the functions input points. Functions are often declared and defined outside `main()` so they can be accessed from various parts of a codebase.

```c
#include <stdio.h>

void print_int_array(int arr[], unsigned long long sz)
{
    for (unsigned long long i = 0; i < sz; ++i)
    {
        printf("%d\n", arr[i]);
    }
}

int main()
{
    int arr[] = { 1, 2, 3, 4, 5 };
    print_int_array(arr, sizeof(arr) / sizeof(arr[0]));

    return 0;
}
```

> **Note:** If an array is used as an input point to a function, the size doesn't have to be specified.
