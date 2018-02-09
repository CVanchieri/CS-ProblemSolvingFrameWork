Instructions and pitfalls in getting your C compiler installed.

* [General Build Instructions](#general-build-instructions)
* [macos](#macos)
* [Windows](#windows)
* [Linux/Unix-likes](#linux-unix-likes)

## General Build Instructions

To build your C program from the command line (Bash shell or Terminal):

```
gcc -Wall -Wextra -o hello hello.c
```

## General Pitfalls

* If you accidentally tell `gcc` to overwrite your `.c` file with the `-o` (output) flag, you'll get errors. And your source code will be overwritten!

    ```
    # WRONG!!
    gcc -Wall -Wextra -o foo.c foo

    # RIGHT!!
    gcc -Wall -Wextra -o foo foo.c
    ```

* If you're on Windows and get errors about `WinMain`, make sure you have a `main()` function in your code! There are also other reasons you might see this error. Read on, below.

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

The two options for Windows that we know of for building the Unix-like code we play with at Lambda School are WSL and Cygwin. MinGW is too minimalist for our use.

### WSL

The [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/about) is an officially-supported binary compatibility layer for Linux apps running on Windows.

This basically gives you a mini Linux install. Ubuntu is recommended, but not required.

Requires Windows 10.

* [Install WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10)
  * [Check your build number](https://docs.microsoft.com/en-us/windows/wsl/troubleshooting#check-your-build-number). If it is pre-16215, you'll need to turn on developer mode, as per the above instructions.
* Run bash from the command prompt or start menu.
* Run `sudo apt install build-essential` to install GCC.

#### Drive Access

* To get to your Windows drive from Bash, type:
  ```
  cd /mnt/c/Users/YourUserName
  ```
* There is no supported way to access your WSL drive from Windows command prompt. _[Don't do it](https://blogs.msdn.microsoft.com/commandline/2016/11/17/do-not-change-linux-files-using-windows-apps-and-tools/)_.

#### VSCode and WSL

* Keep your program files on your Windows drive.
* Run VSCode as normal.
* You can bring up a bash shell then switch to your Windows drive, as outlined above. Then run `gcc` or whatever you need to.
* Unrelated to C programming, VSCode has some integrated WSL support for running the node debugger. See [launching WSL node from the VSCode debugger](https://code.visualstudio.com/updates/v1_17#_first-steps-towards-wsl-support).

### Cygwin

[Cygwin](https://cygwin.com/) is a library compatibility layer for building and running Linux apps.

* [Install Cygwin](https://cygwin.com/install.html).
* Launch a _Windows_ command prompt.
* Install the necessary packages by running the Cygwin Setup utility.
  ```
  setup-x86_64.exe -q -P wget -P gcc-g++ -P make -P diffutils -P libmpfr-devel -P libgmp-devel -P libmpc-devel
  ```
* Launch Cygwin-Terminal from its icon.

#### Drive Access

* To get to your Windows drive from Bash, type:
  ```
  cd /cygdrive/c/Users/YourUserName
  ```
  or 
  ```
  cd c:/Users/YourUserName
  ```

* To get to your Cygwin drive from Windows command prompt, type:
  ```
  cd c:\cygwin\home\youruser
  ```

#### VSCode and Cygwin

* Keep your files either on your Windows drive or Cygwin drive. Access them as per above.
* Run VSCode as normal.
* Run `gcc` from the Cygwin Terminal bash shell.

#### Cygwin Pitfalls

* If you have MinGW also installed, make sure that the Cygwin binaries are first in your `PATH`. If not, it will run the wrong GCC on the command line and you'll receive an error about `WinMain` not being found. Uninstall MinGW, per below.

* Another way to get an error about `WinMain` not being found is if you accidentally specify your source `.c` program as the _output_ file with `-o`. See [General Pitfalls](#general-pitfalls), above.

### MinGW

[MinGW does not support `fork()`, so will not work for LS classes](http://www.mingw.org/node/21).

Having a MinGW install can interfere with the workings of Cygwin. You might get errors related to an undefined `WinMain`. Here are [instructions for uninstalling MinGW](https://stackoverflow.com/questions/15741692/how-to-uninstall-mingw-and-make-cygwin-make-as-deafult-make-program-with-gcc-3).

## Linux/Unix-likes

Google for specific instructions using your distribution name, e.g. `ubuntu gcc install`.
