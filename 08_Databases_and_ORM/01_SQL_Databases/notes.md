# SQL Databases

## Explanation

SQL (Structured Query Language) is used to interact with relational databases. Core topics include:

- **Basic queries**: `SELECT`, `INSERT`, `UPDATE`, `DELETE`.
- **Filtering and sorting**: `WHERE`, `ORDER BY`, `LIMIT`.
- **Joins**: `INNER JOIN`, `LEFT/RIGHT OUTER JOIN`, cross joins.
- **Aggregation**: `GROUP BY`, `HAVING`, functions like `COUNT`, `SUM`, `AVG`.
- **Database design**: tables, primary/foreign keys, normalization (1NF, 2NF, 3NF).
- **Transactions and connection pooling**: `BEGIN`, `COMMIT`, `ROLLBACK`; using pools for efficiency.
- **Security**: preventing SQL injection via parameterized queries and ORM abstractions.

Python connectors (e.g., `psycopg2` for PostgreSQL, `mysql-connector-python` for MySQL) allow running SQL from code. Other tools like `sqlite3` are included in the standard library for lightweight storage.

## Examples

### SQLite example (built-in)
```python
import sqlite3

conn = sqlite3.connect(':memory:')
c = conn.cursor()
c.execute('CREATE TABLE users (id INTEGER PRIMARY KEY, name TEXT)')
c.execute('INSERT INTO users (name) VALUES (?)', ('Alice',))
conn.commit()
c.execute('SELECT * FROM users')
print(c.fetchall())  # [(1, 'Alice')]
conn.close()
```

### Parameterized query (to avoid injection)
```python
user_input = "Robert'); DROP TABLE users; --"
c.execute('SELECT * FROM users WHERE name = ?', (user_input,))
```

## Tasks

### Beginner
1. Install SQLite3 (if not present) and practice creating a table, inserting rows, and querying data.
2. Write queries that use `WHERE` and `ORDER BY` on a sample dataset.

### Intermediate
1. Design a normalized schema for a blog (posts, authors, comments) and create it in a database.
2. Use `psycopg2` or `mysql-connector-python` to connect to a local PostgreSQL/MySQL instance and execute CRUD operations.
3. Demonstrate a transaction by performing multiple updates and rolling back on error.

### Advanced
1. Experiment with connection pooling libraries (e.g., SQLAlchemy’s pool) and benchmark query throughput.
2. Analyze query plans (e.g., `EXPLAIN` output) to optimize joins and indexes.
3. Implement a small web app (e.g., Flask or FastAPI) that performs database operations securely.

## Quick Review
- What’s the difference between `INNER JOIN` and `LEFT JOIN`?
- Why are parameterized queries important for security?
- Explain normalization and why it’s useful.

---