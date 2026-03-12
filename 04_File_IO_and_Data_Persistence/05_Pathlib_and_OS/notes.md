# Pathlib and OS Module for File System Operations

## Explanation

Python offers multiple ways to work with file system paths and perform operations like listing directories, creating or deleting files, and querying metadata.

### os Module

The `os` module provides functions such as:

- `os.getcwd()` – get current working directory
- `os.chdir(path)` – change directory
- `os.listdir(path)` – list entries in a directory
- `os.makedirs(path)` – create directories recursively
- `os.remove(path)` / `os.unlink(path)` – delete a file
- `os.rmdir(path)` – remove an empty directory
- `os.path` submodule for path operations (`join`, `exists`, `isfile`, `isdir`, etc.)

```python
import os
print(os.getcwd())
for entry in os.listdir('.'):
    print(entry, os.path.isfile(entry))

if not os.path.exists('newdir'):
    os.makedirs('newdir')
```

### pathlib Module

`pathlib` provides an object-oriented approach to path manipulation.

```python
from pathlib import Path

p = Path('.')
print(p.resolve())
for child in p.iterdir():
    print(child.name, child.is_file())

newdir = Path('newdir')
newdir.mkdir(exist_ok=True)

# Path operations
print(newdir / 'subfile.txt')
```

`pathlib` works seamlessly with other libraries and can convert to/from strings with `str(pathobj)`.

## Tasks

### Beginner

1. Use `os` to list all files in a directory and print their sizes.
2. Create a directory structure using `os.makedirs` and then remove it.
3. Use `pathlib` to create a new file path and write/read text to it.

### Intermediate

1. Write a script that walks a directory tree and prints all `.py` files using `os.walk`.
2. Use `pathlib` to find all files larger than a specified size.
3. Compare the behaviors of `os.path.join` vs `pathlib.Path` concatenation.

### Advanced

1. Implement a cross-platform file synchronization utility using `pathlib` and `os`.
2. Write a tool that watches a directory for changes and logs events (use `watchdog` library optionally).
3. Build a utility that converts Windows-style paths to POSIX-style paths and vice versa.

## Quick Review

- `os` is procedural; `pathlib` is object-oriented.
- Use `os.path` for compatibility if not using `pathlib`.
- Pathlib `Path` objects have many helpful methods like `.exists()`, `.is_dir()`, `.iterdir()`.
- Both modules work with file I/O operations and metadata queries.