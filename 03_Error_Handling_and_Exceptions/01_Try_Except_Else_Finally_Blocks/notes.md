# Try Except Else Finally Blocks - Notes

## Overview
Exception handling allows programs to gracefully handle errors and unexpected situations. The try/except/else/finally structure provides comprehensive error management.

## 1. Basic Try-Except Structure

```python
try:
    # Code that might raise an exception
    result = 10 / 0
except ZeroDivisionError:
    # Handle the specific exception
    print("Cannot divide by zero!")
```

### Multiple Exception Types

```python
try:
    num = int(input("Enter a number: "))
    result = 10 / num
    print(f"Result: {result}")
except ValueError:
    print("Please enter a valid number")
except ZeroDivisionError:
    print("Cannot divide by zero")
```

### Catching All Exceptions

```python
try:
    # Risky code
    risky_operation()
except Exception as e:
    # Catch any exception
    print(f"An error occurred: {e}")
```

## 2. Else Clause

The `else` block executes only if no exceptions occur in the `try` block.

```python
try:
    file = open("data.txt", "r")
    content = file.read()
except FileNotFoundError:
    print("File not found")
else:
    # Only runs if no exception
    print("File read successfully")
    print(f"Content length: {len(content)}")
finally:
    # Always runs
    if 'file' in locals():
        file.close()
```

## 3. Finally Clause

The `finally` block always executes, regardless of whether an exception occurred.

```python
def process_file(filename):
    try:
        file = open(filename, "r")
        data = file.read()
        return data
    except FileNotFoundError:
        print("File not found")
        return None
    finally:
        # Always close the file
        if 'file' in locals():
            file.close()
        print("File operation completed")
```

### Use Cases for Finally
- Resource cleanup (files, database connections, network sockets)
- Releasing locks
- Resetting state

## 4. Exception Handling Patterns

### Resource Management with Finally

```python
def read_config():
    config_file = None
    try:
        config_file = open("config.ini", "r")
        config = {}
        for line in config_file:
            key, value = line.strip().split("=")
            config[key] = value
        return config
    except (FileNotFoundError, ValueError) as e:
        print(f"Error reading config: {e}")
        return {}
    finally:
        if config_file:
            config_file.close()
```

### Nested Try-Except Blocks

```python
try:
    # Outer try block
    try:
        # Inner try block
        result = risky_calculation()
    except ValueError:
        # Handle inner exception
        result = 0
    # Continue with result
    final_result = result * 2
except Exception:
    # Handle outer exception
    final_result = None
```

## Practice Tasks

### Beginner Level
1. Write a program that divides two numbers with proper exception handling for division by zero and invalid input.
2. Create a function that opens a file and handles FileNotFoundError.

### Intermediate Level
1. Implement a calculator that handles multiple types of errors (division by zero, invalid operations, etc.).
2. Write a program that processes a list of files, handling missing files gracefully.

### Advanced Level
1. Create a context manager using try/finally for database connections.
2. Implement a retry mechanism that catches specific exceptions and retries operations.

## Quick Review

### Key Concepts
- **try**: Code that might raise exceptions
- **except**: Handle specific or general exceptions
- **else**: Execute if no exceptions in try block
- **finally**: Always execute (cleanup code)

### Common Patterns
```python
# Safe file operations
try:
    with open(filename, 'r') as f:
        data = f.read()
except FileNotFoundError:
    data = None
except PermissionError:
    data = None
else:
    process_data(data)
finally:
    cleanup_resources()

# Input validation with retry
def get_number(prompt):
    while True:
        try:
            return float(input(prompt))
        except ValueError:
            print("Please enter a valid number")
```

### Best Practices
- Catch specific exceptions rather than generic Exception
- Use finally for resource cleanup
- Don't suppress exceptions unnecessarily
- Provide meaningful error messages
- Consider using context managers (with statement) for automatic cleanup