# Cython for Performance-Critical Code

## Explanation

Cython compiles Python-like code to C extensions, boosting performance for CPU-bound tasks. It allows static typing and direct C calls. Use for bottlenecks identified by profiling; not for I/O-bound code.

Key features:
- `.pyx` files with type annotations
- `cython` command to generate C code
- Integration with `setup.py` for building

## Examples

`example.pyx`:
```cython
def fib(int n):
    cdef int a = 0, b = 1
    cdef int i
    for i in range(n):
        a, b = b, a + b
    return a
```

`setup.py`:
```python
from setuptools import setup
from Cython.Build import cythonize

setup(ext_modules=cythonize("example.pyx"))
```

Build: `python setup.py build_ext --inplace`

## Tasks

### Beginner
1. Convert a pure Python function to Cython and compare speeds.
2. Add basic type declarations and rebuild.

### Intermediate
1. Use Cython to wrap a C library function.
2. Profile before/after Cython optimization.

### Advanced
1. Implement parallel processing with Cython and OpenMP.
2. Create a Cython extension with custom C code.

## Quick Review
- What file extension does Cython use?
- When should you use Cython over pure Python?
