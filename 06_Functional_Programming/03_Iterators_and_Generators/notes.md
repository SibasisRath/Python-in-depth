# Iterators and Generators

## Explanation

An **iterator** is an object that implements the `__iter__()` and `__next__()` methods, allowing traversal over a sequence. Python’s iteration protocols make `for` loops and many built-ins work seamlessly.

A **generator** is a special kind of iterator defined with a function that uses the `yield` statement. Generators produce items lazily, which is memory-efficient for large datasets.

## Examples

### Custom iterator
```python
class Countdown:
    def __init__(self, start):
        self.current = start

    def __iter__(self):
        return self

    def __next__(self):
        if self.current <= 0:
            raise StopIteration
        val = self.current
        self.current -= 1
        return val

for n in Countdown(3):
    print(n)
# 3
# 2
# 1
```

### Generator function
```python
def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

for num in fibonacci(5):
    print(num)
# 0 1 1 2 3
```

## Tasks

### Beginner
1. Convert a list to an iterator using `iter()` and retrieve elements with `next()`.
2. Write a simple generator that yields square numbers.

### Intermediate
1. Implement a generator that reads lines from a file one at a time.
2. Create an iterator class that cycles through a given list infinitely.

### Advanced
1. Build a coroutine using a generator that can receive values via `send()`.
2. Write a pipeline using generators to process a large text stream (filter, map, reduce).

## Quick Review
- What methods must an iterator implement?
- How does `yield` differ from `return`?

---