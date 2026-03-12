# Async Database Operations

## Explanation

Asynchronous frameworks often need to perform database I/O without blocking the event loop. Many ORMs and drivers now offer async variants (e.g., `asyncpg` for PostgreSQL, `databases` library, or async ORM extensions like `SQLAlchemy 1.4+` with `asyncio`).

Key topics:
- Connecting to a database asynchronously
- Executing queries with `await`
- Working with async versions of ORMs or raw drivers
- Combining async database calls with web frameworks (FastAPI, aiohttp)

## Examples

### Using `asyncpg`
```python
import asyncio
import asyncpg

async def run():
    conn = await asyncpg.connect(user='user', password='pass', database='test', host='127.0.0.1')
    await conn.execute('CREATE TABLE IF NOT EXISTS items(id serial PRIMARY KEY, name text)')
    await conn.execute('INSERT INTO items(name) VALUES($1)', 'foo')
    rows = await conn.fetch('SELECT * FROM items')
    print(rows)
    await conn.close()

asyncio.run(run())
```

### Async SQLAlchemy example
```python
from sqlalchemy.ext.asyncio import create_async_engine, AsyncSession
from sqlalchemy.orm import sessionmaker

engine = create_async_engine('postgresql+asyncpg://user:pass@localhost/test')
AsyncSessionLocal = sessionmaker(engine, expire_on_commit=False, class_=AsyncSession)

async def get_items():
    async with AsyncSessionLocal() as session:
        result = await session.execute("SELECT * FROM items")
        return result.fetchall()
```

## Tasks

### Beginner
1. Install `asyncpg` and write a simple async script to create a table and query it.
2. Experiment with `await`-ing different query types (select vs insert).

### Intermediate
1. Integrate async database calls into a FastAPI endpoint.
2. Handle connection errors gracefully in async code with try/except/finally.

### Advanced
1. Benchmark async vs synchronous database access under concurrent load.
2. Explore how connection pooling works in async drivers and configure pool sizes.

## Quick Review
- Why is it important not to run blocking database calls in an event loop?
- Which libraries provide async database support in Python?

---