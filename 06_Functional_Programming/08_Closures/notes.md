# Closures

## Explanation

A **closure** occurs when a nested function captures variables from its enclosing scope, allowing those values to persist even after the outer function has finished executing. Closures are useful for creating data that is private to a function and establishing factories or callbacks.

## Examples

### Basic closure
```python
def make_multiplier(factor):
    def multiply(x):
        return x * factor
    return multiply

double = make_multiplier(2)
print(double(5))  # 10
```

### Using closure for state
```python
def counter():
    count = 0
    def incr():
        nonlocal count
        count += 1
        return count
    return incr

c = counter()
print(c())  # 1
print(c())  # 2
```

## Tasks

### Beginner
1. Create a closure that remembers a greeting string and appends it to names.
2. Explain why `factor` in the first example doesn’t change when `double` is called.

### Intermediate
1. Build a simple password checker using a closure to store the correct password.
2. Convert the counter example into a class; compare closure vs. class for state retention.

### Advanced
1. Write a decorator using closures (without `functools.wraps`).
2. Use closures to implement a simple caching mechanism.

## Quick Review
- What keyword allows you to modify a captured variable inside a closure?
- Why might you choose a closure over a global variable?

---