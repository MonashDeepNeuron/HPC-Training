# Dynamic Memory

So far we have only used the stack for memory which has limited how much memory we can actually utilise. While this limit is implementation defined (differs depending on the platform and compiler) its also best not to fill up the stack with too much data that doesn't need to be there. Instead we can utilise the heap memory we discussed earlier, which is supplied by the OS. But how do we request this memory? For this we need to request the OS to allocate the necessary memory for our use and then allow us to access it. This is done by calling `malloc()`, which takes as input the size; in bytes, of the memory we wish to request from the OS and returns a `void*` to the allocated block. `malloc()` can be found in the `<stdlib.h>` header. Every called to `malloc()` must be paired with a call to `free()` which takes a pointer to a `malloc()` allocated block and returns the memory to the OS. Without `free()` the allocated memory will most likely not be freed by your program and thus leaks.

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int* a = (int*)malloc(7 * sizeof(int));  //< Allocate 7 integers
    printf("a lives at: %p\n", a);

    for (int i = 0; i < 7; ++i)
        a[i] = i;

     for (int i = 0; i < 7; ++i)
        printf("%d\n", a[i]);

    free(a);
    return 0;
}
```

> **Note:**
>
> - Memory allocated by `malloc()` is left in an uninitialised stake meaning whatever values that were left in that memory block remain ie. the junk that is help by the memory doesn't get cleared.
> - Because `malloc()` just takes the number of bytes we want to allocate as a parameter we must calculate the total size of memory we need which depends on the size of an individual element ie. \\(n × s\\) where \\(n\\) is the number of elements we desire and \\(s\\) is the size of an individual element. We can use the `sizeof` operator on a type name to get the size of that type.

## Zero-Initialised Memory Allocation

Notice above we stated that `malloc()` returns a block of uninitialised memory but what if you want to memory that is initialised ahead of time. For this we use `calloc()`. This takes two parameters, the number of objects we wish to allocate and the size of each object. The memory block returned will have all of its bits initialised to 0.

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int* a = (int*)calloc(4, sizeof(int));
    printf("a lives at: %p\n", a);

    for (int i = 0; i < 4; ++i)
        printf("%d\n", a[i]);

    free(a);
    return 0;
}
```

## Reallocated Memory

We can also reallocate data to fit a larger or smaller amount. The elements from the old block will be copied to the new location until the new array is full or there are no more elements to copy. `realloc()` my not actual allocate memory in a new locating if there is free space next to the existing array. `realloc()` also works like `malloc()` where the new memory is left uninitialised. `realloc()` takes two parameters, the old pointer address and the new size.

```c
#include <stdio.h>
#include <stdlib.h>

int main()
{
    int* a = (int*)malloc(4 * sizeof(int));
    printf("a lives at: %p\n", a);

    for (int i = 0; i < 4; ++i)
        a[i] = i;

    for (int i = 0; i < 4; ++i)
        printf("%d, ", a[i]);

    a = (int*)realloc(a, 7);
    printf("\na lives at: %p\n", a);

    for (int i = 0; i < 7; ++i)
        printf("%d, ", a[i]);

    free(a);
    return 0;
}
```

> **Note:**
>
> - Any memory allocated by `malloc()`, `calloc()` or `realloc()` must be returned to the OS by a call to `free()`.

## General Memory Utilities

C features a few byte based memory operations that is able to set, compare and copy data. These are `memset()`, `memcmp()` and `memcpy()` respectively. These memory utilities are found in the `<string.h>` header.

### `memset()`

