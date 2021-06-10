# Python

## Description

Unix-friendly scripting language with clear and simple synax as a goal. Designed by Guido van Rossum at early 1990s.

* [Homepage](https://www.python.org/)
* [PEP](https://www.python.org/dev/peps/) —  Python Enhancement Proposals, standarts of language

## Toolset

* [CPython](https://www.python.org/) — most popular reference environment \(interpreter and standard library\)
* [pip](https://pip.pypa.io/en/stable/) — package manager
* [PyPI](https://pypi.org/) — official modules repository
* [flake8](https://gitlab.com/pycqa/flake8) — linting tool wrapped up few utilities
* [mypy](http://mypy-lang.org/) — type checker
* [Django](https://www.djangoproject.com/) — popular MVC web-framework
* [NumPy](https://numpy.org/) — math library with comprehensive matrixes support

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

Modules, import or including. Major project files, common structure of library and application. Local environment.

```python
# Import module
import os

# Import object from module
from datetime import timedelta

# Import all objects from local module into current scope.
# Usually is undesirable.
from app.my_module import *
```

## Type system

* Dynamic or static
* Strong or weak
* Explicit or implicit

Scopes, variables lifecycle, copying and referencing, modificators like constant.

Generics.

## Base types and data structures

Built-in types, most common collections.

## Strings

Standard types to store strings. Tools and practices to splice, search, copy, replace textual data.

## Execution flow statements

Loops, conditions and jump operator or recursion.

## Exceptions

Handling exceptions or errors. Major exceptions hierarchy.

* 
## Subroutines

Functions, procedures, lambda expressions etc.

Introspection

## Object model

Object-oriented programming tools, syntax of classes.

## Asyncronous model

Asyncronous calls, multithreading, multiprocessing.

## Style guides

Major naming and structuring points.

