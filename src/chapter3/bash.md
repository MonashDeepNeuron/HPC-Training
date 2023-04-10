# Bash Scripts

Bash is both a command line interface and a scripting language. Bash scripts are a series of commands that are executed in order. Bash scripts are useful for automating tasks that you do often, or for running a series of commands that you don't want to type out every time. In our case, Bash scripts are used for running jobs on M3.

The basic syntax of a bash file is as follows:

```bash
#!/bin/bash

# This is a comment

echo "Hello World"
```

We can save this file as `hello.sh` and run it using the following command: `source hello.sh`. This will print `Hello World` to the terminal.

Let's walk through the file. The first line is `#!/bin/bash`. This is called a shebang, and it tells the system that this file is a bash script. The second line is a comment, and is ignored by the system. The third line is the actual command that we want to run. In this case, we are using the `echo` command to print `Hello World` to the terminal.

Bash can do a lot more, including basic arithmetic, if statements, loops, and functions, however these are not really necesary for what we are doing. If you want to learn more about bash, you can find a good tutorial [here](https://linuxconfig.org/bash-scripting-tutorial).

For our use, the main things we need to be able to do are to run executables and files. We do this the exact same way as if manually running them in the terminal. For example, if we want to run a python script, we can do the following:

```bash
#!/bin/bash

# This will run hello.py using the python3 executable
python3 hello.py
```

If we want to compile and then run a C program, we can do the following:

```bash
#!/bin/bash

# This will compile hello.c and then run it
gcc hello.c -o hello
./hello
```

Using bash scripts not only saves a lot of time and effort, but it also makes it easier to run jobs on M3 using SLURM. We will go over how to do this in the next section.
