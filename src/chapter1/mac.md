# Mac Setup

For your training you will need a few tools. Namely:

- Homebrew
- Xcode
- Git
- C compiler toolchain (GCC)
- A text editor (VSCode)

## Installing Homebrew

Homebrew is a package manager for MacOS. It offers thousands of developer libraries that would be difficult to obtain on the Mac platform. To install open the Terminal app and run the following command:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

[Homebrew](https://brew.sh/)

## Installing Xcode

Next we will need Xcode, Apple's compiler toolchain. Open the App Store and search for 'xcode' and press install.

## Installing Git

Git may already be installed with your copy of Xcode. To check run the following in the Terminal:

```sh
git --version
```

If it prompts you to install Git, follow the install wizard keeping the default options.

## Installing GCC

To install the GCC compiler, we'll use the Homebrew program we installed before.

```sh
brew install gcc-12
```

## VSCode Installation and Setup

Now that Homebrew, Xcode and GCC are installed and setup we will want to setup a text editor so we can easily edit and build our programs. For your training, I recommend using VSCode as it allows you to customize you developer environment to your needs. If you prefer another editor such as Neovim, feel free to use them as you please.

First download VSCode for Mac [VSCode Download](https://code.visualstudio.com/download)

Once installed, open the app and navigate to the extensions tab (icon on the left size made of four boxes). Using the search bar, install the following extensions.

- C/C++
- GitLens
- Git Graph
- GitHub Pull Requests and Issues
- Sonarlint

And thats it, you are all setup.
