# Django Framework

## Explanation

Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design. Key components include:

- **Project structure**: `manage.py`, settings.py, apps, `urls.py`.
- **Models and ORM**: define data models as Python classes; Django handles database queries behind the scenes.
- **Views and URL routing**: functions or classes that process requests and return responses; routing defined in `urls.py`.
- **Templates**: HTML templates with Django’s templating language and inheritance.
- **Forms and validation**: form classes for input handling and validation.
- **Authentication and authorization**: built-in user model, login/logout, permissions.
- **Admin interface**: auto-generated admin dashboard for models.
- **Middleware and request/response cycle**: hooks for processing requests/responses globally.
- **Static files and media**: serving CSS, JS, user-uploaded files.
- **Django REST Framework (DRF)**: toolkit for building web APIs with serializers, viewsets.
- **Class-based views**, **signals**, **custom management commands**, **testing**, and **deployment settings** are all advanced features.

## Examples

### Creating a model
```python
from django.db import models

class Book(models.Model):
    title = models.CharField(max_length=100)
    author = models.CharField(max_length=100)
    published = models.DateField()

    def __str__(self):
        return self.title
```

### URL pattern and view
```python
# urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('', views.home, name='home'),
]

# views.py
from django.http import HttpResponse

def home(request):
    return HttpResponse('Hello, Django!')
```

### DRF serializer
```python
from rest_framework import serializers
from .models import Book

class BookSerializer(serializers.ModelSerializer):
    class Meta:
        model = Book
        fields = '__all__'
```

## Tasks

### Beginner
1. Start a new Django project (`django-admin startproject`) and create a simple app.
2. Define a model and run migrations to create the corresponding database table.
3. Create a basic view that returns "Hello, world!" and wire it to a URL.

### Intermediate
1. Build a form for creating and editing objects of a model, including validation.
2. Customize the Django admin to display additional fields or filters for a model.
3. Use class-based views (ListView, DetailView) for standard CRUD operations.

### Advanced
1. Build a REST API using Django REST Framework with viewsets and routers.
2. Implement custom middleware that logs request/response times.
3. Deploy a Django app to a cloud provider (Heroku, AWS, GCP) with production settings.

## Quick Review
- How does Django’s ORM translate queries into SQL?
- What is the purpose of the `urlpatterns` list?
- Describe the difference between function-based and class-based views.

---