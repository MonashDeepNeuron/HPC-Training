# Printing

We're going to briefly discuss how to print stuff to the terminal so you can start writing some C.

## `printf`

Earlier we saw the `puts()` function which prints strings to the terminal. This function is really good for strings but does not work for any other data type. Instead, there is the `printf()` function which prints formatted text to the terminal. This allows you to print different data types to the terminal and control various aspects of the output.

### Signature

The general signature of `printf()` is quite unique in C and how it achieves it is a bit of compiler magic in order to actually implement but you do not have to worry about it. `printf()` takes as its first argument a string that represents the output format of the printed text. The next argument is the `...`. This is called the ellipsis and it is used to represent a variable number of untyped function arguments. This allows you to pass ass many arguments as you want to `printf()` and it will print them all as long as there are an equivalent number of positional arguments in the format string. The variadic arguments are inserted in output string in the same order they are passed to `printf()` ie. there is now way to indicate in the format string which variadic argument to use at any given positional argument. The positional argument introducer character is the `%` followed by a modifier to indicate in incoming type.

```c
printf(char* fmtstring, ...);
```

> **Note:**
>
> - Ignore the use of `char*` for now.
> - `printf()` is different to `puts()` in that it doesn't pad the end if the output string with a newline so you will have to manually provide it. The newline character is `'\n'`. The backslash is a special character that indicates the proceeding character is "escaped". Escaped characters have special meanings for string and character data.
> If the format string doesn't have any positional arguments then `printf()` will just print the string like `puts()`.
> `printf()` is not able to print data of any kind without a format string ie. `printf(10)` would fail to compile.

### Example

The following simple code snippet creates to variables `num` and `dec` and computes their `sum`. It then prints a string according to the format `"%d + %f = %f"`, substituting `num`, `dec` and `sum` respectively.

```c
#include <stdio.h>

int main()
{
    int num     = 4;
    double dec  = 3.54756;
    double sum  = num + dec;

    printf("%d + %f = %f", num, dec, sum);

    return 0;
}
```

> Question: Notice how we used `double` for the type of `sum`. What would happen if `sum` type was `int`?

If you want to have a play with `printf()`, copy the following code snippet run it on your own device. The command line will output different varieties of 'Hello World!'.

```c
#include <stdio.h>

int main() {
    printf("%30s\n", "Hello World!"); // Padding added
    printf("%40s%10s%20s%15s\n", "Hell", "o", "World", "!"); 
    printf("%10.7s\n", "Hello World!"); // Print only the first 7 characters with padding
    printf("%100c%c%c%c%c %c%c%c%c%c%c%c\n", 
         72, 101, 108, 108, 111, 32, 87, 111, 114, 108, 100, 33, '\n'); // Hex values
    return 0;
}

```
### Formatting Specification

You'll notice we used a different character after the `%` for each argument. This is because `printf()` needs to know the type of the incoming arguments so that it can format the string appropriately. For example floating point types have to use a decimal point when transformed into a text format while integers do not.

C has a concise language for `printf()` format arguments with the general format for a positional argument specifier being:

`_%\[flag\]\[width\]\[.precision\]\[length\]type-specifier_`

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

#### Flags

|   Flag  |                                                                                                                                                               Description                                                                                                                                                              |
|:-------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|   `-`   |                                                                                                           Left-justify within the given field width; Right justification is the default (see [width](#width) sub-specifier).                                                                                                           |
|   `+`   |                                                                                        Forces to preceed the result with a plus or minus sign (+ or -) even for positive numbers. By default, only negative numbers are preceded with a - sign.                                                                                        |
| _space_ |                                                                                                                             If no sign is going to be written, a blank space is inserted before the value.                                                                                                                             |
|   `#`   | Used with `o`, `x` or `X` specifiers the value is preceded with `0`, `0x` or `0X` respectively for values different than zero. Used with `a`, `A`, `e`, `E`, `f`, `F`, `g` or `G` it forces the written output to contain a decimal point even if no more digits follow. By default, if no digits follow, no decimal point is written. |
|   `0`   |                                                                                                         Left-pads the number with zeroes (`0`) instead of spaces when padding is specified (see [width](#width) sub-specifier).                                                                                                        |

#### Width

|   Width  |                                                                                              Description                                                                                             |
|:--------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| _number_ | Minimum number of characters to be printed. If the value to be printed is shorter than this number, the result is padded with blank spaces. The value is not truncated even if the result is larger. |
|    `*`   |                                          The **width** is not specified in the **format** string, but taken from the next variadic argument from `printf()`.                                         |

#### Precision

| .precision |                                                                                                                                                                                                                                                                                                                                                                                                             Description                                                                                                                                                                                                                                                                                                                                                                                                             |
|:----------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|  _.number_ | For integer specifiers (`d`, `i`, `o`, `u`, `x`, `X`): precision specifies the minimum number of digits to be written. If the value to written is shorter than this number, the result is padded with leading zeros. The value is not truncated even if the result is longer. A precision of `0` means that no character is written for the value 0. For `a`, `A`, `e`, `E`, `f` and `F` specifiers: this is the number of digits to be printed after the decimal point (by default, this is 6). For g and G specifiers: This is the maximum number of significant digits to be printed. For `s`: this is the maximum number of characters to be printed. By default all characters are printed until the ending null character is encountered. If the period is specified without an explicit value for precision, `0` is assumed. |
|    `.*`    |                                                                                                                                                                                                                                                                                                                                                        The **precision** is not specified in the **format** string, but taken from the next variadic argument from printf().                                                                                                                                                                                                                                                                                                                                                        |

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
