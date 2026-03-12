# ORM and Database Abstraction

## Explanation

Object-Relational Mappers (ORMs) let you work with databases using Python classes instead of raw SQL. They handle query generation, schema migrations, and help prevent SQL injection.

Main topics:

- **Django ORM**: built into Django; uses model classes, querysets, and manager methods. Supports advanced features like select_related, prefetch_related, and custom managers.
- **SQLAlchemy**: a flexible ORM and SQL toolkit. You can work with the `Core` layer (SQL expressions) or the `ORM` layer (mapped classes). It also provides connection pooling, migrations via Alembic, and more.
- **Migrations**: tools to evolve database schema over time (`django migrations`, `alembic` for SQLAlchemy).

Using ORMs simplifies development but understanding the generated SQL and performance implications is important.

## Examples

### Django ORM example
```python
# models.py
from django.db import models

class Author(models.Model):
    name = models.CharField(max_length=100)

class Book(models.Model):
    title = models.CharField(max_length=100)
    author = models.ForeignKey(Author, on_delete=models.CASCADE)

# usage in Django shell
>>> Author.objects.create(name='Jane Austen')
>>> Book.objects.filter(author__name='Jane Austen')
```

### SQLAlchemy example
```python
from sqlalchemy import Column, Integer, String, ForeignKey, create_engine
from sqlalchemy.orm import declarative_base, relationship, sessionmaker

Base = declarative_base()

class Author(Base):
    __tablename__ = 'authors'
    id = Column(Integer, primary_key=True)
    name = Column(String)
    books = relationship('Book', back_populates='author')

class Book(Base):
    __tablename__ = 'books'
    id = Column(Integer, primary_key=True)
    title = Column(String)
    author_id = Column(Integer, ForeignKey('authors.id'))
    author = relationship('Author', back_populates='books')

engine = create_engine('sqlite:///:memory:')
Base.metadata.create_all(engine)
Session = sessionmaker(bind=engine)
session = Session()

session.add(Author(name='Mark Twain'))
session.commit()
```

## Tasks

### Beginner
1. Create a simple Django model and retrieve records using the shell.
2. Define SQLAlchemy models for a small database and perform basic CRUD with a session.

### Intermediate
1. Explore complex queries in Django ORM (e.g., annotate, aggregate).
2. Use SQLAlchemy’s Core layer to write a custom SQL expression and execute it.

### Advanced
1. Write a raw SQL query in Django and compare performance to the ORM equivalent.
2. Set up Alembic migrations for a SQLAlchemy project and apply versioned schema changes.

## Quick Review
- What does a queryset represent in Django?
- How do you create a one-to-many relationship using SQLAlchemy?
- Why are migrations necessary, and how do ORMs help manage them?

---