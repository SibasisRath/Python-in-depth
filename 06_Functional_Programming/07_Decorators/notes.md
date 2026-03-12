# Decorators

## Explanation

Decorators are functions that take another function and extend or modify its behavior without explicitly changing its code. They are frequently used for logging, access control, timing, and caching.

A decorator is applied with the `@decorator` syntax above a function definition. Decorators can also be stacked.

## Examples

### Simple decorator
```python
def my_decorator(func):
    def wrapper(*args, **kwargs):
        print("Before call")
        result = func(*args, **kwargs)
        print("After call")
        return result
    return wrapper

@my_decorator
def say_hi():
    print("Hi")

say_hi()
# Before call
# Hi
# After call
```

### Using `functools.wraps`
```python
from functools import wraps

def debug(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        return func(*args, **kwargs)
    return wrapper

@debug
def add(a, b):
    return a + b

print(add(2,3))  # Calling add
                  # 5
```

## Tasks

### Beginner
1. Write a decorator that prints "Entering" and "Exiting" around a function call.
2. Apply a decorator to a function that takes arguments and returns a value.

### Intermediate
1. Create a decorator that measures and prints execution time.
2. Write a decorator factory that takes an argument (e.g., a logging level).

### Advanced
1. Implement a class-based decorator that counts how many times a function has been called.
2. Combine multiple decorators and reason about the order in which they execute.

## Quick Review
- How do you preserve a function’s metadata when writing a decorator?
- What happens to function arguments when using `*args, **kwargs` in a wrapper?

---