# User input in C

We're going to briefly discuss how to take user input  in C.

## scanf()
scanf() allows you to read different data types from the user's input and store them in variables, making it a versatile function for interactive applications. It enables you to control the input format, extract data from the input stream, and store it in the appropriate variables.

### Signature

The general siHere are some key points about the scanf() function and its variadic nature:

1)Variadic Function: scanf() is a variadic function, which means it can accept a variable number of arguments. The first argument is always a format string that specifies the expected input format, while subsequent arguments (after the format string) are the memory addresses of variables where the data will be stored.

2)Format Specifiers: The format string in scanf() consists of format specifiers, introduced by the % character, which indicates the expected type of input. For example, %d is used for integers, %f for floating-point numbers, %c for characters, %s for strings, etc. These format specifiers tell scanf() how to interpret and read the input data.

3)Variable Input: With scanf(), you can read multiple values of different data types in a single call, as long as the format string and the subsequent variable arguments match in number and order. For instance, scanf("%d%f", &num, &flt); will read an integer and a floating-point number from the user.

4)Address (&) Operator: Just like in printf(), when using scanf(), you need to provide the memory address of the variables where the data should be stored. This is done using the address-of operator &. For example, scanf("%d", &num); reads an integer from the user and stores it in the variable num.

5)Positional Arguments: Unlike printf(), scanf() does not support positional argument indexing in the format string. The variadic arguments are consumed in the same order they appear in the format string. For instance, scanf("%d %f", &num, &flt); expects an integer followed by a floating-point number from the user.

6)Handling Newlines: As mentioned before, scanf() can leave the newline character (\n) in the input stream, which may cause issues with subsequent input functions. To handle this, you can include a space before the format specifier, like scanf(" %c", &ch);, to skip any leading whitespace characters, including the newline.gnature of `scanf()` is quite unique in C and how it achieves it is a bit of compiler magic in order to actually implement but you do not have to worry about it. `scanf()` takes as its first argument a string that represents the output format of the printed text. The next argument is the `...`. This is called the ellipsis and it is used to represent a variable number of untyped function arguments. This allows you to pass ass many arguments as you want to `printf()` and it will print them all as long as there are an equivalent number of positional arguments in the format string. The variadic arguments are inserted in output string in the same order they are passed to `printf()` ie. there is now way to indicate in the format string which variadic argument to use at any given positional argument. The positional argument introducer character is the `%` followed by a modifier to indicate in incoming type.

```c
The C library function int scanf(const char *format, ...) reads formatted input from stdin.
```



### Example

// C program to implement
// scanf
#include <stdio.h>

int main()
{
	int a, b;

	printf("Enter first number: ");
	scanf("%d", &a);

	printf("Enter second number: ");
	scanf("%d", &b);

	printf("A : %d \t B : %d" ,
			a , b);

	return 0;
}




### Formatting Specification

The general format for the scanf () function format string is:

`%[*][width][length]specifier`

Thus the format specifier has the following parts:

1)Non-whitespace character:These are the characters except % that consume one identical character from the input stream.<br>
Whitespace character: All consecutive whitespace characters are considered as one whitespace character. The same goes forscape sequences too.<br>
2)Conversion specification: It has the following format:<br>
a)%: Character that specifies the beginning.<br>
b)*: Called assignment suppressing character. If present, the scanf does not assign the result to any receiving parameters. This parameter is optional.<br>
c)Field width:Optional parameter (a positive integer) that specifies a maximum field width.<br>
d)Length: Specifies the size of receiving an argument.

There are a variety of different options for each part of the specification. Below is a series of tables breaking down the various options for each sub-specifier but note that only _type-specifier_ is needed, the others are optional.

#### Type Specifiers

