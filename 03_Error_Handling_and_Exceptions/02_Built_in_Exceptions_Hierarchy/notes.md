# Built-in Exceptions Hierarchy

## Explanation

Python has a rich hierarchy of built-in exceptions that are organized in a class-based structure. All exceptions inherit from the `BaseException` class, which is the root of the exception hierarchy. The most common base class for user-defined exceptions is `Exception`, which itself inherits from `BaseException`.

### Key Exception Classes:

1. **BaseException**: The base class for all exceptions. It provides basic functionality for exceptions.

2. **Exception**: The base class for all built-in non-system-exiting exceptions. Most user-defined exceptions should inherit from this class.

3. **ArithmeticError**: Base class for arithmetic errors.
   - `ZeroDivisionError`: Raised when division or modulo by zero occurs.
   - `OverflowError`: Raised when an arithmetic operation exceeds the limits of the data type.
   - `FloatingPointError`: Raised when a floating-point operation fails.

4. **LookupError**: Base class for lookup errors.
   - `IndexError`: Raised when a sequence subscript is out of range.
   - `KeyError`: Raised when a dictionary key is not found.

5. **OSError**: Base class for OS-related errors.
   - `FileNotFoundError`: Raised when a file or directory is requested but doesn't exist.
   - `PermissionError`: Raised when trying to run an operation without the adequate access rights.

6. **ValueError**: Raised when an operation or function receives an argument that has the right type but an inappropriate value.

7. **TypeError**: Raised when an operation or function is applied to an object of inappropriate type.

8. **AttributeError**: Raised when an attribute reference or assignment fails.

9. **NameError**: Raised when a local or global name is not found.

10. **ImportError**: Raised when an import statement fails to find the module definition.

Understanding this hierarchy helps in writing more specific exception handlers and creating custom exceptions that fit appropriately in the exception tree.

## Examples

### Example 1: Catching specific exceptions

```python
try:
    # This will raise ZeroDivisionError
    result = 10 / 0
except ZeroDivisionError as e:
    print(f"ZeroDivisionError: {e}")
except ArithmeticError as e:
    print(f"ArithmeticError: {e}")
```

### Example 2: Understanding exception hierarchy

```python
# ZeroDivisionError is a subclass of ArithmeticError
print(issubclass(ZeroDivisionError, ArithmeticError))  # True
print(issubclass(ArithmeticError, Exception))  # True
print(issubclass(Exception, BaseException))  # True

# KeyError is a subclass of LookupError
print(issubclass(KeyError, LookupError))  # True
```

### Example 3: Multiple exception types

```python
def safe_divide(a, b):
    try:
        return a / b
    except ZeroDivisionError:
        return "Cannot divide by zero"
    except TypeError:
        return "Invalid types for division"

print(safe_divide(10, 0))  # Cannot divide by zero
print(safe_divide(10, "2"))  # Invalid types for division
```

## Tasks

### Beginner

1. Write a function that divides two numbers and handles `ZeroDivisionError`.
2. Create a list and try to access an index that doesn't exist. Catch the `IndexError`.
3. Attempt to access a non-existent key in a dictionary and handle the `KeyError`.
4. Try to open a file that doesn't exist and catch `FileNotFoundError`.

### Intermediate

1. Create a function that accepts different types of inputs and raises appropriate exceptions for invalid types.
2. Implement a custom class that raises `AttributeError` when trying to access undefined attributes.
3. Write a program that demonstrates the difference between `ValueError` and `TypeError`.
4. Create a script that handles multiple types of file-related errors (`FileNotFoundError`, `PermissionError`).

### Advanced

1. Build a calculator class that handles various arithmetic exceptions and provides meaningful error messages.
2. Implement a data validator that checks input data and raises specific exceptions for different validation failures.
3. Create a file processor that handles multiple file operation exceptions and logs them appropriately.
4. Design an exception hierarchy for a banking system with specific exceptions for different account operations.

## Quick Review

- **BaseException**: Root of all exceptions
- **Exception**: Base for user exceptions
- **Common subclasses**: `ArithmeticError`, `LookupError`, `OSError`, `ValueError`, `TypeError`, etc.
- **Specific exceptions**: `ZeroDivisionError`, `IndexError`, `KeyError`, `FileNotFoundError`
- **Best practice**: Catch specific exceptions before general ones
- **Hierarchy checking**: Use `issubclass()` to understand relationships