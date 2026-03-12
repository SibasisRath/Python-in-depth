# Map, Filter, Reduce

## Explanation

These built-in functions support functional-style operations on iterables.

- `map(func, iterable)`: apply `func` to each element and return an iterator of results.
- `filter(func, iterable)`: include only elements where `func(element)` is truthy.
- `reduce(func, iterable, [initializer])`: cumulatively apply `func` to elements, reducing to a single value (from `functools`).

They promote concise, declarative code.

## Examples

```python
numbers = [1, 2, 3, 4]
squares = list(map(lambda x: x*x, numbers))
print(squares)  # [1, 4, 9, 16]

evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)  # [2, 4]

from functools import reduce
product = reduce(lambda a, b: a * b, numbers)
print(product)  # 24
```

## Tasks

### Beginner
1. Use `map` to convert a list of strings to uppercase.
2. Use `filter` to remove empty strings from a list.
3. Compute the factorial of a number using `reduce`.

### Intermediate
1. Combine `map` and `filter` to process a list in one line.
2. Write a custom `map` function using a for-loop to replicate the behavior of the built-in.

### Advanced
1. Implement a `reduce`-like function that can handle multiple iterables simultaneously.
2. Analyze the performance of `map` vs a list comprehension for large datasets using `timeit`.

## Quick Review
- How does `map` differ from a list comprehension?
- What is the purpose of the initializer in `reduce`?

---