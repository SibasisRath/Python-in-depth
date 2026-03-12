# Custom Iterators and Iterables

## Explanation

Iterables implement `__iter__()` to return an iterator; iterators implement `__next__()` to return successive values. Distinguish between iterable (object you can loop over) and iterator (stateful object returning items). Use generators (`yield`) for simpler iterator creation. Implement custom iterators for lazy evaluation and memory efficiency.

Key concepts:
- `__iter__()` returns an iterator
- `__next__()` returns next value or raises `StopIteration`
- Generators create iterators concisely
- `itertools` for functional iteration tools

## Examples

```python
class CountUp:
    def __init__(self, max):
        self.max = max
        self.current = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.current < self.max:
            self.current += 1
            return self.current
        raise StopIteration

for num in CountUp(3):
    print(num)  # 1, 2, 3
```

Generator:
```python
def count_up(max):
    current = 0
    while current < max:
        current += 1
        yield current
```

## Tasks

### Beginner
1. Create a custom iterator class and iterate over it.
2. Write a generator function with `yield`.

### Intermediate
1. Create an iterable that yields filtered values.
2. Use `itertools` to combine/transform iterables.

### Advanced
1. Implement a lazy Fibonacci sequence generator.
2. Create a custom iterator that supports both forward and reverse iteration.

## Quick Review
- What is the difference between an iterable and an iterator?
- What keyword creates a generator function?