| Type Specifier |                                                                       Type                                                                       |           Example          |
|:--------------:|:------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------:|
|       `%`      |                                           Two sequential `%` will result in a single `%` being printed.                                          |              %             |
|   `d` or `i`   |                                                              Signed Decimal Integer                                                              |            `392`           |
|       `u`      |                                                             Unsigned Decimal Integer                                                             |           `7235`           |
|       `o`      |                                                              Unsigned Octal Integer                                                              |            `610`           |
|   `x` or `X`   |                                               Unsigned Hexadecimal Integer (`X`: uppercase variant)                                              |       `7fa` or `7FA`       |
|   `f` or `F`   |                              Decimal Floating Point (`F`: uppercase variant for special numbers eg. `nan` vs `NAN`)                              |          `392.65`          |
|   `e` or `E`   |                                       Scientific Notation (mantissa and exponent) (`E`: uppercase variant)                                       | `3.9265e+2` or `3.9265E+2` |
|   `g` or `G`   |                                   Use the shortest representation: `%e` or `%f` (`G`: uses uppercase variants)                                   |       `7fa` or `7Fa`       |
|   `a` or `A`   |                                                Hexadecimal Floating Point (`A`: uppercase variant)                                               |       `7fa` or `7Fa`       |
|       `c`      |                                                                     Character                                                                    |             `a`            |
|       `s`      |                                                                      String                                                                      |          `example`         |
|       `p`      |                                                                  Pointer Address                                                                 |      `0x7ffce531691c`      |
|       `n`      | Prints nothing. The argument corresponding to this specifier must be pointer to a signed integer. Stores the number of character written so far. |                            |                          |
|     `[set]`    |Matches non-.empty sequence of characters from the given set. If preceded by ^, then characters not in set are matched.                           |`scanf(%s[A-Z,_,a,b,c]s,str)`|                            |         


#### Width

|   Width  |                                                                                              Description                                                                                             |
|:--------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| _number_ | Minimum number of characters to be printed. If the value to be printed is shorter than this number, the result is padded with blank spaces. The value is not truncated even if the result is larger. |
|    `*`   |                                          The **width** is not specified in the **format** string, but taken from the next variadic argument from `printf()`.                                         |


#### Length

<table>
<thead>
  <tr>
    <th></th>
    <th colspan="7">Type Specifier</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Length Modifier</td>
    <td><code>d</code>, <code>i</code></td>
    <td><code>u</code>, <code>o</code>, <code>x</code>, <code>X</code></td>
    <td><code>f</code>, <code>F</code>, <code>e</code>, <code>E</code>, <code>g</code>, <code>G</code>, <code>a</code>, <code>A</code></td>
    <td><code>c</code></td>
    <td><code>s</code></td>
    <td><code>p</code></td>
    <td><code>n</code></td>
  </tr>
  <tr>
    <td>(none)</td>
    <td><code>int</code></td>
    <td><code>unsigned int</code></td>
    <td><code>double</code></td>
    <td><code>int</code></td>
    <td><code>char*</code></td>
    <td><code>void*</code></td>
    <td><code>int*</code></td>
  </tr>
  <tr>
    <td><code>hh</code></td>
    <td><code>signed char</code></td>
    <td><code>unsigned char</code></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><code>signed char*</code></td>
  </tr>
  <tr>
    <td><code>h</code></td>
    <td><code>short int</code></td>
    <td><code>unsigned short int</code></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><code>short int*</code></td>
  </tr>
  <tr>
    <td><code>l</code></td>
    <td><code>long int</code></td>
    <td><code>unsigned long int</code></td>
    <td></td>
    <td><code>wint_t</code></td>
    <td><code>wchar_t*</code></td>
    <td></td>
    <td><code>long int*</code></td>
  </tr>
  <tr>
    <td><code>ll</code></td>
    <td><code>long long int</code></td>
    <td><code>unsigned long long int</code></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><code>long long int*</code></td>
  </tr>
  <tr>
    <td><code>j</code></td>
    <td><code>intmax_t</code></td>
    <td><code>uintmax_t</code></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><code>intmax_t</code></td>
  </tr>
  <tr>
    <td><code>z</code></td>
    <td><code>size_t</code></td>
    <td><code>size_t</code></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><code>size_t</code></td>
  </tr>
  <tr>
    <td><code>t</code></td>
    <td><code>ptrdiff_t</code></td>
    <td><code>ptrdiff_t</code></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td><code>ptrdiff_t</code></td>
  </tr>
  <tr>
    <td><code>L</code></td>
    <td></td>
    <td></td>
    <td><code>long double</code></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</tbody>
</table>
