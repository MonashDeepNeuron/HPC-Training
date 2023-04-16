# Types & Variables

## Fundamental Data Types

In C there are six fundamental data types, `bool`, `char`, `int`, `float`, `double` and `void`. There are also a variety of modified integral and floating point types to allow for different sizes.

- `bool` - Boolean type, can either be `true` or `false`. It's width is 8-bits (1 byte).
- `char` - Character type. Can be unsigned or signed. Represents any ASCII character value. Usually has a width of 8-bits (1 byte).
- `short int` or `short` - Number type, can be signed or unsigned. Only represents whole number values. Usually has a width of 16-bits (2 bytes).
- `int` - Number type, can be signed or unsigned. Only represents whole number values. Usually has a width of 32-bits (4 bytes).
- `long int` or `long` - Number type, can be signed or unsigned. Only represents whole number values. Sometimes has a width of 32-bits (4 bytes) or 64-bits (8 bytes).
- `long long int` or `long long` - Number type, can be signed or unsigned. Only represents whole number values. Has a width of 64-bits (8 bytes).
- `float` - Single precision floating point type, represents decimal number values. Usually has a width of 32-bits (4 bytes).
- `double` - Double precision floating point type, represents decimal number values. Usually has a width of 64-bits (8 bytes).
- `long double` - Extended double precision (or quadruple precision) floating point type, represents decimal number values. Usually has a width of at least 64-bits (8 bytes) but sometimes has a width of 128-bits (16 bytes).
- `void` - Incomplete data type. Indicates the absence of a type of value.

> **Note:** `bool`, `char` and `int` (and sized variants) are defined as integral types ie. they are all number types.

## Variables

Variables are integral to computer programming. Variables are objects that own a piece of data. What data or rather value of a variable can change throughout the lifetime of a program. To declare a variable in C, we first declare its type. The type predicates which operations are valid for that variable as well as tells the compiler the size of the variable. We then git it a name and assign it an initial value.

```c
/// General syntax: type name = value

int a = 10;
```

In C variables have 'value semantics', this means that the data of a variable is always copied. For the example above, the data representing the literal `10` is copied into the location of `a` by the assignment operator (`=`).

> **Note:** Often the compiler will likely try to construct variables (like `a`) directly to the evaluated value of the right-hand-side of the `=` ie. construct `a` directly from `10` rather than create `a` with a dummy value and then copy `10` to `a`'s location. This is called copy elision or return value optimization.

You can also create new variables and initialize them to the value of an existing variables using the same syntax. Because C uses value semantics, `b` now has its own copy of the data owned by `a`. These can now be modified independently of each other.

```c
int a = 10;
int b = a;
```

> **Note:**
>
> - Literals are data with a constant value that are predefined. They are often used to initialise variables to a particular starting value.
> - A `char` literal is a single letter surrounded in single quotes eg. `'a'` is a literal for the letter 'a'.

### Constant Data

Sometimes you want data to be constant or immutable. This is data that does not and cannot change during its lifetime. To do this in C we use the `const` qualifier before the type of a variable. This marks some variable as constant. Constant data must be given an initialiser or the program will not compile. `const` can be applied to any variable of any type but a constant variable cannot be modified to be mutable however, you can create a copy of a constant variable that is mutable.

```c
const int a = 4;
```

## Operators

Operators are the most primitive way to manipulate data and variables in C. There are four major categories for operators these being arithmetic, bitwise, logical and assignment. Each operator is written in either infix (binary), prefix or prefix (unary) form. Most operators return the result of their evaluation meaning it can can be assigned to a new variable however, some modify the data in-place, this includes all assignment operators and the increment and decrement operators (which do both).

> **Note:** Parenthesis are used to control the order of execution, separating sub-expressions.

### Arithmetic Operators

Arithmetic operators work for integral and floating point type. They are the most common type of operator used in C.

