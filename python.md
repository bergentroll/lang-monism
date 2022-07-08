# Python

## Description

Unix-friendly scripting language with clear and simple syntax as a goal. Designed by Guido van Rossum at early 1990s. It based on object model, supports functional programming idioms and metaprogramming.

* [Homepage](https://www.python.org/) :snake:
* [PEP](https://www.python.org/dev/peps/) — Python Enhancement Proposals, standards of language :blue\_book:

## Toolset

* [CPython](https://www.python.org/) — most popular reference environment (interpreter and standard library)
* [pip](https://pip.pypa.io/en/stable/) — package manager
* [PyPI](https://pypi.org/) — official modules repository
* [IPython](https://ipython.org/) — advanced Python shell.
* [flake8](https://gitlab.com/pycqa/flake8) — linting tool wrapped up few utilities
* [Pylint](https://www.pylint.org/) — another major linter
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

```
# Comments are allowed
reportlab
# Version may be speciefied with comparison operator
numpy==1.20.0
```

`setup.cfg` is standard project configuration file. It has INI format and may be used to configure different tools like linters.

## Type system

Python has dynamic (duck typing) strong implicit type system.

CPython implements garbage collection with GIL (global interpreter lock).

In Python everything is object. In Python 3 every type is child class of `object`.

Python variables works like references. There are mutable and immutable types. Objects of immutable types can not be changed and just copied on assignment. Variable of mutable type just gets new reference on assignment.

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

```python
''' Immutable types '''
# int
i = 1

# float
f1 = float(1)
f2 = 1.0

#bool
b = True

# str
string = 'I am a string and i am immutable'
```

```python
''' Mutable collections '''

# list (dynamic array)
l1 = list(range(3))
l2 = [0, 1, 2, 3]
l3 = [float(i) for i in range(10) if i % 2]  # With comprehensions expression

# dict (associative array)
d = {'zero': 0, 'one': 1, 'two': 2, 'three': 3}

# set
st = {0, 1, 2, 3}

# tuple (fixed size array)
t = (0, 1, 2, 3)
```

## Strings

`str` is a built-in immutable type for strings. There is member access operations like as `list` has.

```python
# Both '' and "" are valid and equal for string literals
s: str = "This is" + ' the string variable.'

# Taking slice (produce a new string)
s[0:10]

# Test ending of string
s.endswidth('able.')

# Find first matching of substring
s.find('iab')

# Make a list of tokens
s.split()

# Join collection of strings with string
', '.join(s.split())

# Replace every match of 'i' with 'o'
s.replace('i', 'o')
```

There is three major ways of string formatting:

```python
x = 10
y = 15

# Plain concatenation (not actually formatting)
s = 'Coordinates is ' + str(x) + ':' + str(y)

# Modern in-place f-strings
s = f'Coordinates is {x}:{y}'

# str.format() method
s = 'Coordinates is {}:{}'.format(x, y)

# Oldschool C-style
s = 'Coordinates is %i:%i' % (x,  y)

# There is also formatting syntax for placeholders
f'{x:10.2f}'
```

## Execution flow statements

There are `if`,`else` statements and `for`, `while` loops.

```python
if 'o' is not in 'Hello':
    print('That is false')

# for works like foreach
for i in range(10):
    if i == 0:
        continue  # Skip the remaining statements for this iteration
    print(i)

while True:
    break  # leave the current cycle

# No goto :'(
```

## Subroutines

```python
# Functions may or may not return values and have args.
# Functions are objects.
def function(value, flag, optional=None):
    return (value, flag)  # Return a tuple

# args is a list of positional arguments, kvargs is a dict of named arguments
def var_args_function(*args, **kvargs):
    pass

# Generator funciton with yield keyword.
# It can be iterated and calculates lazely (when a next value is needed).
def gen(max=10):
    i = 0
    while i < max:
        i += 2
        yield(i)

for val in gen():
    print(val)

list_of_odd = list(
    filter(
        lambda x: x % 2,  # lambda expression as arg of the filter function
        range(10)))
```

## Object model

Python has `class` keyword for user-defined complex types.

```python
# User defined type
class MyType:
    # Class level variable
    COUNTER = 0

    # Constructor, self is a reference on object itself
    def __init__(self, name=''):
        # Instance level variable
        self.name = name
        # Prepended underscore means the member is private
        # therefore it is just an agreement for users
        self._secret_name = f'Secret name {name}'
        MyType.COUNTER += 1

    # Destructor
    def __del__(self):
        MyType.COUNTER -= 1

    # Ordinary member function, getter
    def get_secret_name(self):
        return self._secret_name

    # property decorator creates calculable data member
    @property
    def upper_name(self):
        return self.name.upper()

# Constructing an instance
obj = MyType('Object Jonny')

# Accessing object members
obj.name
obj.COUNTER
obj.get_secret_name()
# "Private" members are still accessible
obj._secret_name
obj.upper_name
```

There are bunch of special dunder methods know as magic and used for overloading.

```
# TODO __add__() and other magic
```

_TODO Inheritance, ABC_

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

There is nice builtin [exceptions hierarchy](https://docs.python.org/3/library/exceptions.html). Most useful classes are `Exception`, `RuntimeError`, `SyntaxError`, `NotImplementedError`,  `TypeError` and also FileNotFoundError.

Custom Exceptions should inherit the appropriate builtin type.

```python
try:
    ...
except:  # Generic excepting is possible but not recommended
    ...
```

## Filesystem

```python
'''
Reading and writing to file example
'''

from datetime import datetime

# Open file and read contents
f = open('data.txt', mode='w', encoding='utf-8-sig')
f.write(str(datetime.now()))
f.close()  # File should be closed after usage

# With context manager
with open('data.txt', mode='r') as f:
    content: str = f.read()
    empty = f.read()  # The reading pointer is on end of file already

print(content)
print(empty)
```

```python
'''
Exploring directories
'''

import os

PATH = os.path.expanduser('~/')

# Recursive directory traversal
def deep_list(path):
    for (dirpath, dirnames, filenames) in os.walk(path):
        print(dirpath)

# Iterate through directory listing
for node_path in os.listdir(PATH):
    abs_node_path = os.path.abspath(PATH + node_path)
    if os.path.isfile(abs_node_path):
        print(f'File {node_path}')
    elif os.path.isdir(abs_node_path):
        print(f'Directory {node_path}')
```

## Introspection

Built-in function `type(obj)` returns a type of a passed object.

Built-in functions `isinstance(obj, typename)`, `issubclass(typename_a, typename_b)` is useful to explore hierarchies of classes.

```python
class A:
    ...


class B(A):
    ...


class C:
    ...


a = A()

isinstance(a, A) == True
isinstance(a, B) == False

issubclass(B, A) == True
issubclass(C, A) == False
issubclass(C, object) == True

type(a).__name__

b = B()

issubclass(type(b), A) == True
```

The `inspect` module provides useful tools to explore objects' attributes.

```python
iimport sys
import inspect


class A:
    def method_a(self):
        ...


class B(A):
    def method_b(self):
        ...


b = B()

# Thera are a plenty of other inspect.as*(obj) functions also
inspect.isclass(B)
inspect.ismethod(b.method_b)

# Make list of names of object methods
[name for name, type_ in inspect.getmembers(b)
    if inspect.ismethod(type_)] == ['method_a', 'method_b']

# Make list of types in current module
[type_ for name, type_ in inspect.getmembers(sys.modules[__name__])
    if inspect.isclass(type_)] == [A, B]

# Get method resolving order sequence
inspect.getmro(B) == (B, A, object)
```

## Asyncronous model

Three major models in modern Python:

* Threads based with [threading](https://docs.python.org/3/library/multiprocessing.html) module. Uses OS threads, but hardly limited with GIL (global interpreter lock), which means performance comatible to single thread.:snail:
* Processes based with [multiprocessing](https://docs.python.org/3/library/multiprocessing.html) module. Allow to efficiently spread load between CPU cores, but have&#x20;
* Coroutins concurrency with [asyncio](python.md#asyncronous-model) module.

{% code title="asyncio_example1.py" %}
```python
import asyncio
import typing


# ↓ keyword async is built-in since 3.5 to mark awaitable coroutins
async def job(string: str) -> None:
    # ↓ keyword is a built-in that makes execution to wait a coroutine return
    await asyncio.sleep(1)
    # also the sleep ↑ from asyncio pauses an execution and allows to run other
    # coroutines in the event loop
    print(string)

# False, job is just a function
print(isinstance(job, typing.Awaitable))

# But job returns a coroutine
coro = job('job0')
print(isinstance(coro, typing.Awaitable))

# Let run the coro at last
asyncio.run(coro)
```
{% endcode %}

## Style guides

[PEP8](https://www.python.org/dev/peps/pep-0008/) is a comprehensive style guide. [Toolset](python.md#toolset) section gives some most common linting tools.

```python
'''
Exaple shows most common naming and code structure conventions
'''

import os
import datetime  # Separate imports

GLOBAL_VAR = 'Value'


# Two empty lines before functions
def my_function(val, flag=True):  # No spaces around = in args list
    pass  # 4 spaces for indented blocks


# Two empty lines before class defenitions
class MyClass:
    def __init__(self):
        local_var = 50
        self.property = 100
```
