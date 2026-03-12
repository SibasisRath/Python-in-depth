# `concurrent.futures` for Threading

## Explanation

The `concurrent.futures` module provides a high-level interface for asynchronously executing callables using threads or processes. The `ThreadPoolExecutor` uses a pool of threads; tasks are submitted and results retrieved via `Future` objects.

This is useful for I/O-bound work when you need to run blocking operations concurrently but want a simpler API than managing threads manually.

## Examples

```python
from concurrent.futures import ThreadPoolExecutor

import time

def blocking_io(n):
    time.sleep(n)
    return n

with ThreadPoolExecutor(max_workers=3) as executor:
    futures = [executor.submit(blocking_io, i) for i in range(3)]
    for future in futures:
        print(future.result())
``` 

## Tasks

### Beginner
1. Use `ThreadPoolExecutor` to run a blocking I/O function several times concurrently.
2. Experiment with `max_workers` and observe CPU utilization.

### Intermediate
1. Use `as_completed` to process futures as they complete.
2. Combine `ThreadPoolExecutor` with `asyncio` using `run_in_executor`.

### Advanced
1. Compare performance of thread vs process executors on CPU-bound tasks.
2. Implement a custom executor by subclassing `ThreadPoolExecutor`.

## Quick Review
- When should you use `ThreadPoolExecutor` vs `ProcessPoolExecutor`?
- How do `Future` objects signal completion?

---