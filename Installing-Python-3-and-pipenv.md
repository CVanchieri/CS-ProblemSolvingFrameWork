We'll want to install Python 3 (version 3.x), which is the runtime for the language itself. The runtime is what allows you to execute Python code and files by typing `python [file_or_code_to_execute]` in your terminal. You can also open up a Python REPL (Read-Eval-Print Loop) to quickly and easily mess around with Python code once you've gotten the runtime installed. If you recall how Node let's you execute and run JavaScript code locally on your machine instead of having to rely on the browser, the Python runtime pretty much let's you do the same thing but with Python code. 

Additionally, we'll be using the pipenv virtual environment manager. Think of it as the `npm` of Python (though pipenv is also capable of performing a bunch of other tasks as well, most notably running your Python projects in an isolated virtual environment). 

## Note for Anaconda users

Unfortunately, we haven't found a way to get Anaconda to play nicely with pipenv. If you get them working together, please let your instructor know how you did it.

For now, you'll have to uninstall Anaconda from your machine. Look up how to do this for your particular Anaconda version and operating system. 

## Testing the Install

If you can run `python` or `python3` and see a 3.x version, and you can run `pipenv`, you're good to go.

```
$ python3 --version
Python 3.6.5
```
or on some systems, Python 3 is just `python`:

```
$ python --version
Python 3.6.5
```

And try `pipenv`:

```
$ pipenv --version
pipenv, version [some remotely recent date, probably]
```

Otherwise, keep reading. :)

## macOS

While macOS comes with Python 2, we need to get Python 3 in there as well.

If you don't have Brew installed, [follow the instructions on the brew website](https://brew.sh/).

Use Brew to install Python and pipenv at the Terminal prompt:

```
brew install python pipenv
```

## Windows

_**Note**:_ Git Bash doesn't seem to cooperate if you're trying to install Python on Windows. Try another terminal like Powershell. 

Recommend updating Windows to the latest version.

### Windows Store

Python 3 is in the Windows Store and can be installed from there.

### Official Binaries

When installing the official package, be sure to check the

```
[ ] Add to PATH
```

checkbox!!

[Official Package](https://www.python.org/downloads/windows/)

### Pipenv

This is what worked for Beej. YMMV.

1. Install Python, as per above.
2. Bring up a shell (cmd.exe or Powershell)
3. Run `py -m pip`
4. Run `py -m pip install --user pipenv`

   At this point, you should be able to always run pipenv with `py -m pipenv`, but that's a little inconvenient. Read on for making it easier.

5. You'll see a message like this in the pipenv install output, but with a slightly different path:
   ```
   add C:\Users\username\AppData\Roaming\Python\Python38\Scripts to your path
   ```
6. Select that path (not including any quotes around it), and copy it
7. Go to the Start menu, type "environment" and run the program `Edit Environment Variables`
8. In the System Properties popup, hit the `Advanced` tab, then `Environment Variables`
9. On the list of environment variables, doubleclick `Path`
10. Click `New`
11. Paste that path from step 5 into the new entry slot. Make sure there aren't any quotes around it.
12. Click `OK`, `OK`, `OK`.
13. Relaunch any shells you have open.
14. Now you should be able to just run `pip` and `pipenv` in Powershell without putting `py -m` in front of it.

#### Pipenv official instructions

[Install pipenv per these instructions](http://docs.python-guide.org/en/latest/dev/virtualenvs/#virtualenvironments-ref)

### Chocolatey

[Install Chocolatey](https://chocolatey.org/install)

[Install Python 3 with Chocolatey](https://chocolatey.org/packages/python3)

[Install pipenv per these instructions](http://docs.python-guide.org/en/latest/dev/virtualenvs/#virtualenvironments-ref)

### WSL

If you're running Windows 10+, you might want to install the Windows Subsystem for Linux. This gives you a mini, integrated Linux system inside Windows. You then install and use Python from there.

1. Update Windows to latest if you haven't already.
2. [Install WSL from here](https://docs.microsoft.com/en-us/windows/wsl/install-win10).
3. Go to the Microsoft store and install Ubuntu.
4. Run Ubuntu to get a bash shell.
5. Make a new username and password. This is completely separate from your Windows username and password, but I made mine the same so that I wouldn't forget.
6. Upgrade the Ubuntu system. Run:
   ```
   sudo apt-get update
   sudo apt-get upgrade
   ```
   Give your newly-entered password if prompted.
7. Running `python3 --version` should give you 3.6 or higher.
8. Run `pip install pipenv`.

If you've installed VS Code, add the "Remote WSL" extension. This way you can run `code` from within Ubuntu.

In the Ubuntu shell, you can run `explorer.exe .` in any directory to open a Windows Explorer window in that directory.

Also in Windows Explorer, you can put `\\wsl$` in the URL bar to see your Ubuntu drive. (If it doesn't show up, relaunch your Ubuntu shell.)

## Linux
Consult the documentation for your distribution.