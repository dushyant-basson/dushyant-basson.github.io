---
author: "Dushyant Basson"
categories:
- uncategorized
date: "2024-07-14"
slug: "set-a-particular-python-version-for-a-directory"
tags:
- python
title: "Set a particular Python version for a directory"
---

## Install and set a specific Python version for a directory

On a Mac (M1 / arm64), to install an older version of Python (say 2.7), follow these steps:

1. Install the required Python version using `pyenv`:  
   **`pyenv install 2.7.18`**  
   That should install Python-2.7.18 to **~/.pyenv/versions/2.7.18**  
   Check other versions of Python installed:  
   **`ls ~/.pyenv/versions`**  

2. To run that version of Python:  
   **`~/.pyenv/versions/2.7.18/bin/python`**  
   _Output_: `Python 2.7.18 (default, Jul 14 2024, 15:15:48) [GCC Apple LLVM 15.0.0 (clang-1500.3.9.4)] on Darwin`  

3. Check which version of Python `pyenv` is using:  
   **`pyenv version`**  
   _Output_: **`3.10.12`** (set by /Users/username/.pyenv/version)  

4. Set up a particular version for a directory (say 2.7), change to that directory, and run:  
   **`pyenv local 2.7.18`**  
   This creates a **.python-version** file in the current directory. Whenever you change to this directory or its subdirectories, pyenv will automatically switch to Python 2.7.18 for that session.  
   The **.python-version** simply has the Python version:  
   **`cat .python-version`**  
   _Output_: 2.7.18  

5. Check the Python version in that directory:  
   **`pyenv version`**  
   _Output_: **`2.7.18`** (set by /Users/username/somedirectory/.python-version)  

6. Try to change to the parent directory and check the Python version again:  
   **`cd ..`**  
   **`pyenv version`**  
   _Output_: **`3.10.12`** (set by /Users/username/.pyenv/version)  

7. To explicitly run Python 2.7.18 that is set by pyenv in the local directory, use pyenv’s exec command:  
   **`pyenv exec python`**  
   _Output_: Python 2.7.18 (default, Jul 14 2024, 15:15:48) ...

## Install a virtual environment in a directory using a specific Python version

It's good to install an app's dependencies in a local/virtual environment instead of polluting the global Python environment on your system. `virtualenv` available globally on the system might be set to use another version of Python than what was set using `pyenv` for a specific directory. To set up a virtual environment in a directory, first install `virtualenv` in the `pyenv`'s required Python version. Then create the virtual environment using that `virtualenv`. Follow these steps:

1. Use `pip` to install `virtualenv` using the Python 2.7 interpreter provided by `pyenv`:  
   **`~/.pyenv/versions/2.7.18/bin/pip install virtualenv`**  
   This command ensures `virtualenv` is installed using Python 2.7.18.  

2. Now create a virtual environment (say 'myenv') using the Python 2.7 interpreter:  
   **`~/.pyenv/versions/2.7.18/bin/virtualenv myenv`**  

3. Activate 'myenv' and verify the Python version:  
   **`source myenv/bin/activate`**  
   **`python --version`**  
   _Output_: `Python 2.7.18`  

4. Now go ahead and install the app's dependencies. If it has a 'requirements.txt':  
   **`pip install -r requirements.txt`**