| Operator |        Name       |                                     Description                                    | Example |
|:--------:|:-----------------:|:----------------------------------------------------------------------------------:|:-------:|
|    `+`   |      Addition     |                                   Adds two values                                  | `a + b` |
|    `-`   |    Subtraction    |                                Subtracts two values                                | `a - b` |
|    `*`   |   Multiplication  |                                Multiplies two values                               | `a * b` |
|    `/`   |      Division     |                                 Divides two values                                 | `a / b` |
|    `%`   |  Modulo Division  | Modulo divides two values ie. returns the remainder of the division of two numbers | `a % b` |
|   `++`   |  Prefix Increment |                  Increment the value in-place and return new value                 |  `++a`  |
|   `--`   |  Prefix Decrement |                  Decrement the value in-place and return new value                 |  `--a`  |
|   `++`   | Postfix Increment |                  Increment the value in-place and return old value                 |  `a++`  |
|   `--`   | Postfix Decrement |                  Decrement the value in-place and return old value                 |  `a--`  |
|    `+`   |     Posigation    |                            Set sign of value to positive                           |   `+a`  |
|    `-`   |      Negation     |                            Set sign of value to negative                           |   `-a`  |

> **Notes:**
>
> - Binary arithmetic operators will a return value whose type is the larger of `a` or `b`.
> - If `a` or `b` is smaller than its counterpart, the smaller will be implicitly promoted to a larger type.
> - Division between two integral types performs integer division.
> - Division between a floating point type and any other type (integral or floating point) performs floating point division by implicitly promoting the integral or smaller argument to an adequate type or size.
> - Modulo division does not exist for floating point types.

### Bitwise Operators

Bitwise operators are used to manipulate the individual bits of an integral type allowing precise control of the most fundamental data type.

|        Operator         |        Name        |                      Description                      |          Example        |
|:-----------------------:|:------------------:|:-----------------------------------------------------:|:-----------------------:|
|           `~`           |     Compliment     |              Inverts the bits of a values             |           `~a`          |
|           `&`           |         And        |              Ands the bits of two values              |          `a & b`        |
|   <code>&vert;</code>   |         Or         |               Ors the bits of two values              | <code>a &vert; b</code> |
|           `^`           | Exclusive Or (Xor) |              Xors the bits of two values              |          `a ^ b`        |
|           `<<`          |     Left Shift     |  Shifts the bits of `a` to the left by `b` positions. |          `a << b`       |
|           `>>`          |     Right Shift    | Shifts the bits of `a` to the right by `b` positions. |          `a >> b`       |

> **Note:**
>
> - Bitwise operators do not exist for floating point types.
> - Bits are lost from shift operators.
> - Left shift (`>>`) pads with zeros ie. adds a zero in the new empty position.
> - Right shift (`<<`) pads with the most significant bit ie. the new empty position is filled with the same value as the previous occupant.
> - Left and right shifts are formally described respectively as: \\(a << b ≡ a * 2^{b} mod(2^{N})\\) and \\(a >> b ≡ \frac{a}{2^{b}} mod(2^{N})\\) where \\(N\\) is the numbers bits in the resulting value.

### Logical Operators

Logical operators operate on Boolean expressions statements. They only evaluate to another Boolean expression (ie. type `bool`).

|           Operator          |          Name         |              Description             |            Example            |
|:---------------------------:|:---------------------:|:------------------------------------:|:-----------------------------:|
|             `!`             |          Not          |         Negates the Boolean.         |            `!a`               |
|             `&&`            |      Logical And      |    Both `a` and `b` must be true.    |           `a && b`            |
|  <code>&vert;&vert;</code>  |       Logical Or      |    Either `a` or `b` must be true.   | <code>a &vert;&vert; b</code> |
|             `==`            |         Equals        |         `a` is equal to `b`.         |           `a == b`            |
|             `!=`            |       Not Equal       |       `a` is not equal to `b`.       |           `a != b`            |
|             `<`             |          Less         |         `a` is less than `b`.        |           `a < b`             |
|             `>`             |        Greater        |       `a` is greater than `b`.       |           `a > b`             |
|             `<=`            |   Less than or equal  |   `a` is less than or equal to `b`.  |           `a <= b`            |
|             `>=`            | Greater than or equal | `a` is greater than or equal to `b`. |           `a >= b`            |

