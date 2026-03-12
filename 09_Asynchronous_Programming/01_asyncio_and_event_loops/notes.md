# asyncio and Event Loops

## Explanation

`asyncio` is Python’s standard library for writing single-threaded concurrent code using coroutines. The **event loop** schedules and runs these coroutines, handling I/O and other awaitable tasks.

Key concepts:
- Event loop creation (`asyncio.get_event_loop()`, `asyncio.run()`).
- Tasks, futures, and callbacks.
- I/O bound concurrency without threading.

`asyncio` is the backbone of modern async frameworks such as FastAPI and aiohttp.

## Examples

### Basic coroutine and event loop
```python
import asyncio

async def say(what, when):
    await asyncio.sleep(when)
    print(what)

async def main():
    await asyncio.gather(say('hello', 1), say('world', 2))

asyncio.run(main())
```

### Running callbacks on the loop
```python
loop = asyncio.get_event_loop()
loop.call_later(1, lambda: print('later'))
loop.run_until_complete(asyncio.sleep(2))
```

## Tasks

### Beginner
1. Write several `async` functions and run them concurrently with `asyncio.gather`.
2. Use `asyncio.sleep` to simulate I/O and observe order of execution.

### Intermediate
1. Create an event loop manually and schedule tasks with `create_task`.
2. Set up a periodic callback using `call_later` or `call_at`.

### Advanced
1. Implement a simple TCP echo server using `asyncio` streams.
2. Profile an `asyncio` program with many tasks and determine where time is spent.

## Quick Review
- What is the role of the event loop in `asyncio`?
- How do you schedule a coroutine to run later on the loop?

---