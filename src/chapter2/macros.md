# Macros & The Preprocessor

Sometimes we need to control how source code is compiled, enable certain parts of the source code while disabling other parts. How do you do this? This is done using macros in C. Macros are compile time expressions that are executed by a part of the compiler called the preprocessor.

## What is a macro?

Macros are expressions that are evaluated and removed from the final source code. They are created using a `#` followed by a macro identifier. One macro we have used consistently throughout this book is the `#include` macro which is used to copy the source code from header files into other source and header files. Macros in C mostly perform in-source text replacement.

> **Note:** Conventionally, macro symbols (names) are written in all uppercase to prevent conflation with regular source code.

### `#define` & `#undef`

The most common and general macro is the `#define` macro. This allows you to define a symbol that will be replaced with its definition during the compilation phase. `#undef` can be used to undefine a symbol so that its usage is ignored. Names, value, types and even function-like entities can be defined and undefined using `#define` and `#undef`.

```c
#include <stdio.h>

#define INT int

#define ADD(x, y) x + y

int main()
{
    INT i = 5;  //< Ok
    printf("%d\n", i);
    printf("%d\n", ADD(i, 2));

    #undef INT
    // INT a = 4;  //< Compile time error

    return 0;
}
```

> Note: Even though you can define function-like entities using macros I would highly recommend against it in 99% of cases as it is nearly impossible to debug as the macros are expanded and removed very early on in the compilation of a program.

#### Include Guards

One common use of macros is for include guards. These are valueless macros that are defined once for a header file and only expose the contents of the header file if the macro is not defined. This prevents headers from being included twice and causing a redefinition or duplication error. How does this work? Essentially, when a header is first encountered, a macro is checked. If it is **_not_** defined we then define it and define the rest of the contents of the header. If it was already defined then the header is 'empty'. This stops the contents of headers being imported multiple times or as a transitive dependency.

```c
#ifndef HEADER
#define HEADER

/// Headers contents

#endif  /// HEADER
```

#### Defining Macros from the Command Line

Macros are able to be defined from the command line through the compiler. Many compilers support a `-D` and `-U` fag which can define and undefine macros in source code respectively. These are typically used to control macros similar to header guards which control which parts of a codebase are defined eg. for different OS or graphical backends.

```sh
# Forces in to be defined
gcc -o main -DUSE_WINDOWS_INT main.cpp
```

### `#if`, `#elif`, `#else`, `#ifdef`, `ifndef` and `#endif`

The other common class of macros is the control flow macros. These can control which parts of the source code are visible to the compiler thus which parts are compiled. They can be used just like regular control flow using predicates to determine the correct part of the codebase to use. However, they often are used with empty macros which are control from the command line to easily control which parts of the code we wish to compile. The `#ifdef` and `#ifndef` macros are slightly different in the sense that they check if other macros are defined as apposed to checking a predicate. All control flow macros must end in `#endif` for the final macro expression to help denote the end of a macros scope as macros do not use braces.

```c
#include <stdio.h>

#if ADD
    int op(int a, int b)
    { return a + b; }
#elif SUB
    int op(int a, int b)
    { return a - b; }
#else
    int op(int a, int b)
    { return a * b; }
#endif /// ADD

int main()
{
    printf("%d\n", op(5, 6));

    return 0;
}
```

> Try it yourself. Write up the following code and see how using the `-D` flag when compiling it changes the outcome.

### `#pragma`

The final macro worth mentioning is the `#pragma` macro. This macro is special is it is used by compilers and libraries to implement specific and unique features to their platform. In essence these are non-portable and non-standard macro that are specific to the platform you are targeting or compiler you are building with. A common `#pragma` directive in many C compilers in the `#pragma once` directive which is designed to replace the need for header guard.

```c
#pragma once

/// Header's content

```
