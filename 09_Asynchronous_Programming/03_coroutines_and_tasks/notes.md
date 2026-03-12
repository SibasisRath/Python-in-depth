# Coroutines and Tasks

## Explanation

A **coroutine** is a special function defined with `async def`. It returns a coroutine object when called and only executes when awaited or scheduled as a task.  
A **task** wraps a coroutine and schedules it on the event loop; tasks are a subclass of `asyncio.Future`.

Tasks allow concurrent execution and can be created with `asyncio.create_task()` or `loop.create_task()`.

## Examples

### Creating tasks
```python
async def count():
    for i in range(3):
        print(i)
        await asyncio.sleep(0.5)

async def main():
    task1 = asyncio.create_task(count())
    task2 = asyncio.create_task(count())
    await task1
    await task2

asyncio.run(main())
```

### Cancelling tasks
```python
task = asyncio.create_task(count())
await asyncio.sleep(1)
task.cancel()
try:
    await task
except asyncio.CancelledError:
    print('Task was cancelled')
```

## Tasks

### Beginner
1. Create two coroutines and schedule them as tasks to run concurrently.
2. Cancel a task after a short delay and handle the cancellation exception.

### Intermediate
1. Use `asyncio.wait` and `asyncio.as_completed` to handle multiple tasks.
2. Monitor task status with `task.done()` and `task.result()`.

### Advanced
1. Implement a supervisor coroutine that restarts failed tasks automatically.
2. Explore how tasks are cleaned up when the event loop is closed.

## Quick Review
- What’s the difference between a coroutine and a task?
- How do you cancel a running task and handle the result?

---