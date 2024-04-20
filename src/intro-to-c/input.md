# Input

We're now going to discuss how to take user input from the standard input (`stdin`) in C.

## `scanf`

`scanf()` allows you to read different data types from the user's input and store them in variables, making it a versatile function for interactive applications. It enables you to control the input format, extract data from the input stream, and store it in the appropriate variables.

### Signature

The general signature of `scanf()` is similar to `printf()`, it takes a format string indicating the format of the input sequence and a variadic list of addresses (pointers)where values are stores. `scanf()`'s format string uses a similar format specification to `printf()` however, the variable specifiers (denoted with `%`) indicate values that are to be read in and stored in program variables. As we are reading values in with `scanf()`, when we wish to store a variable we must pass the address of the variable we want to store the value in. This is because variables have copy semantics in C meaning we cannot pass a variable to a function and get the modified value with returning it or using a pointer. `scanf()` uses pointers.

```c
scanf(char* fmtstring, ...);
```

### Example

This simple program is similar to the `printf()` example we saw earlier in the book except, instead of hard coding values we are able to take input from the user in the form `x + y` and the program will return the result.

```c
#include <stdio.h>

int main()
{
    double a = 0.0;
    double b = 0.0;
    double sum = 0.0;

    printf(">> ")
    scanf("%f + %f", &a, &b);
    sum = a + b;
    printf("%f", sum);

    return 0;
}
```

### Formatting Specification

The format specification is a mirror to that used by `printf()` (there are many `_f()` functions in the C standard library that all use similar format specifications) as values being read in must conform to a given C type. This allows us to easily convert the incoming string data as `int`, `double` or even substrings.

The general format specification is as below:

`_%\[width\]\[.precision\]\[length\]type-specifier_`

There are a variety of different options for each part of the specification. Below is a series of tables breaking down the various options for each sub-specifier but note that only _type-specifier_ is needed, the others are optional.

#### Type Specifiers

| Type Specifier |                                                                                                                                                                                                                                                                                                  Type                                                                                                                                                                                                                                                                                                  |           Example          |
|:--------------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------------------------:|
|       `%`      |                                                                                                                                                                                                                                                                      Two sequential `%` will result in a single `%` being printed.                                                                                                                                                                                                                                                                     |             `%`            |
|   `d` or `i`   |                                                                                                                                                                                                                                                                                         Signed Decimal Integer                                                                                                                                                                                                                                                                                         |            `392`           |
|       `u`      |                                                                                                                                                                                                                                                                                        Unsigned Decimal Integer                                                                                                                                                                                                                                                                                        |           `7235`           |
|       `o`      |                                                                                                                                                                                                                                                                                         Unsigned Octal Integer                                                                                                                                                                                                                                                                                         |            `610`           |
|   `x` or `X`   |                                                                                                                                                                                                                                                                           Unsigned Hexadecimal Integer (X: uppercase variant)                                                                                                                                                                                                                                                                          |       `7fa` or `7FA`       |
|   `f` or `F`   |                                                                                                                                                                                                                                                          Decimal Floating Point (F: uppercase variant for special numbers eg. `nan` vs `NAN`)                                                                                                                                                                                                                                                          |          `392.65`          |
|   `e` or `E`   |                                                                                                                                                                                                                                                                   Scientific Notation (mantissa and exponent) (E: uppercase variant)                                                                                                                                                                                                                                                                   | `3.9265e+2` or `3.9265E+2` |
|   `g` or `G`   |                                                                                                                                                                                                                                                               Use the shortest representation: `%e` or `%f` (G: uses uppercase variants)                                                                                                                                                                                                                                                               |       `7fa` or `7Fa`       |
|   `a` or `A`   |                                                                                                                                                                                                                                                                            Hexadecimal Floating Point (A: uppercase variant)                                                                                                                                                                                                                                                                           |       `7fa` or `7Fa`       |
|       `c`      |                                                                                                                                                                                                                                                                                                Character                                                                                                                                                                                                                                                                                               |             `a`            |
|       `s`      |                                                                                                                                                                                                                                                                                                 String                                                                                                                                                                                                                                                                                                 |          `example`         |
|       `p`      |                                                                                                                                                                                                                                                                                             Pointer Address                                                                                                                                                                                                                                                                                            |      `0x7ffce531691c`      |
|       `n`      |                                                                                                                                                                                                                              Prints nothing. The argument corresponding to this specifier must be pointer to a signed integer. Stores the number of character read so far.                                                                                                                                                                                                                             |                            |
|     `[set]`    | Matches a non-empty sequence of character from set of characters. If the first character of the set is `^`, then all characters not in the set are matched. If the set begins with `]` or `^]` then the `]` character is also included into the set. It is implementation-defined whether the character - in the non-initial position in the scanset may be indicating a range, as in `[0-9]`. If a width specifier is used, matches only up to _width_. Always stores a null character in addition to the characters matched (so the argument array must have room for at least _width+1_ characters) |                            |
|       `*`      |                                                                                                                                                                                                                      Assignment-suppressing character. If this option is present, the function does not assign the result of the conversion to any receiving argument (optional).                                                                                                                                                                                                                      |                            |

#### Width

|   Width  |                                                                                              Description                                                                                             |
|:--------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| _number_ | Minimum number of characters to be printed. If the value to be printed is shorter than this number, the result is padded with blank spaces. The value is not truncated even if the result is larger. |

#### Precision

| .precision |                                                                                                                                                                                                                                                                                                                                                                                                             Description                                                                                                                                                                                                                                                                                                                                                                                                             |
|:----------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|  _.number_ | For integer specifiers (`d`, `i`, `o`, `u`, `x`, `X`): precision specifies the minimum number of digits to be read. If the value read is shorter than this number, the result is padded with leading zeros. The value is not truncated even if the result is longer. A precision of `0` means that no character is written for the value 0. For `a`, `A`, `e`, `E`, `f` and `F` specifiers: this is the number of digits to be printed after the decimal point (by default, this is 6). For g and G specifiers: This is the maximum number of significant digits to be printed. For `s`: this is the maximum number of characters to be printed. By default all characters are printed until the ending null character is encountered. If the period is specified without an explicit value for precision, `0` is assumed. |

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
