# Generator Expressions and `yield`

## Explanation

Generator expressions are similar to list comprehensions but use parentheses and produce a generator instead of a list. They yield items one at a time, which saves memory.

The `yield` keyword inside a function turns it into a generator, allowing the function to produce a sequence of values over time.

## Examples

### Generator expression
```python
squares = (x*x for x in range(5))
print(next(squares))  # 0
print(list(squares))  # [1, 4, 9, 16]
```

### Using `yield`
```python
def countdown(n):
    while n > 0:
        yield n
        n -= 1

for num in countdown(3):
    print(num)
# 3 2 1
```

## Tasks

### Beginner
1. Create a generator expression to compute even numbers up to 20.
2. Convert a generator expression to a list and observe the memory usage difference.

### Intermediate
1. Write a function with `yield` that generates prime numbers indefinitely.
2. Use `yield from` to delegate to another generator.

### Advanced
1. Compare performance and memory of a generator expression vs. a list comprehension on a large range.
2. Implement a coroutine that accumulates values sent to it via `send()`.

## Quick Review
- When should you prefer a generator expression over a list comprehension?
- What does `yield from` accomplish?

---