# How to Install Pyenv on Ubuntu 18.04

[ref](https://www.liquidweb.com/kb/how-to-install-pyenv-on-ubuntu-18-04/)

## Step #1: Update and Install Dependencies
It’s always a good idea to start off any installation process by updating system packages:

```
root@ubuntu:~#
    sudo apt update -y
```

Once that has finished up, run the following command to install all of pyenv’s dependencies:

```
root@ubuntu:~#
    sudo apt install -y make build-essential libssl-dev zlib1g-dev \
    libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev\
    libncursesw5-dev xz-utils tk-dev libffi-dev liblzma-dev python-openssl\
    git
```


## Step #2: Clone the Repository
To install the latest version of pyenv and provide a straightforward method for updating it, run the following command to pull it down from GitHub:

```
    git clone https://github.com/pyenv/pyenv.git ~/.pyenv
```


## Step #3: Configure the Environment
Next, to properly configure pyenv for use on the system, run the following block of commands to set some important environment variables and setup pyenv autocompletion:
```
    echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
    echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
    echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n eval "$(pyenv init -)"\nfi' >> ~/.bashrc
```
Finally, to start using pyenv, restart the shell by running:
```
root@ubuntu:~# 
    exec "$SHELL"
```


## Step #4: Verify the Installation
To verify that pyenv is installed correctly, we will try installing a new version of Python. First, we will list the available versions of Python:

```
root@ubuntu:~#
    pyenv install --list
```

The list of the available version is long. Let’s go ahead and install Python version 3.8.3:

```
root@ubuntu:~#
    pyenv install 3.8.3
```

Downloading Python-3.8.3.tar.xz...
-> https://www.python.org/ftp/python/3.8.3/Python-3.8.3.tar.xz
Installing Python-3.8.3...
Installed Python-3.8.3 to /root/.pyenv/versions/3.8.3
Do not be surprised if it takes a while for this command to run. Pyenv is building this version of Python from source.

To verify that Python 3.8.3 is now installed run the pyenv versions command:

```
root@ubuntu:~# 
    pyenv versions
    * system (set by /root/.pyenv/version)
    3.8.3
```

Now for further verification, change the version of Python to 3.8.3 and drop into a python shell.
```
root@ubuntu:~#
    pyenv global 3.8.3

root@ubuntu:~#
    python

Python 3.8.3 (default, Jun 10 2020, 22:45:23)
[GCC 7.5.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>>
```
Switching back is just as easy!

## Useful Commands
Finally, to get an idea of all the commands and features pyenv has to offer, run the following command:

```
root@ubuntu:~# 
    pyenv help
    Usage: pyenv <command> [<args>]
```

Some useful pyenv commands are as follows.

- `--version` :: Display the version of pyenvcommands List all available pyenv commands
- `exec` :: Run an executable with the selected Python version
- `global` :: Set or show the global Python version(s)
- `help` :: Display help for a command
- `hooks` :: List hook scripts for a given pyenv command
- `init` :: Configure the shell environment for pyenv
- `install` :: Install a Python version using python-build
- `local` :: Set or show the local application-specific Python version(s)
- `prefix` :: Display prefix for a Python version
- `rehash` :: Rehash pyenv shims (run this after installing executables)
- `root` :: Display the root directory where versions and shims are kept
- `shell` :: Set or show the shell-specific Python version
- `shims` :: List existing pyenv shims
- `uninstall` :: Uninstall a specific Python version
- `version` :: Show the current Python version(s) and its origin
- `version`-file :: Detect the file that sets the current pyenv version
- `version`-name :: Show the current Python version
- `version`-origin ::Explain how the current Python version is set
- `versions` ::List all Python versions available to pyenv
- `whence` ::List all Python versions that contain the given executable
- `which` ::Display the full path to an executable
- See the `pyenv help <command>` for information on a specific command.


The full documentation for pyenv can be found at GitHub.

There you have it! With pyenv installed, you’re off and running with more granular control of your Python environment!
