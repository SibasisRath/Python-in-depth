# `async`/`await` Syntax

## Explanation

Python 3.5 introduced the `async` and `await` keywords to define asynchronous coroutines more cleanly. An `async def` function returns a coroutine object; `await` pauses execution until the awaited object is complete.

The syntax resembles synchronous code, making asynchronous logic easier to write and read.

## Examples

### Basic usage
```python
async def fetch_data():
    await asyncio.sleep(1)
    return 'data'

async def main():
    result = await fetch_data()
    print(result)

asyncio.run(main())
```

### Mixing synchronous and asynchronous
```python
def sync_func():
    return 'sync'

async def async_wrapper():
    print(sync_func())
    await asyncio.sleep(0)
```

## Tasks

### Beginner
1. Rewrite a synchronous function into async by adding `async` and using `await` on a dummy sleep.
2. Experiment with nesting `await` calls in multiple layers of coroutines.

### Intermediate
1. Understand `await` on non-coroutine awaitables like `asyncio.Future` or `asyncio.Task`.
2. Use `async`/`await` in list comprehensions with `asyncio.gather`.

### Advanced
1. Read the Python bytecode of an `async` function (`dis` module) to see how it differs from a regular function.
2. Implement a custom awaitable object by defining `__await__`.

## Quick Review
- What does `async def` return when called?
- Why can't you use `await` at the top level in normal code (outside a coroutine)?

---