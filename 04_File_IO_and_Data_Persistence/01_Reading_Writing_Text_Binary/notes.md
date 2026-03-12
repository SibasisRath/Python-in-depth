# Reading and Writing Text and Binary Files

## Explanation

File input/output is a fundamental operation in most applications. Python makes it easy to open, read, write, and close files using built-in functions. Files can be opened in text mode (default) or binary mode.

- `open(filename, mode, encoding=None)` opens a file and returns a file object.
- Modes include: `'r'` (read), `'w'` (write, truncates), `'a'` (append), `'b'` (binary), `'x'` (exclusive creation), `'+'` (read/write).
- Always close files to release resources; use `file.close()` or context managers.

### Text vs Binary

- **Text mode**: strings are read/written; encoding/decoding occurs (default UTF-8).
- **Binary mode**: data is read/written as bytes; useful for images, audio, etc.

### Basic Operations

```python
# Writing text
with open('example.txt', 'w', encoding='utf-8') as f:
    f.write('Hello, world!\n')

# Reading text
with open('example.txt', 'r', encoding='utf-8') as f:
    content = f.read()
    print(content)

# Appending
with open('example.txt', 'a', encoding='utf-8') as f:
    f.write('Another line\n')

# Binary write
with open('image.png', 'wb') as f:
    f.write(b'\x89PNG...')

# Binary read
with open('image.png', 'rb') as f:
    data = f.read()
```

## Tasks

### Beginner

1. Write a program that creates a text file and writes several lines of text into it.
2. Read the file back and print each line.
3. Open a binary file (like an image) and print its first 20 bytes.

### Intermediate

1. Copy a binary file (e.g., an image) to a new location using read and write.
2. Write a function that reads a large file line-by-line without loading the entire file into memory.
3. Handle potential `IOError` exceptions during file operations.

### Advanced

1. Implement a simple file-based key-value store using binary mode for serialization.
2. Create a log rotation script that moves old log files to an archive directory.
3. Develop a text-processing pipeline that reads multiple files, processes the contents, and writes results to a new file.

## Quick Review

- Use `open()` with appropriate mode (`'r'`, `'w'`, `'a'`, `'b'`).
- Text mode deals with strings and encoding; binary mode uses bytes.
- Use context managers (`with`) to automatically close files.
- Check for exceptions like `FileNotFoundError` or `PermissionError` when opening files.