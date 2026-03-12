# Modules and Packages - Notes

## Overview
Modules and packages help organize code into reusable, manageable components. This section discusses importing, creating custom modules, the `__name__ == "__main__"` pattern, and package management.

## 1. Importing Modules

### Built-in Modules

```python
import math
print(math.sqrt(16))  # 4.0

import random
print(random.randint(1, 10))
```

### Specific Imports

```python
from math import sqrt, pi
print(sqrt(25))  # 5.0
print(pi)        # 3.141592653589793
```

### Aliasing

```python
import numpy as np
from datetime import datetime as dt
```

### Importing from Packages

```python
from collections import defaultdict
from os import path
```

## 2. Creating Custom Modules

```python
# file: utilities.py

def add(a, b):
    return a + b

PI = 3.14159
```

```python
# file: main.py
import utilities

print(utilities.add(2, 3))
print(utilities.PI)
```

### Module Search Path

```python
import sys
print(sys.path)
```

## 3. __name__ == "__main__" Pattern

```python
# module: example.py

def main():
    print("Running as script")

if __name__ == "__main__":
    main()
```

This allows the file to be imported without executing the script portion.

## 4. Standard Library Overview

Key modules:
- `os` / `sys` for system operations
- `datetime` for dates/times
- `json` / `csv` for data serialization
- `re` for regular expressions
- `subprocess` for spawning processes
- `pathlib` for path operations

## 5. Virtual Environments (venv, virtualenv)

```bash
# create and activate
python3 -m venv venv
source venv/bin/activate

# install packages
pip install requests

# freeze dependencies
pip freeze > requirements.txt

# deactivate
deactivate
```

## 6. Requirements.txt and Dependency Management

```
# requirements.txt
Django==3.2
requests>=2.25

# install
pip install -r requirements.txt
```

Use tools like `pipenv` or `poetry` for more advanced workflows.

## Practice Tasks

### Beginner
1. Create a module with a few utility functions and import them from another file.
2. Experiment with `__name__ == "__main__"` by running module directly and importing it.

### Intermediate
1. Build a package with `__init__.py` and submodules.
2. Use `pip freeze` to generate `requirements.txt` and recreate the environment.

### Advanced
1. Publish a simple package to PyPI (use `setup.py` or `pyproject.toml`).
2. Use virtual environments to manage conflicting dependencies across projects.

## Quick Review

- **Modules**: `.py` files containing code
- **Packages**: directories with `__init__.py`
- **import**: bring functionality into scope
- **__name__**: identifies module execution context
- **venv**: isolated Python environment
- **requirements.txt**: track dependencies

### Common Patterns

```python
# package structure
my_package/
    __init__.py
    module1.py
    module2.py

# __init__.py
from .module1 import func1
from .module2 import func2

# usage
from my_package import func1
```