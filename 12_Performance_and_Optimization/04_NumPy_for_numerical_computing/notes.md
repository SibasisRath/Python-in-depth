# NumPy for Numerical Computing

## Explanation

NumPy provides efficient arrays and mathematical operations for numerical data. Its `ndarray` is faster than Python lists for vectorized operations. Use for scientific computing, data analysis, and performance-critical math. Key features: broadcasting, universal functions (ufuncs), and integration with other libraries.

Key concepts:
- `numpy.array()` for creating arrays
- Vectorized operations (no explicit loops)
- Broadcasting for shape-compatible operations
- Indexing, slicing, and reshaping

## Examples

```python
import numpy as np

# Create arrays
a = np.array([1, 2, 3])
b = np.array([[1, 2], [3, 4]])

# Vectorized operations
c = a * 2  # [2, 4, 6]
d = np.dot(a, a)  # 14

# Broadcasting
e = a + np.array([[1], [2], [3]])  # Adds column-wise
```

## Tasks

### Beginner
1. Create a 1D and 2D NumPy array and perform basic arithmetic.
2. Use `np.arange()` and `np.linspace()` to generate sequences.

### Intermediate
1. Implement matrix multiplication using NumPy and compare to nested loops.
2. Use broadcasting to add a vector to each row of a matrix.

### Advanced
1. Optimize a numerical algorithm (e.g., Monte Carlo simulation) using NumPy.
2. Explore advanced indexing with boolean masks and fancy indexing.

## Quick Review
- What is the main advantage of NumPy arrays over Python lists?
- How does broadcasting work in NumPy?
