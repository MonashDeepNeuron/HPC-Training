# Mac Setup

For your training you will need a few tools. Namely:

- Xcode
- Git
- C compiler toolchain (GCC)
- A text editor (VSCode)

## Installing Xcode, Git & GCC

First, we will need Xcode command line tool utilities, to do so, open the 'Terminal' app and run the following command:

```sh
xcode-select --install
```

This will prompt you to accept the install and will download Git and GCC onto your device. To verify installation was successful, run:

```sh
$ xcode-select -p

# Should print this
/Library/Developer/CommandLineTools
```

> **Note:**
>
> Here, `$` indicates the prompt of the terminal. Do not include it in the command. This may be a different symbol on your device.

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
