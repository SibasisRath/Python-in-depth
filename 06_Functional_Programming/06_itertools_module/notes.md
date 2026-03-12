# `itertools` Module

## Explanation

The `itertools` module offers a collection of fast, memory-efficient tools for working with iterators. It includes functions for creating and combining iterators, such as:

- `count()`, `cycle()`, `repeat()` for infinite iterators
- `chain()`, `zip_longest()` for combining iterables
- `islice()` for slicing iterators
- `combinations()`, `permutations()`, `product()` for combinatorial iterators
- `groupby()` for grouping consecutive keys

These utilities are invaluable when processing large datasets or building complex iterator pipelines in a functional style.

## Examples

```python
import itertools

# infinite count
for i in itertools.count(5):
    if i > 8:
        break
    print(i)

# combining iterables
for x in itertools.chain([1,2], ['a','b']):
    print(x)

# combinatorics
print(list(itertools.combinations('ABC', 2)))
# [('A','B'), ('A','C'), ('B','C')]

# slicing
print(list(itertools.islice(range(10), 2, 5)))
# [2, 3, 4]
```

## Tasks

### Beginner
1. Use `count()` and `zip()` to pair indices with values from a list.
2. Generate all 2‑letter permutations of `['x','y','z']`.

### Intermediate
1. Write a function that groups consecutive identical elements using `groupby()`.
2. Create an iterator pipeline that filters, maps, and accumulates values from a large range.

### Advanced
1. Implement a Sudoku solver using `itertools.product` to try combinations.
2. Develop a custom iterator that interleaves multiple input iterators (`round-robin` fashion).

## Quick Review
- Which `itertools` functions produce infinite iterators?
- How does `islice` differ from normal slicing?

---