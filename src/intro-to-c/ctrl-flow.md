# Control Flow

Control flow is an integral part of any computer program. They allow use to change which parts of a program run at runtime. C features three main categories of control flow, the first being `if` statements and its extensions which are the most common type of control flow used in C. The other two are switch statements and the ternary operator which provide slightly different semantics to their `if` counterparts.

## `if` Statements

`if` statements are the most primitive form of control flow in programming. In essence, some block of code is isolated from the rest of the program, protected by some Boolean expression. If the Boolean expression evaluates as truth then the block of code is executed. In C the keyword `if` is used to introduce an `if` clause. This is the part of the statement that contains a Boolean expression (called a redicate) which is evaluated on arrival. The rest of the `if` statement is a block of code nested in braces which only executes when the `if` clause is `true`.

<!-- > If are often implemented as a conditional jumps when compiled to assembly languages. -->

```c
#include <stdio.h>

int main()
{
    int a = 4;

    if (a > 5)
    {
        puts("a > 5");
    }

    return 0;
}
```

> What do you think the output of the above code is?

### `else` Statements

Often an `if` statement on its own is not enough because there will always be two potential outcomes of the Boolean predicate the `true` and the `false` branches and we will often want to handle the case when the predicate fails. This is where an `else` statement comes in. `else` statements have no predicate clause as it is bound to the alternative outcome of an `if` clause. C uses the `else` keyword to introduce the `else` statement which is just another code block surrounded in braces.

```c
#include <stdio.h>

int main()
{
    int a = 4;

    if (a > 5)
    {
        puts("a > 4");
    }
    else
    {
        puts("a <= 4");
    }

    return 0;
}
```

> **Note:**
>
> The placement of braces in C is not strict ie. the above can be written as:
>
> ```c
>   #include <stdio.h>
> 
>   int main() {
>       int a = 4;
>
>       if (a > 5) {
>           puts("a > 4");
>       } else {
>           puts("a <= 4");
>       }
>
>       return 0;
>   }
> ```

### `else-if` Clauses

C allows use to extend the usage of `else` statements with additional `if` clauses. This allows you to form an `else-if` clause which allows you to test multiple predicates and select only one block of code to execute. These additional clauses are called branches of the program as the line of execution can differ depending on runtime conditions.

```c
#include <stdio.h>

int main()
{
    int a = 4;

    if (a > 5)
    {
        puts("a > 4");
    }
    else if (a == 4)
    {
        puts("a == 4");
    } 
    else
    {
        puts("a < 4");
    }

    return 0;
}
```

> **Note:**
>
> Inefficient usage of branching constructs can cause massive slow downs of many systems at large scales due to a CPU level optimisation called branch prediction which tries to 'predict' which branch is most likely to occur and load the instructions corresponding to its code block into the cache ahead of time. However, a large number of branches increases the chance of these algorithms being incorrect which can lead to a cache miss which involves the CPU having to wipe the cache of the prefetched instructions and then lookup and load the correct instructions which can be expensive if the branching code runs a lot.

## `switch` Statements

The other main control flow construct in C is called the `switch` statement. These take an integral value and matches it against a particular `case` for which it is equal and executes the corresponding code block. While similar are to `if` statements, `switch` statements differ in a subtle way. `switch` statements allow for fallthrough which means that the line of execution will continue through different cases if the `switch` statement is not broken out of using a `break` statement. The most common use of `switch` statements is with enums as they allow you to use an enum to represent a finite list of possible states and handle each case accordingly. `switch` statements can also have a default case to handle any uncaught matches.

```c
#include <stdio.h>

enum cmp_result_t { UNDEF, EQUAL, LESS, GREATER };

int main()
{
    int a = 4;
    cmp_result_t cmp_r = UNDEF;

    if (a > 5)
    {
        cmp_r = GREATER;
    }
    else if (a == 4)
    {
        cmp_r = EQUAL;
    } 
    else
    {
        cmp_r = LESS;
    }

    switch (cmp_r)
    {
        case EQUAL:
            puts("equal");
            break;
        
        case LESS:
            puts("less");
            break;

        case GREATER:
            puts("greater");
            break;

        default:
            puts("NaN");
            break;
    }

    return 0;
}
```

## Ternary Operator

The final control flow construction is the ternary operator. This is a condensed `if` statement that is able to return a value. It involves a Boolean predicate followed by two expressions that may return or have side effects (ie. print something). The ternary operator comprises of the symbol `?:` where `?` is used to separate the predicate and branches and `:` is used to separate the branches.

```c
#include <stdio.h>

int main()
{
    int a = 4;
    a > 4 ? puts("a > 4") : puts("a <= 4");

    int b = a > 4 ? a + 5 : a * 100;
    printf("%d\n", b);

    return 0;
}
```
