# Hello World

If you have ever programmed before you may be familiar with 'Hello World'. If not, a 'Hello World' program is often the first program you write in a programming language. It serves a brief introduction to the languages syntax, a simple workflow in that language and also as a sanity check to ensure the developer tools for the project were installed and setup correctly.

> **Fun Fact:**
>
> The 'Hello World' test program was popularized by Brian Kernighan's _Programming in C: A Tutorial_.

## Setup

To begin open a new terminal window. If you don't already have a development directory it is a good idea to create one. This should be where you host all your projects. 

```sh
# Optional
mkdir dev
cd dev
```

In this directory (or another of your choosing) we are going to create a directory for our 'Hello World' project. Finally, we'll open VSCode in this location so that we can easily edit our code.

```sh
mkdir hello
cd hello
code . 
```

> **Note:**
>
> Windows users will have to use the Developer Command Prompt used in the Windows section of the last chapter. You will then need to navigate to a different directory. Ideally use your 'Home' directory.
>
> ```cmd
> cd C:\Users\<username>
> ```
>
> You should be able to follow the instructions above normally.

## Compiling and Running

'Hello World' in C is quite simple, although not as simple as say Python. First create a new file called `main.c`.

```c
#include <stdio.h>

int main()
{
    puts("Hello World\n");
    return 0;
}
```

To compile and run the program simply run the commands below. The output will be an executable called `main` (`main.exe` on Windows) located in the same directory as the source file.

### Linux, MacOS & WSL

```sh
gcc -o main main.c
./main
Hello World
```

### Windows

```sh
cl main.c
main.exe

# ...

Hello World
```

## What's Going On Here?

Let's break down the 'Hello World' program a bit to see what is going on.

```c
#include <stdio.h>
```

On the first line we have we have included a library. This is the Standard IO library. Libraries come in the form of one or more headers, denoted by the `*.h` file extension. More on headers in the next section. The `#include` is called a preprocessor directive. It is resolved at compile time meaning it does not exist at runtime. Here `#include` will copy (yes, literally copy) the entire contents of the file specified. In this case, it is the file `stdio.h`. This means that the symbols from this header are now available in our program.

```c
int main()
{
    /// ...

    return 0;
}
```

`main()` is a function. Functions are subroutines that allow us to run a piece of code many time without repeating it everywhere we need it. In C, the `main()` function has a special meaning, it is the entry point of the application. After some initial setup from the OS, this is first section of the application to run. Here `main()` takes no arguments however, sometimes it will take two special arguments which are used to communicate information from the outside world to the program at the point of execution. Here, we indicate `main()` returns an `int`. The return value is used by the OS to handle specific errors that may occur. A return value of `0` from main indicate success with any non-zero value indicating an error.

```c
puts("Hello World!");
```

`puts()` is another function. It was obtained from the `stdio` library we included before. `puts()` means 'put string'. It takes a null-terminating string as input and returns the op-code indicating success or failure. As a side effect,`puts()` writes the string to the `stdout` file-stream ie. outputs the string to the terminal and appends a newline character at the end. Both the call to `puts()` and `return` end in a semicolon. This indicates the end of the line/expression and is required for almost every line of C.
