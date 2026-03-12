# Exception Chaining

## Explanation

Exception chaining in Python allows one exception to be raised during the handling of another exception, creating a linked chain of errors. This is useful for preserving context when an error occurs while handling another error.

Python provides two ways to chain exceptions:

1. **Implicit chaining**: When an exception is raised in an `except` block without using `from`, the new exception's `__context__` attribute is set to the original exception automatically.
2. **Explicit chaining**: Using the `raise ... from ...` syntax sets the new exception's `__cause__` attribute to the original exception and suppresses the context unless the interpreter can't handle the cause.

### Key Attributes

- `__context__`: Automatically set for implicit chaining, holds the previous exception.
- `__cause__`: Set by `raise ... from ...` for explicit chaining.
- `__suppress_context__`: When set to `True`, suppresses the automatic display of the exception context.

### Why Use Chaining?

- To maintain detailed error information through multiple layers of exception handlers.
- To provide clearer debugging information by showing the sequence of failures.
- To differentiate between the original cause and the new error being reported.

## Examples

### Implicit Chaining

```python
try:
    x = 1 / 0
except ZeroDivisionError as e:
    # This will set __context__ to the original ZeroDivisionError
    raise ValueError("Failed during computation")

# Output shows the context:
# Traceback (most recent call last):
#   File "<stdin>", line 2, in <module>
# ZeroDivisionError: division by zero
#
# During handling of the above exception, another exception occurred:
#
# Traceback (most recent call last):
#   File "<stdin>", line 4, in <module>
# ValueError: Failed during computation
```

### Explicit Chaining

```python
try:
    x = 1 / 0
except ZeroDivisionError as e:
    raise ValueError("Computation error") from e

# Output shows the cause:
# Traceback (most recent call last):
#   File "<stdin>", line 2, in <module>
# ZeroDivisionError: division by zero
#
# The above exception was the direct cause of the following exception:
#
# Traceback (most recent call last):
#   File "<stdin>", line 4, in <module>
# ValueError: Computation error
```

### Suppressing Context

```python
try:
    x = int('not-a-number')
except ValueError:
    # raise a new error without showing the original context
    raise RuntimeError("Conversion failed") from None

# Output:
# Traceback (most recent call last):
#   File "<stdin>", line 3, in <module>
# RuntimeError: Conversion failed
```

## Tasks

### Beginner

1. Write code that demonstrates implicit chaining by raising a new exception inside an `except` block.
2. Create a piece of code that uses `raise ... from ...` to chain exceptions explicitly.
3. Show how to suppress the context using `from None`.

### Intermediate

1. Implement a function that catches a `KeyError` and raises a custom `DataError` using explicit chaining.
2. Write a nested try/except block where an inner exception leads to an outer exception and display both context and cause.
3. Create a scenario where you intentionally suppress context to hide implementation details from the end user.

### Advanced

1. Build a small library that wraps lower-level errors (e.g., `IOError`) into higher-level domain-specific exceptions, using chaining.
2. Develop a debugging tool that prints out the full exception chain for any given error.
3. Design a system that logs exception chains with full stack traces and saves them to a file for later analysis.

## Quick Review

- **Implicit chaining**: Occurs automatically when a new exception is raised in an `except` block.
- **Explicit chaining**: Use `raise ... from ...` to set `__cause__`.
- **Suppressing context**: Use `from None` to prevent automatic context display.
- **Attributes**: `__context__`, `__cause__`, and `__suppress_context__` help inspect chaining.
- **Use case**: Retain error context and provide clearer debugging information.