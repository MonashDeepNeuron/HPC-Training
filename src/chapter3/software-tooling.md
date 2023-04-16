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
conda create --name env-name python=3.10

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
