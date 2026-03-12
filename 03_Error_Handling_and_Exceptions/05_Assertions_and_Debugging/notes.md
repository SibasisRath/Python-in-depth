# Assertions and Debugging

## Explanation

Assertions are statements that test a condition as a debugging aid; they are not meant to handle runtime errors in production code. An assertion uses the `assert` keyword followed by an expression that should evaluate to `True`. If the expression evaluates to `False`, an `AssertionError` is raised with an optional error message.

### When to Use Assertions

- To catch programmer errors during development.
- To document assumptions in the code (preconditions, postconditions, invariants).
- Not for handling user input or external conditions, since they can be disabled with optimization (`-O` flag).

### Debugging Tools

- **pdb**: Python's built-in interactive debugger. Use `import pdb; pdb.set_trace()` to drop into a debugging session.
- **logging**: While primarily for logging, it can also aid debugging with detailed messages and levels.
- **traceback module**: Provides utilities for extracting and formatting tracebacks.
- **IDE debuggers**: Most modern IDEs (VSCode, PyCharm) offer breakpoints, step execution, variable inspection, etc.

## Examples

### Using Assertions

```python
def divide(a, b):
    assert b != 0, "Denominator must not be zero"
    return a / b

print(divide(10, 2))
# print(divide(10, 0))  # triggers AssertionError
```

### Disabling Assertions

```
$ python -O script.py
```

The above command ignores all `assert` statements.

### Basic pdb Usage

```python
import pdb

def buggy_function(x):
    y = x + 1
    pdb.set_trace()
    z = y / 0  # will raise an error
    return z

buggy_function(5)
```

### Traceback example

```python
import traceback

try:
    1 / 0
except ZeroDivisionError as e:
    traceback.print_exc()
```

## Tasks

### Beginner

1. Add assertions to a function that computes factorial and checks for non-negative input.
2. Write a function with an assertion for list length before accessing an index.
3. Explore disabling assertions with the `-O` flag and observe behavior.

### Intermediate

1. Use `pdb` to step through a function that has a bug, and fix it.
2. Write a script that catches an exception and uses `traceback.print_exc()` to show the stack.
3. Practice using logging alongside assertions for more informative debugging output.

### Advanced

1. Create a custom assertion-like decorator that validates function preconditions.
2. Integrate `pdb` calls into a larger application and navigate through modules during a debugging session.
3. Develop a small debugging utility that captures variable states at exception points.

## Quick Review

- **assert**: Used for internal sanity checks during development.
- **Disable with -O**: Assertions can be turned off in optimized mode.
- **pdb**: Interactive debugger (`pdb.set_trace()`).
- **traceback**: Module for printing exception tracebacks.
- **Not for production**: Avoid using assertions for error handling in user-facing code.