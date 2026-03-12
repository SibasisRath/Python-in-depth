# Context Managers with Files

## Explanation

Context managers in Python are used to ensure that resources are properly acquired and released. The most common pattern is the `with` statement, which simplifies exception handling and guarantees cleanup.

For file operations, using `with` ensures that the file is closed automatically, even if an exception occurs.

```python
with open('example.txt', 'r') as f:
    data = f.read()
# file is automatically closed here
```

### Creating a Custom Context Manager

You can create your own context managers using:

- **`__enter__` and `__exit__` methods** in a class
- The `contextlib` module with `@contextmanager` decorator

Example using a class:

```python
class ManagedFile:
    def __init__(self, filename, mode='r'):
        self.filename = filename
        self.mode = mode
    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file
    def __exit__(self, exc_type, exc_val, exc_tb):
        self.file.close()

with ManagedFile('test.txt', 'w') as f:
    f.write('hello')
```

Example using `contextlib`

```python
from contextlib import contextmanager

@contextmanager
def open_file(name, mode='r'):
    f = open(name, mode)
    try:
        yield f
    finally:
        f.close()

with open_file('test.txt', 'w') as f:
    f.write('hi')
```

## Tasks

### Beginner

1. Rewrite a file-reading script to use `with` instead of manually closing the file.
2. Observe what happens if an exception is raised inside a `with` block.

### Intermediate

1. Implement a custom context manager for acquiring/releasing a lock (use `threading.Lock`).
2. Use `contextlib.suppress` to ignore specific exceptions within a `with` block.

### Advanced

1. Design a context manager that temporarily changes the current working directory and restores it afterward.
2. Create a resource pool context manager that opens multiple files and ensures all are closed properly.

## Quick Review

- `with` statement ensures clean-up of resources.
- Implement custom managers via `__enter__/__exit__` or `contextlib`.
- `finally` block inside custom managers ensures resource release even on errors.