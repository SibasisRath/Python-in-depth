# Threading and Multiprocessing

## Explanation

Threading allows concurrent execution of multiple threads in a single process; multiprocessing uses separate processes to bypass the GIL. Use threading for I/O-bound tasks (network, file I/O); use multiprocessing for CPU-bound work. The `threading` and `multiprocessing` modules provide tools; synchronization primitives (Lock, Condition, Queue) prevent race conditions.

Key concepts:
- Threads share memory; processes have isolated heaps
- GIL limits Python threads for CPU-bound work
- Race conditions and synchronization
- Deadlock prevention

## Examples

```python
import threading

def worker(name):
    print(f"Worker {name}")

thread = threading.Thread(target=worker, args=("A",))
thread.start()
thread.join()
```

Multiprocessing:
```python
from multiprocessing import Process

def worker():
    print("Process")

p = Process(target=worker)
p.start()
p.join()
```

## Tasks

### Beginner
1. Create and start a thread; use `join()` to wait for completion.
2. Demonstrate a simple multiprocessing example.

### Intermediate
1. Use locks to prevent race conditions in shared state.
2. Create a thread pool with `concurrent.futures.ThreadPoolExecutor`.

### Advanced
1. Implement a producer-consumer pattern with queues.
2. Compare threading and multiprocessing performance on I/O vs CPU tasks.

## Quick Review
- Why can't threading improve CPU-bound performance in Python?
- What synchronization primitive prevents race conditions?
