# Working with Different Encodings and Charsets

## Explanation

When reading or writing text files, it's important to handle character encodings correctly. Python uses Unicode internally, and the `encoding` parameter of `open()` specifies how to encode or decode the file contents.

Common encodings include `utf-8` (default in Python 3), `latin-1`, `ascii`, `utf-16`, etc. Using the wrong encoding can lead to `UnicodeDecodeError` or `UnicodeEncodeError`.

### Detecting Encoding

Modules like `chardet` or `charset-normalizer` (third-party) can help detect an unknown encoding.

### Example

```python
# writing with utf-8
with open('utf8.txt', 'w', encoding='utf-8') as f:
    f.write('Café — ☕\n')

# reading with explicit encoding
with open('utf8.txt', 'r', encoding='utf-8') as f:
    print(f.read())

# mis-match example
with open('utf8.txt', 'r', encoding='ascii') as f:
    # will raise UnicodeDecodeError
    try:
        print(f.read())
    except UnicodeDecodeError as e:
        print('Decoding error:', e)
```

## Tasks

### Beginner

1. Open a file with explicit UTF-8 encoding and read a string with non-ASCII characters.
2. Write a file using `latin-1` encoding and then read it back.
3. Trigger and catch a `UnicodeDecodeError` by using the wrong encoding.

### Intermediate

1. Read a file with an unknown encoding and try to detect it using `chardet`.
2. Convert a text file from one encoding to another (e.g., latin-1 to utf-8).
3. Work with BOM (byte order mark) in UTF-16 files.

### Advanced

1. Build a script to recursively scan text files and normalize them to UTF-8.
2. Handle streaming text data from network sources with mixed encodings.
3. Implement an editor-like function that auto-detects encoding and re-saves text.

## Quick Review

- Always specify `encoding` when opening text files if they contain non-ASCII.
- Use `utf-8` by default; other encodings may be required for legacy data.
- `UnicodeDecodeError` and `UnicodeEncodeError` indicate mismatched encodings.
- Tools like `chardet` can help guess file encoding; be cautious with detection accuracy.