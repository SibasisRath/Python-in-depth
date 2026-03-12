# NoSQL Databases

## Explanation

NoSQL databases provide flexible schemas and scale horizontally. Common types include document stores, key-value stores, and column-family stores. Python interfaces exist for many of them.

This section focuses on:

- **MongoDB**: a document database storing JSON-like objects. The PyMongo driver is commonly used.
- **Redis**: an in-memory key-value store often used for caching, pub/sub, and simple data structures.
- **Differences from relational**: schema-less, eventual consistency, horizontal scaling.

Understanding when to choose NoSQL vs. SQL is critical based on your data access patterns.

## Examples

### MongoDB using PyMongo
```python
from pymongo import MongoClient

client = MongoClient('mongodb://localhost:27017/')
db = client['testdb']
collection = db['people']

collection.insert_one({'name': 'Alice', 'age': 30})
print(collection.find_one({'name': 'Alice'}))
```

### Redis usage
```python
import redis

r = redis.Redis(host='localhost', port=6379, db=0)
r.set('foo', 'bar')
print(r.get('foo'))  # b'bar'
r.lpush('mylist', 1, 2, 3)
print(r.lrange('mylist', 0, -1))
```

## Tasks

### Beginner
1. Install MongoDB or run a Docker container, connect via PyMongo, and insert/retrieve documents.
2. Install Redis (or use a Docker container) and practice setting/getting keys and using a list.

### Intermediate
1. Model a simple catalog of products in MongoDB with nested documents and indexes.
2. Implement a caching layer for a Python function using Redis with expiration.

### Advanced
1. Compare performance of a read-heavy workload on MongoDB vs PostgreSQL for the same data.
2. Build a Pub/Sub notification system using Redis that notifies subscribers when data changes.

## Quick Review
- What are the trade-offs between a document store and a relational database?
- How does Redis achieve high performance?
- When would eventual consistency be acceptable, and when is it problematic?

---