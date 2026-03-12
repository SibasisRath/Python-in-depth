# Algorithms

## Explanation

Algorithms are step-by-step procedures for solving problems. Key families include:

- **Sorting algorithms**: arrange items in order (e.g., bubble sort, merge sort, quick sort).
- **Searching algorithms**: find elements within a dataset (linear search, binary search).
- **Recursion and backtracking**: solving problems by breaking them into smaller instances of the same problem.
- **Dynamic programming**: optimizing recursive solutions by caching results (memoization/table filling).
- **Greedy algorithms**: build a solution iteratively by making the best immediate choice.
- **Graph algorithms**: traverse or compute properties over graph structures (DFS, BFS, shortest paths).
- **Complexity analysis**: use Big-O notation to measure time and space requirements.

Understanding these will help you design efficient solutions in real-world coding and interviews.

## Examples

### Bubble sort
```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j+1]:
                arr[j], arr[j+1] = arr[j+1], arr[j]

nums = [5, 3, 8, 4, 2]
bubble_sort(nums)
print(nums)  # [2, 3, 4, 5, 8]
```

### Binary search (requires sorted list)
```python
def binary_search(arr, target):
    low, high = 0, len(arr) - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1
    return -1

print(binary_search([1, 2, 3, 4, 5], 3))  # 2
```

### Recursive Fibonacci with memoization
```python
from functools import lru_cache

@lru_cache(None)
def fib(n):
    if n < 2:
        return n
    return fib(n-1) + fib(n-2)

print(fib(10))  # 55
```

### BFS on a graph represented by adjacency list
```python
def bfs(start, graph):
    visited = set()
    queue = [start]
    order = []
    while queue:
        node = queue.pop(0)
        if node not in visited:
            visited.add(node)
            order.append(node)
            queue.extend(graph.get(node, []))
    return order

graph = {'A': ['B', 'C'], 'B': ['D'], 'C': ['E']}
print(bfs('A', graph))  # ['A', 'B', 'C', 'D', 'E']
```

## Tasks

### Beginner
1. Implement selection sort and test it on a list of numbers.
2. Write a function to perform linear search on an unsorted list.
3. Given a recursive definition, trace and print values for `factorial(n)`.

### Intermediate
1. Compare the runtime of bubble sort vs. merge sort on random data (you can use `time` module).
2. Write a recursive backtracking solution to solve the N‑Queens problem for small N.
3. Implement dynamic programming to compute the longest common subsequence (LCS) of two strings.

### Advanced
1. Implement Dijkstra's algorithm for shortest paths (without heap optimization first).
2. Write a function using bit manipulation to count the number of 1‑bits in an integer.
3. Solve a complex competitive programming problem that requires greedy + DP combination (e.g., coin change with limited coins).

## Quick Review
- Why does binary search require a sorted array?
- What is the difference between a greedy algorithm and dynamic programming?
- What does Big‑O notation describe?
- Explain how memoization changes the complexity of a recursive solution.

---

These algorithmic patterns will be reused when we implement advanced data structures and solve real problems.