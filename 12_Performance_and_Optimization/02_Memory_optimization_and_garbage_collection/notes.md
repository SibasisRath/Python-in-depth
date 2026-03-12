# Memory Optimization and Garbage Collection

## Explanation

Python uses reference counting and cyclic garbage collection to manage memory. The `gc` module controls garbage collection; `tracemalloc` tracks memory allocations. Optimize by minimizing object creation, using `__slots__` in classes, and avoiding circular references. Weak references allow objects to be garbage-collected while still referenced.

Key concepts:
- Reference counting vs generational GC
- `gc.collect()` to force collection
- `tracemalloc` for memory snapshots and traces

## Examples

```python
import gc
import tracemalloc

tracemalloc.start()

# Create some objects
data = [i for i in range(10000)]

snapshot = tracemalloc.take_snapshot()
top_stats = snapshot.statistics('lineno')

print("Top memory consumers:")
for stat in top_stats[:5]:
    print(stat)

gc.collect()  # Force garbage collection
```

## Tasks

### Beginner
1. Use `tracemalloc` to profile memory usage in a simple list comprehension.
2. Experiment with `gc.disable()` and `gc.enable()` and observe effects.

### Intermediate
1. Implement `__slots__` in a class and compare memory usage with and without it.
2. Detect and break a circular reference using `gc.get_referrers()`.

### Advanced
1. Profile memory leaks in a long-running script using tracemalloc snapshots.
2. Optimize a data structure to reduce memory footprint (e.g., use arrays instead of lists).

## Quick Review
- What is the difference between reference counting and garbage collection in Python?
- How do you start memory tracing with `tracemalloc`?
