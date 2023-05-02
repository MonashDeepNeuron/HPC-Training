# Software and Tooling

Software and development tooling is handled a little differently on M3 than you might be used to. In particular, because M3 is a shared file system, you do not have access to `sudo`, and you cannot install software on the system manually. Instead, you will need to use the `module` command to load software and development tools.

## Module

The `module` command is used kind of as an alternative to package managers like `apt` or `yum`, except it is managed by the M3 team. It allows you to load software and development tools into your environment, and is used to load software on M3. To see a comprehensive list of commands go [here](./linux-cmds.md#m3-specific-commands).

In general, however, you will only really need to use `module load` and `module unload`. These commands are used to load and unload software and development tools into your environment.

For most of the more popular software packages, like gcc, there are multiple different versions available. You will need to specify which version you want to load based on your needs.

## C

### GCC

To load GCC, you can run the following command:

```bash
module load gcc/10.2.0
```

This will load GCC 10.2.0 into your environment, and you can use it to compile C/C++ programs as described in the [Intro to C](../chapter2/intro-to-c.md) chapter. To unload GCC, you can run the following command:

```bash
module unload gcc/10.2.0
```

## Python

Python is a bit of a special case on M3. This is because of how many different versions there are, as well as how many different packages are available. To make things easier, it is recommended that you use miniconda or anaconda to manage your python environments instead of using the system python.

These instructions are based off the M3 docs, which can be found [here](https://docs.massive.org.au/M3/software/pythonandconda/pythonandconda.html#pythonandconda).

### Miniconda

#### Installing Miniconda

To install Miniconda on M3, there is a dedicated install script that you can use. This will install miniconda into your default scratch space, i.e. `/vf38_scratch/<username>/miniconda3`. To install miniconda, run the following command:

```bash
module load conda-install

# To install miniconda to the default location 
conda-install

# To install miniconda to a custom location
conda-install your/install/location
```

#### Activating Miniconda

To activate the base conda environment, run the following command:

```bash
source your/install/location/miniconda/bin/activate
```

You will notice that once activated, `(base)` will appear in the prompt before your username.

To create and activate Python environments within Miniconda, follow these steps:

```bash
# Create a new environment
# Change env-name to whatever you want to call your environment
conda create --name env-name python=<version>

# Activate the environment
conda activate env-name
```

#### Managing Python packages

Use the following commands to install and manage Python packages:

```bash
# Install a package
conda install package-name

# Update a package
conda update package-name

# You can also change the version of packages by adding a = and the version number

# Remove a package
conda remove package-name
```

#### Deactivating Miniconda

To deactivate the conda environment you are in, run `conda deactivate`. To exit conda entirely run `conda deactivate` again. You will know you have fully exited conda when `(base)` is no longer in the prompt.

### VIM

VIM is a terminal based text editor. You may have heard about it, or even tried using it before. If so, you might recognise the common meme of "how do I exit VIM???". This is because VIM uses a very different key binding system to other text editors, and it can be a little confusing to get used to. However, once you get used to it, it is actually a very powerful and efficient text editor.

I will attemt to give a brief overview of VIM commands, however you should really check out the [VIM documentation](https://vimhelp.org/) if you want to learn more.

VIM also has a built in tutorial that you can access by running `:help` while in VIM.

To use VIM to edit a file, just type `vim <filename>` into the terminal. This will open the file in VIM. If the file does not exist, it will create a new file with that name.

VIM has three different modes. The first is the command mode, which is the default mode when you open a file. In this mode, you can navigate around the file, and perform other commands. The second is the insert mode, which is used to insert text into the file. The third is the visual mode, which is used to select text.

To enter the insert mode, press `i`. To exit the insert mode, press `esc`. To enter the visual mode, press `v`. To exit the visual mode, press `esc`.

In command mode, you move around using `h`, `j`, `k`, `l`. To move along words, press `w` or `b`. To move to the start or end of the line, press `0` or `$`. You can delete a line using `dd`, or delete a word using `dw`. You might be noticing some patterns here. In VIM, commands are made up of single or multiple characters that represent different things. For example, if I wanted to delete a word, I would press `d` to delete, and then `w` to delete a word. If I wanted to delete 3 words, I would press `d3w`. If I just wanted to change a word, I would press `c` instead of `d`. If I wanted to change 3 words, I would press `c3w`. If I wanted to change a line, I would press `cc`. Some other useful command mode commands are `u` to undo, `o` to insert a new line and go into insert mode, and `?` to search for a string.

To get to insert mode, there are a lots of different ways, but the most common are `i` to insert text before the cursor, `a` to insert text after the cursor, and `o` to insert a new line. The capital versions of these also do things. `I` inserts text at the start of the line, `A` inserts text at the end of the line, and `O` inserts a new line above the current line. To exit insert mode, press `esc`.

To get to visual mode, press `v`. In visual mode, you can select text using the same commands as in command mode. To delete the selected text, press `d`. To change the selected text, press `c`. To copy the selected text, press `y`. To paste press `p`. To exit visual mode, press `esc`.

To exit VIM itself, enter command mode, and then press `:q!`. This will exit VIM without saving any changes. To save and exit, press `:wq`. To save without exiting, press `:w`.
