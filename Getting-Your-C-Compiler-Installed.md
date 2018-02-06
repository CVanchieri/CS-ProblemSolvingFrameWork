Instructions and pitfalls in getting your C compiler installed.

* [General Build Instructions](#general-build-instructions)
* [macos](#macos)
* [Windows](#windows)
* [Linux/Unix-likes](#linux-unix-likes)

## General Build Instructions

To build your C program from the command line (Bash shell or Terminal):

```
gcc -Wall -Wextra -o myprog myprog.c
```

## macos

### Option A: Command Line Tools

* Open a Terminal.
* Run `xcode-select --install`.
* When prompted to install the developer command line tools, click `Install`.

### Option B: Full XCode install

If you're going to install XCode anyway for some other reason, you can use these instructions:

* Install _XCode_ from the AppStore.
* Open a Terminal.
* Run `gcc`.
* When prompted to install the developer command line tools, click `Install`.

## Windows

The two options for 
### WSL

The [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/about) is an officially-supported binary compatibility layer for Linux apps running on Windows.

This basically gives you a mini Linux install. Ubuntu is recommended, but not required.

Requires Windows 10.

* [Install WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
* Run bash from the command prompt or start menu.
* Run `sudo apt install build-essential` to install GCC.

### Cygwin

[Cygwin](https://cygwin.com/) is a library compatibility layer for building and running Linux apps.

* [Install Cygwin](https://cygwin.com/install.html).
* Launch a _Windows_ command prompt.
* Install the necessary packages by running the Cygwin Setup utility.
  ```
  setup-x86_64.exe -q -P wget -P gcc-g++ -P make -P diffutils -P libmpfr-devel -P libgmp-devel -P libmpc-devel
  ```
* Launch Cygwin-Terminal from its icon.

### MinGW

[MinGW does not support `fork()`, so will not work for LS classes](http://www.mingw.org/node/21).

## Linux/Unix-likes

Google for specific instructions using your distribution name, e.g. `ubuntu gcc install`.
