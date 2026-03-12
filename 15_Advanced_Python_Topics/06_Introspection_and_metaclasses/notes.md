# Introspection and Metaclasses

## Explanation

Introspection examines objects at runtime using functions like `dir()`, `getattr()`, `inspect` module, and `type()`. Metaclasses are classes of classes; they define how a class behaves. Advanced topic for framework developers; use sparingly. Understand `type()`, `__new__`, `__init__`, and `__mro__` (Method Resolution Order).

Key tools:
- `type()` for class/type inspection
- `isinstance()` and `issubclass()`
- `inspect` module for detailed examination
- Metaclass definition with `type()` or `class Meta(type)`

## Examples

```python
class MyMeta(type):
    def __new__(mcs, name, bases, namespace):
        print(f"Creating class {name}")
        return super().__new__(mcs, name, bases, namespace)

class MyClass(metaclass=MyMeta):
    pass
```

Introspection:
```python
import inspect

def my_func(a, b):
    return a + b

sig = inspect.signature(my_func)
print(sig)  # (a, b)
```

## Tasks

### Beginner
1. Use introspection to examine a class and list its methods.
2. Experiment with `getattr()`, `setattr()`, and `hasattr()`.

### Intermediate
1. Create a simple metaclass that logs method calls.
2. Use `inspect.signature()` to analyze function parameters.

### Advanced
1. Implement an ORM-like metaclass for automatic table mapping.
2. Explore ABCs (Abstract Base Classes) and their metaclasses.

## Quick Review
- What is a metaclass?
- How do you define a custom metaclass in Python?