`memset()` takes an input pointer that you wish to modify, an `int` value which is narrowed to an `unsigned char`; such that each byte of the input memory is set this value, and a count for the number of bytes affected. This is not to be confused will a general fill algorithm as this function writes to individual bytes not to individual elements in a memory block.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main()
{
    int* a = (int*)calloc(4, sizeof(int));

    for (int i = 0; i < 4; ++i)
        printf("%d, ", a[i]);

    puts("");

    memset(a, (unsigned char)1, 6);

    for (int i = 0; i < 4; ++i)
        printf("%d, ", a[i]);

    free(a);
    return 0;
}
```

### `memcmp()`

`memcmp()` will lexicographically compare the bytes of two input pointers up until the specified count. Returning a negative value if the bytes passed as the left argument is greater than the right, 0 if they are the same or a positive value of the right is greater then the left.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main()
{
    int* a = (int*)calloc(4, sizeof(int));
    int* b = (int*)calloc(4, sizeof(int));

    for (int i = 0; i < 4; ++i)
        printf("%d, ", a[i]);

    puts("");

    for (int i = 0; i < 4; ++i)
        printf("%d, ", b[i]);

    puts("");

    int cmp = memcmp(a, b, 4);
    printf("a = b: %d\n", cmp);

    memset(a, (unsigned char)1, 6);

    cmp = memcmp(a, b, 4);
    printf("a = b: %d\n", cmp);

    free(a);
    free(b);
    return 0;
}
```

### `memcpy()`

`memcpy()` is probably the most useful as it allows you to efficiently copy the bytes directly from one memory block to another. It takes two input pointers with the first be the destination and the second being the source. it also takes a count for the number of bytes you want to copy.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main()
{
    int* a = (int*)calloc(4, sizeof(int));
    int b[] = { 1, 2, 3, 4 };

    for (int i = 0; i < 4; ++i)
        printf("%d, ", a[i]);

    puts("");

    for (int i = 0; i < 4; ++i)
        printf("%d, ", b[i]);

    puts("\n");

    memcpy(a, b, 4 * sizeof(int));

    for (int i = 0; i < 4; ++i)
        printf("%d, ", a[i]);

    puts("");

    for (int i = 0; i < 4; ++i)
        printf("%d, ", b[i]);

    puts("");

    free(a);
    return 0;
}
```

> **Note:** If you access more bytes than what is allocated to a pointer using any of these algorithms or even directly will cause undefined behaviour which might (hopefull) crash the program or lead to consequences that are very hard to trace. Don't do it.

## Dynamic String Utilities

Since operating on strings is so common their are more specific string manipulation functions available. These allow you to more easily work with character arrays and manipulate them in the way you would expect. These functions can be found in the `<string.h>` header.

### `strlen()`

Obtains the length of a null-terminating string, not including the null-terminated character. It is undefined if the string is not null-terminated.

```c
#include <stdio.h>
#include <string.h>

int main()
{
    char c[] = "Hello";

    printf("sizeof(c) = %zu\n", sizeof(c));
    printf("strlen(c) = %zu\n", strlen(c));

    return 0;
}
```

### `strcmp()`

Compares to strings lexicographically, same manner as `memcmp()`. The return value is also an `int` with a negative value meaning the left is greater than the right, 0 meaning they are the same and a positive value meaning the right is greater than the left.

```c
#include <stdio.h>
#include <string.h>

int main()
{
    char a[] = "Hello";
    char b[] = "Hello";

    int cmp = strcmp(a, b);
    printf("a = b: %d\n", cmp);

    a[1] = 'E';
    cmp = strcmp(a, b);
    printf("a = b: %d\n", cmp);

    return 0;
}
```

### `strcpy()`

Allows you to efficiently copy the characters from one string to another including the null-terminator. The first argument is the destination adn the second is the source. Returns a copy of the destination pointer.

```c
#include <stdio.h>
#include <string.h>

int main()
{
    char a[] = "Hello";
    char b[strlen(a) + 1];  //< +1 to accommodate the null-terminator

    printf("%s\n", a);
    printf("%s\n\n", b);

    strcpy(b, a);

    printf("%s\n", a);
    printf("%s\n", b);

    return 0;
}
```

### `strcat()`

Concatenates two strings by appending the second string to the end of the first.

```c
#include <stdio.h>
#include <string.h>

int main()
{
    char a[13] = "Hello";
    char b[] = " World!";

    printf("%s\n", a);
    printf("%s\n\n", b);

    strcat(a, b);

    printf("%s\n", a);
    printf("%s\n", b);

    return 0;
}
```
