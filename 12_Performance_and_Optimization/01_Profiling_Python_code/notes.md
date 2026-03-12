# Profiling Python Code (cProfile, line_profiler)

## Explanation

Profiling identifies performance bottlenecks in code. `cProfile` is Python's built-in profiler, measuring function call counts and times. `line_profiler` provides line-by-line timing for detailed analysis. Use profiling to focus optimizations on slow parts, avoiding premature optimization.

Key tools:
- `cProfile.run()` or `python -m cProfile script.py`
- `pstats` module for analyzing output
- `line_profiler` decorator `@profile` for per-line stats

## Examples

```python
import cProfile

def slow_function():
    return sum(i**2 for i in range(10000))

cProfile.run('slow_function()')
```

For line_profiler:
```bash
pip install line_profiler
```

```python
from line_profiler import LineProfiler

@profile
def my_func():
    a = [i for i in range(1000)]
    return sum(a)

lp = LineProfiler()
lp.add_function(my_func)
lp.run('my_func()')
lp.print_stats()
```

## Tasks

### Beginner
1. Profile a simple script with `cProfile` and identify the slowest function.
2. Use `pstats` to sort output by cumulative time.

### Intermediate
1. Apply `@profile` to a function and analyze line-by-line output.
2. Compare profiling results before and after a small optimization.

### Advanced
1. Profile a multi-threaded program and interpret the results.
2. Integrate profiling into a test suite to catch regressions.

## Quick Review
- What does `cProfile` measure by default?
- How do you enable line-by-line profiling with `line_profiler`?
