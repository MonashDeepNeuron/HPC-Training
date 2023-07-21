# Scanf

scanf() is a function in the C programming language that stands for "Scan Formatted String." It is part of the standard input/output library (stdio.h) and is used to read data from the standard input stream (usually the keyboard) and store it into specified variables based on format specifiers.

The general syntax of scanf() is:


int scanf(const char *format, ...);
Here's a brief explanation of the parameters:

format: A string that contains format specifiers to specify the types of data to be read from the input. The format specifiers are preceded by a percent sign %. For example, %d is used to read an integer, %f for a floating-point number, %c for a character, %s for a string, etc.

...: The ellipsis ... indicates that scanf() can accept a variable number of arguments. This means you can pass multiple variables to scanf() to store the data read from the input.

To use scanf(), you need to pass the address of the variables where the input data should be stored. This is achieved by using the address-of operator & before the variable name. For example, if you want to read an integer and store it in the variable num, you would write scanf("%d", &num);.

## Example format specifiers recognized by scanf:

%d to accept input of integers.

%ld to  accept input of long integersgi

%lld to accept input of long long integers

%f to accept input of real number.

%c to accept input of character types.

%s to accept input of a string.



Return Value of scanf
The scanf in C returns three types of values:

 1)>0: The number of values converted and assigned successfully.<br>
 2)0: No value was assigned.<br>
 3)<0: Read error encountered or end-of-file(EOF) reached before any assignment was made.<br>

Why &?
While scanning the input, scanf needs to store that input data somewhere. To store this input data, scanf needs to known the memory location of a variable. And here comes the ampersand to rescue.

& is also called as address of the operator.
For example, &var is the address of var.

Here's a simple example to illustrate how scanf() works:


#include <stdio.h>

int main() {
    int age;
    char name[50];

    printf("Enter your name: ");
    scanf("%s", name);

    printf("Enter your age: ");
    scanf("%d", &age);

    printf("Hello, %s! You are %d years old.\n", name, age);
    return 0;
}
In this example, the program prompts the user to enter their name and age. The data is read using scanf() with appropriate format specifiers, and then the information is displayed using printf(). Remember that scanf() stops reading as soon as it encounters whitespace characters, so it's not suitable for reading strings with spaces.