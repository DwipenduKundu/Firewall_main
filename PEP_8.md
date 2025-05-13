# PEP 8: 
## Introduction
PEP 8 is the Python Enhancement Proposal which outlines the conventions for writing readable and consistent Python code. Adhering to these guidelines helps developers produce code that is easier to read and maintain.

## Code Lay-out

### Indentation

* Use 4 spaces per indentation level.

```
def example():
    x = 1
    if x > 0:
        print("Positive")
```

### Tabs or Spaces?

* Spaces are the preferred indentation method.
* Tabs should be used only to remain consistent with code that is already indented with tabs.

### Maximum Line Length

* Limit all lines to a maximum of 79 characters.
* For docstrings and comments, limit lines to 72 characters.

```
# Correct
x = "This is a long string, but it is within the character limit."

# Wrong
x = "This is a very long string that goes beyond the recommended character limit."
```

### Should a Line Break Before or After a Binary Operator?

* Break lines **before** binary operators to improve readability.

```
# Correct
income = (gross_income
          - tax
          - other_deductions)

# Wrong
income = (gross_income -
          tax -
          other_deductions)
```

### Blank Lines

* Use blank lines to separate functions and class definitions.
* Within functions, use blank lines sparingly to indicate logical sections.

```
def first_function():
    pass


def second_function():
    pass
```

### Source File Encoding

* By default, Python source files are encoded in UTF-8.
* If using a different encoding, declare it at the top of the file:

```
# -*- coding: latin-1 -*-
```

### Imports

* Imports should usually be on separate lines.

```
# Right
import os
import sys

from tensorflow.keras import backend, models
model = models.load_model('your_model_path.h5')


# Wrong:
import sys, os
```

* Imports should be grouped in the following order:

  1. Standard library imports
  2. Related third party imports
  3. Local application/library specific imports

* Use a blank line between each group.

```
import os
import sys

import requests

import my_local_module
```

### Module Level Dunder Names

* Module-level "dunder" (double underscore) names like `__all__`, `__version__`, and `__author__` should appear near the top of the module.

```
__author__ = "John Doe"
__version__ = "1.0"
```

## String Quotes

* In Python, single (`'`) and double (`"`) quotes are equivalent.
* Choose one style consistently within a project.
* Use the other style to avoid escaping.

```
# Consistent single quotes
message = 'Hello, world!'

# Use double quotes to avoid escaping
message = "It's a beautiful day."
```

## Whitespace in Expressions and Statements

Avoid extraneous whitespace:

```
# Correct:
x = 1

# Wrong:
x             = 1
```

Use a single space around binary operators:

```
x = x + 1
```

No space immediately inside parentheses, brackets, or braces:

```
# Correct:
spam(ham[1], {eggs: 2})

# Wrong:
spam( ham[ 1 ], { eggs: 2 } )
```

## Pet Peeves

Avoid extra spaces:
Immediately inside parentheses, brackets or braces:
```
# Correct:
spam(ham[1], {eggs: 2})
# Wrong:
spam( ham[ 1 ], { eggs: 2 } )
```
Between a trailing comma and a following close parenthesis:
```
# Correct:
foo = (0,)
# Wrong:
bar = (0, )
```
Immediately before a comma, semicolon, or colon:
```
# Correct:
if x == 4: print(x, y); x, y = y, x
# Wrong:
if x == 4 : print(x , y) ; x , y = y , x
```
------

## Other Recommendations

```
# Correct:
i = i + 1
submitted += 1
x = x*2 - 1
hypot2 = x*x + y*y
c = (a+b) * (a-b)

# Wrong:
i=i+1
submitted +=1
x = x * 2 - 1
hypot2 = x * x + y * y
c = (a + b) * (a - b)
```


## Comments

Comments should be complete sentences and helpful to the reader.

### Block Comments

* Apply to some (or all) code that follows them.
* Each line of a block comment should start with a `#` and a single space.

```
# Loop through the list
# and print each item
for item in items:
    print(item)
```

### Inline Comments

* Place on the same line as a statement.
* Use them sparingly.

```
x = x + 1  # Increment counter
```

### Documentation Strings

* Use triple quotes (`"""`) for docstrings.
* The first line should be a short description.
* Follow with more details if necessary.

```
def greet(name):
    """Greet a person by name."""
    print(f"Hello, {name}!")
```

## Naming Conventions

### Overriding Principle

Use the naming style most appropriate for the context. Be consistent.

### Descriptive: Naming Styles

* `b`: single lowercase letter
* `lowercase`
* `lower_case_with_underscores`
* `UPPER_CASE_WITH_UNDERSCORES`
* `CapitalizedWords`
* `mixedCase` (not recommended for new code)

### Prescriptive: Naming Conventions

```
# Function
 def my_function():
     pass

# Variable
 user_name = "Alice"

# Class
 class MyClass:
     pass

# Constant
 MAX_USERS = 100

# Module or package
 import my_module
```

### Names to Avoid

Avoid `l`, `O`, `I` as they are visually confusing:

```
# Bad:
i = 1  # Looks like '1'
```

### ASCII Compatibility

Identifiers should stick to ASCII for maximum compatibility:

```
# Good:
user_name = "Alice"

# Avoid non-ASCII:
naïve_user = "Bob"  # Might cause encoding issues
```

### Package and Module Names

```
# Good:
import data_tools

# Acceptable:
import data_tools_v2
```

### Class Names

```
class BankAccount:
    pass

class _InternalHelper:
    pass  # Internal use
```

### Type Variable Names

```
from typing import TypeVar

T = TypeVar("T")
AnyStr = TypeVar("AnyStr", str, bytes)
```

### Exception Names

```
class CustomError(Exception):
    pass
```

### Global Variable Names

```
config_path = "/etc/config"
```

### Function and Variable Names

```
def calculate_area(width, height):
    return width * height
```

### Function and Method Arguments

```
class Example:
    def instance_method(self, arg):
        pass

    @classmethod
    def class_method(cls, arg):
        pass
```

### Method Names and Instance Variables

```
class User:
    def __init__(self):
        self.user_id = 0
        self._temp_token = None  # Internal use
```

### Constants

```
PI = 3.14159
DEFAULT_TIMEOUT = 30
```

### Designing for Inheritance

Document overridable methods clearly:

```
class Base:
    def do_something(self):
        """Override this in subclass to implement specific behavior."""
        raise NotImplementedError
```

### Public and Internal Interfaces

```
# Public function
 def connect():
     pass

# Internal helper
 def _parse_url():
     pass
```

## Programming Recommendations

### Function Annotations

Use them for documenting expected types:

```
def greet(name: str) -> str:
    return f"Hello, {name}"
```

### Variable Annotations

You may annotate variables with types:

```
age: int = 25
```
### Extra:
```
# Correct:
def f(x): return 2*x
# Wrong:
f = lambda x: 2*x
```
```
# Correct:
if foo is not None:
# Wrong:
if not foo is None:
```