# Compilation

C is a compiled language. This means that all the source code is compiled to machine code before the application is run. This means that the compiler needs to know a lot about a program before it can run. Compilation is the process of combining source files into a single binary and because C is a structured language, the order in which files are compiled is important. C also sometimes requires files to be linked together. This occurs when two source files depend on a common library source file.

## Header & Source Files

In C there are two kinds of files that are used. Source files and header files. These must be combined appropriately by the compiler in order to produce a working executable.

### Header File

Headers are declaration files. They define and state that certain symbols (functions, types etc.) exist such that other headers and source files can use them without knowing there full definition (how they work) yet. Within a header, you define what is called the signature of a function or type. This allows the C type system to validate the uses of the symbol before it even compiles the symbol. Headers in C use the `*.h` file extension.

### Source Files

Source files are the core of any language. They hold the definition of every symbol defined in a codebase. Source files for C use the `*.c` file extension. Source files are what actually get compiled binary machine code. Source files are often compiled into object files first and then linked together using a linker when they depend on each other or external libraries.

## Compiling & Linking

There are four main steps in the compilation pipeline for C programs.

1. Pre-process - The Preprocessor is invoked, which includes headers in source files and expands macros. Comments are also stripped at this step. The step creates the Translation Unit (TU) for a source file.
2. Compilation - The TU's for each source file is then compiled individually into assembly code. During this step the Abstract Syntax Tree is created for the program and is lower to an Higher Intermediate Representation (HIR). Generally this is created in assembly language of the target platform/CPU.
3. Assembly - This step involves lowering the HIR once again into an Intermediate Representation (IR) ie. it assembles the assembly code into an binary object file.
4. Linking - This is the final step. Once objects files are created for each TU, we can link them together as well as link any external libraries to form an executable (or binary library file). Linking provides information to an executable about to file the definition of symbols at runtime so that functions will actually execute the correct code. Before this step, the object files just new that certain symbols existed but not where to find them.
