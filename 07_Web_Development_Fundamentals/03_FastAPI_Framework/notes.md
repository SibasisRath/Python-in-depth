# FastAPI Framework

## Explanation

FastAPI is a modern, fast (high-performance) web framework for building APIs with Python 3.7+ based on standard Python type hints. Features include:

- Automatic interactive API documentation (Swagger UI, ReDoc)
- Asynchronous support using `async`/`await`
- Data validation with Pydantic models
- Dependency injection system
- Designed for production performance (Starlette / Uvicorn under the hood)

FastAPI is ideal for building lightweight APIs and microservices.

## Examples

### Basic FastAPI app
```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"hello": "world"}

@app.get("/items/{item_id}")
def read_item(item_id: int, q: str | None = None):
    return {"item_id": item_id, "q": q}
```

Run the server with:
```
uvicorn main:app --reload
```

### Pydantic model for request body
```python
from pydantic import BaseModel

class Item(BaseModel):
    name: str
    price: float
    is_offer: bool | None = None

@app.post("/items/")
def create_item(item: Item):
    return item
```

### Async endpoint example
```python
@app.get("/slow")
async def slow():
    import asyncio
    await asyncio.sleep(1)
    return {"message": "done"}
```

## Tasks

### Beginner
1. Install FastAPI and Uvicorn; create and run the "hello world" app above.
2. Explore the automatically generated Swagger UI by visiting `/docs`.
3. Define a Pydantic model and POST JSON data to your API.

### Intermediate
1. Add path and query parameter validation using types and regex.
2. Implement dependency injection for a simple authentication scheme.
3. Create background tasks with FastAPI’s `BackgroundTasks` utility.

### Advanced
1. Build a complete CRUD API with database integration (e.g., SQLModel or SQLAlchemy).
2. Use WebSockets to build a real-time chat endpoint.
3. Deploy a FastAPI app using Docker and a production server (Gunicorn/Uvicorn).

## Quick Review
- What are the benefits of using type hints in FastAPI?
- How does FastAPI generate API documentation automatically?
- When would you write an async endpoint versus a regular def?

---