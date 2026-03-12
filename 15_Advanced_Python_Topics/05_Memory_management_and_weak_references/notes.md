# Memory Management and Weak References

## Explanation

Python uses reference counting for memory management; when reference count reaches zero, the garbage collector reclaims memory. Weak references allow objects to be garbage-collected while still being referenced. Use `weakref` module to avoid circular references and memory leaks. Understand reference cycles, `__del__`, and finalization.

Key concepts:
- Reference counting and garbage collection
- Strong vs weak references
- Circular references and memory leaks
- `weakref.ref()` and `weakref.proxy()`
- `gc` module for garbage collection control

## Examples

```python
import weakref

class Node:
    def __init__(self, value):
        self.value = value

node = Node(42)
weak_ref = weakref.ref(node)

print(weak_ref())  # <Node object>
del node
print(weak_ref())  # None
```

Avoiding circular references:
```python
class Parent:
    def __init__(self, name):
        self.name = name
        self.children = []

class Child:
    def __init__(self, name, parent):
        self.name = name
        self.parent = weakref.ref(parent)
```

## Tasks

### Beginner
1. Create a weak reference and observe when the object is garbage-collected.
2. Use `sys.getrefcount()` to inspect reference counts.

### Intermediate
1. Detect and break circular references in a class hierarchy.
2. Implement a cache using weak references.

### Advanced
1. Profile memory usage with and without weak references.
2. Explore finalization with `weakref.finalize()`.

## Quick Review
- What is the difference between a strong reference and a weak reference?
- How do circular references affect garbage collection?
