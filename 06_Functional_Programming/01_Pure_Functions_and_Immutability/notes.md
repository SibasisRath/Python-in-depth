# Pure Functions and Immutability

## Explanation

Functional programming emphasizes functions that have no side effects and always produce the same output given the same inputs. These are called **pure functions**. Immutability means data structures are not modified after creation; instead, new versions are returned.

Benefits:
- Easier to reason about and debug
- Safer for concurrent programming
- Enables memoization and caching

In Python, tuples and namedtuples are immutable; lists and dicts are mutable. We can write functions that avoid mutating their arguments.

## Examples

### Pure function
```python
def add(a, b):
    return a + b

print(add(2, 3))  # 5
```

### Avoiding mutation
```python
def append_item(lst, item):
    return lst + [item]  # returns new list, original unchanged

original = [1, 2]
new = append_item(original, 3)
print(original)  # [1, 2]
print(new)       # [1, 2, 3]
```

## Tasks

### Beginner
1. Write a pure function that computes the square of a number.
2. Create a tuple and demonstrate that assigning to an index raises an error.
3. Given a list, return a sorted copy without modifying the original list.

### Intermediate
1. Implement a function that returns a new dict with an added key-value pair without altering the input.
2. Write a function that takes a string and returns the same string reversed without using list mutation.

### Advanced
1. Build a memoized Fibonacci calculator without using decorators.
2. Design a function that takes a nested list and returns a deep-copied version with all elements incremented by 1.

## Quick Review
- What makes a function "pure"?
- Why is immutability valuable in multi-threaded programs?

---