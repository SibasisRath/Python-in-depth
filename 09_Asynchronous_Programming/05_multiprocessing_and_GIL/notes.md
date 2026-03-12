# Multiprocessing and the GIL

## Explanation

Python’s Global Interpreter Lock (GIL) ensures that only one native thread executes Python bytecode at a time, which can limit CPU-bound concurrency in threads. The `multiprocessing` module sidesteps the GIL by running separate Python processes, each with its own interpreter.

Key points:
- **Processes** vs **threads**
- `multiprocessing.Pool` for parallel execution
- Shared memory and inter-process communication (`Queue`, `Pipe`, `Manager`)
- Overhead of process creation and data serialization (pickling)
- Impact of the GIL on multi-threaded programs

## Examples

### Using a process pool
```python
from multiprocessing import Pool

def f(x):
    return x*x

with Pool(4) as p:
    print(p.map(f, [1, 2, 3, 4]))
```

### Shared state with Manager
```python
from multiprocessing import Manager, Process

def worker(d, key, value):
    d[key] = value

if __name__ == '__main__':
    manager = Manager()
    shared_dict = manager.dict()
    processes = [Process(target=worker, args=(shared_dict, i, i*i)) for i in range(4)]
    for proc in processes:
        proc.start()
    for proc in processes:
        proc.join()
    print(shared_dict)
```

## Tasks

### Beginner
1. Write a script that uses `multiprocessing.Process` to perform simple work in parallel.
2. Demonstrate the effect of GIL by running CPU-bound loops in multiple threads vs processes.

### Intermediate
1. Use a `Pool` to perform a map-reduce style computation.
2. Share a counter between processes using a `Value` or through a `Manager`.

### Advanced
1. Measure overhead of inter-process communication vs threading.
2. Explore alternatives like `multiprocessing.dummy` (thread-based API) and compare to `threading`.

## Quick Review
- Why does the GIL restrict multi-threaded Python programs?
- How does `multiprocessing` overcome the GIL?

---