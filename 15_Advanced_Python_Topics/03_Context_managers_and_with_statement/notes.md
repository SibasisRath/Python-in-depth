# Context Managers and with Statement

## Explanation

Context managers manage setup and teardown of resources using the `with` statement. Implement by defining `__enter__` and `__exit__` methods (or use `@contextmanager` decorator). Ensures resources are properly released even if exceptions occur. Use for files, database connections, locks, etc.

Key features:
- `with` statement syntax
- `__enter__` and `__exit__` protocol
- Exception handling in `__exit__`
- `contextlib` for decorators

## Examples

```python
class FileManager:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode
        self.file = None

    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_val, exc_tb):
        if self.file:
            self.file.close()

# Usage
with FileManager('data.txt', 'r') as f:
    content = f.read()
```

Using decorator:
```python
from contextlib import contextmanager

@contextmanager
def managed_resource():
    print("Setup")
    yield "resource"
    print("Teardown")
```

## Tasks

### Beginner
1. Create a simple context manager for a resource and test it.
2. Use `with` to open a file and verify it closes.

### Intermediate
1. Implement context manager with exception handling.
2. Create a context manager using the `@contextmanager` decorator.

### Advanced
1. Combine multiple context managers with nested `with` statements.
2. Create a timer context manager for performance measurement.

## Quick Review
- What two methods must a context manager implement?
- What happens if an exception occurs inside a `with` block?
