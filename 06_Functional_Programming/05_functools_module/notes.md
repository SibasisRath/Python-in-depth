# `functools` Module

## Explanation

The `functools` module provides higher-order functions and operations on callable objects. Common utilities include:

- `@lru_cache`: memoization decorator for caching results of function calls.
- `partial()`: fix some arguments of a function and return a new callable.
- `wraps()`: helper for writing decorators that preserve metadata.
- `reduce()`: as covered earlier, but also available here.
- `total_ordering`: decorator to fill in rich comparison methods.

These help with performance, functional patterns, and decorator implementation.

## Examples

### `lru_cache`
```python
from functools import lru_cache

@lru_cache(None)
def fib(n):
    if n < 2:
        return n
    return fib(n-1) + fib(n-2)

print(fib(30))  # fast after caching
```

### `partial`
```python
from functools import partial

def multiply(x, y):
    return x * y

double = partial(multiply, 2)
print(double(5))  # 10
```

### `wraps` in decorator
```python
from functools import wraps

def my_decorator(f):
    @wraps(f)
    def wrapper(*args, **kwargs):
        print("Calling", f.__name__)
        return f(*args, **kwargs)
    return wrapper

@my_decorator
def greet(name):
    """Say hello"""
    return f"Hello, {name}!"

print(greet.__name__)  # greet
print(greet.__doc__)   # Say hello
```

## Tasks

### Beginner
1. Apply `@lru_cache` to a recursive function and observe speedup.
2. Use `partial` to create a function that adds 10 to its argument.

### Intermediate
1. Write a decorator using `wraps` that logs execution time.
2. Use `total_ordering` to define comparisons for a custom class with only `__eq__` and `__lt__`.

### Advanced
1. Implement your own memoization decorator from scratch (without `functools`).
2. Explore other utilities in `functools` such as `cmp_to_key` for sorting.

## Quick Review
- What does `@lru_cache` do and when is it useful?
- How does `partial` help in functional composition?

---