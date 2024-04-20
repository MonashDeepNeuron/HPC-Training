# Windows Setup

For your training you will need a few tools. Namely:

- Git
- C compiler toolchain (MSVC)
- A text editor (VSCode)

## Installing Git

First, you will need to install Git. This allows you to use Git from the terminal and also gives you access to a bash shell environment. While following the install wizard, make sure to select the option that adds Git to your `PATH`. This important as it allows you to use Git in 'PowerShell'. Keep the other default operations. Git may require you to restart you machine.

[Git Download](https://git-scm.com/downloads)

### Connect GitHub

Once Git has installed, open a new 'Git Bash' that was installed. This can be found in the Windows 'Start' menu. Once it is open, run the following commands, replacing the username and email section with your details (keeping the quotation marks).

```sh
git config --global user.name "<github-username>"
git config --global user.email "<github-email>"
```

## Installing MSVC

Next we will need to install a C compiler toolchain. There a many different environments such as CygWin, MinGW but the most ideal environment is Microsoft's official development environment, MSVC. Download the Community Edition of Visual Studio and launch the installer. Under the 'Workloads' tab of the installer select the 'C++ Build Tools' bundle and click install. This may take a while. Once installed (may require restart) open the 'Start' menu and navigate to the 'Visual Studio' folder. There should a variety of different terminal environment applications. This is because Windows has slightly different toolchains and environments for x86 (32-bit) and x86_64 (64-bit). Select the 'Developer Command Prompt for VS 2022' app. In the terminal that spawns, run the command.

```cmd
cl
```

This will display the help options for `cl`, Window's C compiler.

[Download MSVC](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)

## VSCode Installation and Setup

Now that MingW and GCC are installed and setup we will want to setup a text editor so we can easily edit and build our programs. For your training, I recommend using VSCode as it allows you to customize you developer environment to your needs. If you prefer another editor such as Neovim, feel free to use them as you please.

First download VSCode for Windows [VSCode Download](https://code.visualstudio.com/download)

Once installed, open the app and navigate to the extensions tab (icon on the left size made of four boxes). Using the search bar, install the following extensions.

- C/C++
- GitLens
- Git Graph
- GitHub Pull Requests and Issues
- Sonarlint

And thats it, you are all setup.
