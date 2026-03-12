# Advanced OOP Concepts - Notes

## Overview
This section dives into deeper object-oriented techniques: magic methods, context managers, descriptors, metaclasses, and dataclasses.

## 1. Magic Methods

Magic methods (dunder methods) allow objects to emulate built-in behavior.

```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)

    def __repr__(self):
        return f"Vector({self.x}, {self.y})"

    def __eq__(self, other):
        return self.x == other.x and self.y == other.y

v1 = Vector(1, 2)
v2 = Vector(3, 4)
print(v1 + v2)  # Vector(4, 6)
print(v1 == Vector(1, 2))  # True
```

Common magic methods:
- `__str__`, `__repr__`
- Arithmetic: `__add__`, `__sub__`, `__mul__`, etc.
- Comparison: `__lt__`, `__gt__`, etc.
- `__len__`, `__iter__`, `__next__`
- `__getitem__`, `__setitem__`

## 2. Context Managers (`with` statement)

```python
class FileManager:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode

    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_value, traceback):
        if self.file:
            self.file.close()

with FileManager("test.txt", "w") as f:
    f.write("Hello")
```

Use `contextlib` for simpler implementations:

```python
from contextlib import contextmanager

@contextmanager

def managed_file(name, mode):
    f = open(name, mode)
    try:
        yield f
    finally:
        f.close()
```

## 3. Descriptors and Property Decorators

Descriptors give fine control over attribute access.

```python
class Descriptor:
    def __init__(self, name=None):
        self.name = name

    def __get__(self, obj, objtype=None):
        return obj.__dict__[self.name]

    def __set__(self, obj, value):
        print(f"Setting {self.name} to {value}")
        obj.__dict__[self.name] = value

class MyClass:
    attr = Descriptor("attr")

m = MyClass()
m.attr = 10  # Setting attr to 10
print(m.attr)  # 10
```

Property decorator is built-in descriptor:

```python
class Celsius:
    def __init__(self, temperature=0):
        self._temperature = temperature

    @property
    def temperature(self):
        return self._temperature

    @temperature.setter
    def temperature(self, value):
        if value < -273.15:
            raise ValueError("Temperature below -273.15 is not possible")
        self._temperature = value

c = Celsius()
c.temperature = 37
print(c.temperature)  # 37
```

## 4. Metaclasses Basics

Metaclasses control class creation.

```python
class Meta(type):
    def __new__(cls, name, bases, class_dict):
        print(f"Creating class {name}")
        return type.__new__(cls, name, bases, class_dict)

class MyClass(metaclass=Meta):
    pass

# Output: Creating class MyClass
```

Use cases: automatic registration, enforcing patterns.

## 5. Data Classes (Python 3.7+)

```python
from dataclasses import dataclass

@dataclass
class Point:
    x: int
    y: int

p = Point(1, 2)
print(p)  # Point(x=1, y=2)
```

Features:
- Automatic `__init__`, `__repr__`, `__eq__`
- `field()` for default values and metadata

## Practice Tasks

### Beginner
1. Implement `__str__` and `__repr__` on a simple class.
2. Write a basic context manager using `__enter__`/`__exit__`.

### Intermediate
1. Create a descriptor to log attribute access.
2. Use `@dataclass` for a `Book` class with title, author, price.

### Advanced
1. Build a metaclass that registers subclasses in a global list.
2. Implement custom `__add__` and `__mul__` on a `Matrix` class.

## Quick Review
- **Magic methods**: customize built-in behavior
- **Context managers**: manage resources with `with`
- **Descriptors**: control attribute access
- **Metaclasses**: modify class creation
- **Dataclasses**: generate boilerplate automatically

### Common Patterns
```python
# Custom metaclass
class Singleton(type):
    _instances = {}
    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            cls._instances[cls] = super().__call__(*args, **kwargs)
        return cls._instances[cls]

class Logger(metaclass=Singleton):
    pass
```
