# Pickle for Object Serialization

## Explanation

The `pickle` module allows you to serialize and deserialize Python objects to and from byte streams. It is useful for saving program state or caching objects.

- `pickle.dump(obj, file)` writes the serialized object to a file.
- `pickle.load(file)` reads the object back.

### Security Warning

Never unpickle data received from an untrusted or unauthenticated source. Pickle can execute arbitrary code during unpickling.

### Example

```python
import pickle

data = {'a': 1, 'b': [2, 3, 4]}
with open('data.pkl', 'wb') as f:
    pickle.dump(data, f)

with open('data.pkl', 'rb') as f:
    obj = pickle.load(f)
    print(obj)
```

### Other Formats

- `shelve` module: provides a dictionary-like object backed by a pickle file
- `json` as safer alternative for simple data structures

## Tasks

### Beginner

1. Serialize a list of numbers to a `.pkl` file and read it back.
2. Experiment with pickling and unpickling a custom class instance.

### Intermediate

1. Use `shelve` to store key-value pairs and retrieve them.
2. Serialize a complex object graph and verify integrity after unpickling.

### Advanced

1. Implement versioning for pickled data: handle loading old formats gracefully.
2. Compare performance of pickle versus JSON or other serialization methods.
3. Build a caching decorator that pickles function results to disk.

## Quick Review

- Use `pickle.dump` and `pickle.load` for serialization.
- Always open files in binary mode (`'wb'`/`'rb'`).
- Beware of security risks; do not unpickle untrusted data.
- `shelve` offers simple persistent storage similar to a dictionary.