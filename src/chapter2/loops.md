# Loops

Loops area another integral construct in almost every programming language. They allow us easily and efficiently express code that we want to repeat. Loops generally execute while a particular predicate is upheld. Loops are essential to programming generic algorithms that operate on constructs that have a varying number of elements such as arrays.

## `while` Loops

The most primitive of any loop is the `while` loop. As its name suggests a `while` loop will execute 'while' a particular predicate is still `true`. `while` loops have a similar syntax to `if` statements. Loops are often paired with an integral value indicating the current state of the loop. Because C loops are primitive and close analogies for the eventual assembly language they do not automatically track the state of the integral meaning you have to manually update its state.

```c
#include <stdio.h>

int main()
{
    int i = 0;
    while (i < 5)
    {
        printf("%d\n", i);
        i++;
    }

    return 0;
}
```

## `do-while` Loops

`do-while` loops are similar to `while` except that the body of the loop is guaranteed to execute at least once. This is because; unlike `while` loops, the predicate is checked at the end of each loop not the beginning.

```c
#include <stdio.h>

int main()
{
    int i = 0;
    do
    {
        printf("%d\n", i);               //< But this still runs once
    } while (i < 0);  //< Will never be true ^

    return 0;
}
```

## `for` Loops

While `while` loops will run while a predicate is `true` which can potentially be 'infinite', `for` loops differ slightly in their semantics. `for` loops typically run for a particular number of iterations and are usually used with arrays to efficiently perform operations on the entire array. `for` loops have three key sub-statements that control its execution. The first is a statement used to initialise a variable to represent the current state. The second is the predicate the controls whether the loops continues and the final one is a post-loop expression that runs at the end of each iteration and is often used to increment or modify the current state integral. Each of these statements are separated by a `;` in the clause (parenthesis) of the `for` loop.

```c
#include <stdio.h>

int main()
{
    int a[] = { 1, 2, 3, 4, 5 };

    for (int i = 0; i < sizeof(a) / sizeof(a[0]); ++i)
    {
        printf("%d\n", a[i]);
    }

    return 0;
}
```

> **Note:**
>
> - Any loop can be exited early using a `break` statement.
> - C doesn't have a function to retrieve the size of an array. However, we can use the `sizeof` operator to retrieve the total number of bytes the entire array occupies and then divide it by the size of one of the elements. This works because each element in an array are contiguous and aligned and thus it is easy to determine the number of bytes to jump for each element and because each element is the same size (type) then the total number of bytes is the array size types the size of each element.