### Assignment Operators

Assignment operators will perform a binary operation between two values and assign the result to the left argument (excluding `=`).

|       Operator       |         Name         |                     Description                     |          Example         |
|:--------------------:|:--------------------:|:---------------------------------------------------:|:------------------------:|
|          `=`         |        Assign        |           Assigns the value of `b` to `a`           |          `a = b`         |
|         `+=`         |      Add Assign      |         Assigns the value of `a + b` to `a`         |         `a += b`         |
|         `-=`         |    Subtract Assign   |         Assigns the value of `a - b` to `a`         |         `a -= b`         |
|         `*=`         |    Multiply Assign   |         Assigns the value of `a * b` to `a`         |         `a *= b`         |
|         `/=`         |     Divide Assign    |         Assigns the value of `a / b` to `a`         |         `a /= b`         |
|         `%=`         | Modulo Divide Assign |         Assigns the value of `a % b` to `a`         |         `a %= b`         |
|         `&=`         |      And Assign      |         Assigns the value of `a & b` to `a`         |         `a &= b`         |
| <code>&vert;=</code> |       Or Assign      | Assigns the value of <code>a &vert; b</code> to `a` | <code>a &vert;= b</code> |
|         `^=`         |      Xor Assign      |         Assigns the value of `a ^ b` to `a`         |         `a ^= b`         |
|         `<<=`        |   Left Shift Assign  |         Assigns the value of `a << b` to `a`        |         `a <<= b`        |
|         `>>=`        |  Right Shift Assign  |         Assigns the value of `a >> b` to `a`        |         `a >>= b`        |

The result of any expression containing operators can be assigned to a new or existing variable by simply using the expression as the right argument of `=`.

```c
/// The value of a is the result of the expression.
double a = (6 + 7) / (5.0 * 4);  ///< a == 0.650000
```

### `sizeof`

There is also one final operator called the `sizeof` operator which returns the number of bytes a particular piece of data occupies in memory. The `sizeof` operator uses a function call syntax with the argument being the data to be queried.

```c
int a = 4;
double b = 3.154;

int sz_a = sizeof(a);   //< 4
int sz_b = sizeof(b);   //< 8
```

## Enumerations

The last data type we will look at is the enum. Enums are another integral data type however, they have a limited number of possible states where each state is named by the user. For example consider a Boolean type `Bool`; although a builtin type can be represented by a enum with its possibles states being `False` and `True`. The states or enumerators of an enum are integral constants ie. each name has a particular integer value associated with it. Using the `Bool` example again, the value of `False` could be 0 and the value of `true` could be 1. This would restrict a `Bool` to only being `True` or `False` (1 or 0).

```c
enum Bool { False = 0, True = 1 };
```

Enums in C can be named (like `Bool`) or unnamed where the variants are simply generated as named integral constants (similar to just creating constant variables for each variants). Enum variants are accessible as long as the enum is in scope meaning I could use say `False` anywhere in the program that `Bool` is in scope without having to express in the language directly that `False` comes from `Bool`. The enumerators of an enum always have an underlying type of `int` meaning they can be used like constant integer value due to C's weak type system. Enumerators will always start with a value of 0 if no value is specified and increase for each subsequent variant however, it is possible to specify any value for variants as long as they are unique.

## Type Casting

Often it is useful to be able to convert data of one type to another. This can be done via type casting. This involve prefixing a variable (or function call return) with the desired type you want to cast to surrounded in parenthesis. This will cast the bits of the current variable to the new type which can then be save to a variable of the appropriate type or passed to a functions expecting that type.

```c
#include <stdio.h>

int main()
{
    int i = 97;
    printf("i = %d\n", i);

    char ic = (char)i;  //< Cast to char
    printf("i = ic = '%c'\n", ic);

    return 0;
}
```
