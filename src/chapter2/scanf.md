# Scanf()
In C programming language, scanf is a function that stands for Scan Formatted String. It is used to read data from stdin (standard input stream i.e. usually keyboard) and then writes the result into the given arguments.

It accepts character, string, and numeric data from the user using standard input.
scanf also uses format specifiers like printf.
## scanf Syntax
The syntax of scanf() in C is similar to the syntax of printf().

int scanf( const char *format, ... );
Here,

int is the return type.
format is a string that contains the format specifiers(s).
“…” indicates that the function accepts a variable number of arguments.
## Example format specifiers recognized by scanf:

%d to accept input of integers.

%ld to  accept input of long integers

%lld to accept input of long long integers

%f to accept input of real number.

%c to accept input of character types.

%s to accept input of a string.

To know more about format specifiers, refer to this article – Format Specifiers in C

## Example:

int var;
scanf(“%d”, &var);

The scanf will write the value input by the user into the integer variable var.

Return Value of scanf
The scanf in C returns three types of values:

 1)>0: The number of values converted and assigned successfully.<br>
 2)0: No value was assigned.<br>
 3)<0: Read error encountered or end-of-file(EOF) reached before any assignment was made.<br>

Why &?
While scanning the input, scanf needs to store that input data somewhere. To store this input data, scanf needs to known the memory location of a variable. And here comes the ampersand to rescue.

& is also called as address of the operator.
For example, &var is the address of var.
## Example of scanf
Below is the C program to implement scanf:


// C program to implement
// scanf
#include <stdio.h>

int main()
{
    int a, b, c;
    printf("Enter the first value:");
    scanf("%d", &a);
    printf("Enter the second value:");
    scanf("%d", &b);
    c = a + b;
    printf("%d + %d = %d\n", a, b, c);
    return 0;
}

//Output:
Enter the first value:58
Enter the second value:12
58 + 12 = 70


...Program finished with exit code 0

