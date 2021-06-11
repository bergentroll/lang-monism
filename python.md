# Python

## Description

Unix-friendly scripting language with clear and simple synax as a goal. Designed by Guido van Rossum at early 1990s. It based on object model, supports functional programming idioms and metaprogramming .

* [Homepage](https://www.python.org/)
* [PEP](https://www.python.org/dev/peps/) —  Python Enhancement Proposals, standarts of language

## Toolset

* [CPython](https://www.python.org/) — most popular reference environment \(interpreter and standard library\)
* [pip](https://pip.pypa.io/en/stable/) — package manager
* [PyPI](https://pypi.org/) — official modules repository
* [IPython](https://ipython.org/) — advanced Python shell.
* [flake8](https://gitlab.com/pycqa/flake8) — linting tool wrapped up few utilities
* [mypy](http://mypy-lang.org/) — type checker
* [Django](https://www.djangoproject.com/) — popular MVC web-framework
* [NumPy](https://numpy.org/) — math library with comprehensive matrixes support

Execution `python` or `ipython` gives an interactive shell in REPL mode. `help()` built-in function takes any object and gives docstring documentation. `dir()` built-in function lists all members of any object.

`python -m MODULE` used to run some executable module, e.g. to create a virtual environment at `env` directory `python -m venv env` command may be used.

## Basic syntax

```python
#! /bin/env python

'''
Fist line may be a hashbang. Then may go module docstring like this.
'''

# Blocks are specified with structural indentation.
# PEP8 specifies 4 spaces indentation level and 80 symbols line lenght.

if True:  # Colon is for beginning of block
    print('True')  # indentation to mark the block
```

## Comments

```python
# One line comment

'''
Multi-line literal

May be used as string, as mulit-line comment and as docstring.
For docstrings see
https://www.python.org/dev/peps/pep-0257/
'''

"""
The same meaning as '''
"""

class MyClass:
    '''
    This is a class docstring.
    '''
    pass
```

## Project model

Python file is a module. Special designed directory may be a module too. Modules are usually imported at top of program. Submodules may be pointed with dot-syntax like object fields.

```python
# Import module
import os

# Import object from module
from datetime import timedelta

# Import all objects from local module into current scope.
# Usually is undesirable.
from app.my_module import *
```

```python
#! /bin/env/ python3

# Here may be defined types, functions and object instances.
GLOBAL_VALUE = 100

if __name__ == '__main__':
    # Code here will be executed when module will be executed
    # but not when it will be imported into other module.
    print('Hello, world')
```

Python supports a number of tools to deal with "virtual environments" which is local directories with special module versions.

Install dependencies and run script from shell:

```bash
# Note you may have e.g. python3 and pip3 commands depends on your environment

# Create a local virtual environment to keep dependencies
python -m venv env

# Activate the local environment
source env/bin/activate

# Install project dependencies specified at Requirements.txt
pip install -r Requirements.txt

# Run project file main.py
python main.py
```

Requirements file is used to keep project dependencies:

```text
# Comments are allowed
reportlab
# Version may be speciefied with comparison operator
numpy==1.20.0
```

`setup.cfg` is standard project configuration file. It has INI format and may be used to configure different tools like linters.

## Type system

Python has dynamic \(duck typing\) strong implicit type system.

CPython implements garbage collection with GIL \(global interpreter lock\).

In Python everything is object. In Python 3 every type is child class of `object`.

Python 3 provides three scopes: local, global and nonlocal.

* Local is default one and is bounded with module, class, method or function.
* Module-level objects are in global scope. Also there is the `global` keyword to put variable into the global scope.
* Nonlocal scope is a closured with nested funciton scope.

```python
GLOBAL_VALUE = 'I am a module variable, and I am in the global scope'

def my_function():
    func_var = 'I am in the function local scope'
    def nested_function():
        func_var = 'But here I am in the nonlocal scope'
        nested_func_var = 'I am in the nested function local scope'
```

Object deletes when it reaches the end of scope.

Python does not require types indication in code, but Python 3 presented type annotation and develop it from version to version. Type annotation is hints about instances types and checked with tools such as [mypy](http://mypy-lang.org/) to make code more strict and prevent some kinds of bugs.

```python
# Standart module provides a bunch of primitives to annotate collections
# and other comples types.
import typing

# There is a colon syntax to annotate variables and args and arrow syntax
# to annotate returned values.

def worker(data: typing.List[str]) -> None:
    '''
    Function takes a list of strings and returns nothing.
    '''
    for item in data:
        print(item)
        
# Variable annotated as typing.Union may be one of pointed to Union types
value: typing.Union[str, int, bool] = 'I am a string'
value = True  # It is valid

# typing.Optional[SomeType] is equal to typing.Union[SomeType, None]
result: typing.Optional[str] = None
```

## Base types and data structures

int float str list dict set tuple

Read-only types

## Strings

Standard types to store strings. Tools and practices to splice, search, copy, replace textual data.

## Execution flow statements

Loops, conditions and jump operator or recursion.

## Filesystem

## Exceptions

```python
# Defines custom exception
class MyError(Exception):
    ...

# Raises exception
def my_func():
    raise MyError('Something goes wrong')

try:  # Wrap code into try block to handle exceptions
    my_func()
except (KeyError, MyError) as error:  # Catches KeyError and MyError
    print(f'Exception {type(error).__name__} with text {error} catched.')

```

Exception types grouped into class hierarhy:

* BaseException
  *  Exception
    * RuntimeError
    * SystemError
    * SyntaxError
    * ...
  * ...

## Subroutines

```python
# Functions may or may not return values and have args.
# Functions are objects.
def function(value, flag, optional=None):
    return (value, flag)  # Return a tuple

# args is a list of positional arguments, kvargs is a dict of named arguments
def var_args_function(*args, **kvargs):
    pass

list_of_odd = list(
    filter(
        lambda x: x % 2,  # lambda expression as arg of the filter function
        range(10)))
```

## Introspection

## Object model

Object-oriented programming tools, syntax of classes.

## Asyncronous model

Asyncronous calls, multithreading, multiprocessing.

## Style guides

Major naming and structuring points.

