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

> Note:
>
> `bool`, `char` and `int` (and sized variants) are defined as integral types ie. they are all number types.

## Variables
