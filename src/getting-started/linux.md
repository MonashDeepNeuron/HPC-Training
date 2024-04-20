# Linux Setup

For your training you will need a few tools. Namely:

- Git
- C compiler toolchain (GCC)
- A text editor (VSCode)

 For this section I will be assuming a Debian system, namely Ubuntu. Replace `apt` commands with your distributions relevant package manager.

## Installing Packages

To begin, you will need to install some packages. This will be done using `apt`, Ubuntu's system package manager. Run the commands in the shell.

```sh
# `sudo` represents 'super user do'.
 
# This runs a command with admin. privileges.
# Update apt's local package index.
sudo apt update

# The `-y` flag means upgrade yes to all.
# This bypasses confirming package upgrades.
# Upgrade packages with new versions
sudo apt upgrade -y

# Installs specified packages (separated by spaces).
sudo apt install git curl wget build-essential
```

And that's it. Linux is setup and installed.

## Connect Git & GitHub

Next we will link your GitHub account to you local Git install. Run the following commands, replacing the username and email section with your details (keeping the quotation marks).

```sh
git config --global user.name "<github-username>"
git config --global user.email "<github-email>"
```

## VSCode Installation and Setup

Now that GCC is installed and setup we will want to setup a text editor so we can easily edit and build our programs. For your training, I recommend using VSCode as it allows you to customize you developer environment to your needs. If you prefer another editor such as Vim, Emacs or Neovim, feel free to use them as you please.

First download VSCode for Linux [VSCode Download](https://code.visualstudio.com/download)

Once installed, open the app and navigate to the extensions tab (icon on the left size made of four boxes). Using the search bar, install the following extensions.

- C/C++
- GitLens
- Git Graph
- GitHub Pull Requests and Issues
- Sonarlint

And thats it, you are all setup.
