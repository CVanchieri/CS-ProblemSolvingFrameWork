We'll want to install Python 3 (version 3.x). Additionally, we'll be using the pipenv virtual environment manager.

## Note for Anaconda users

Unfortunately, we haven't found a way to get Anaconda to play nicely with pipenv. If you get them working together, please let your instructor know how you did it.

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
pipenv, version 11.10.1
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

### Option A: WSL

If you're running Windows 10+, you might want to install [WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10) with Ubuntu.

Some people install WSL, anyway, for the C portion of the CS curriculum.

Install Python 3 in WSL:

```
sudo apt install python3
```
Install pipenv:
```
pip install pipenv
```

### Option B: Chocolatey

[Install Chocolatey](https://chocolatey.org/install)

[Install Python 3 with Chocolatey](https://chocolatey.org/packages/python3)

[Install pipenv per these instructions](http://docs.python-guide.org/en/latest/dev/virtualenvs/#virtualenvironments-ref)

### Option C: Native

[Install Python 3](https://www.python.org/downloads/windows/)

[Install pipenv per these instructions](http://docs.python-guide.org/en/latest/dev/virtualenvs/#virtualenvironments-ref)

## Linux
Consult the documentation for your distribution.