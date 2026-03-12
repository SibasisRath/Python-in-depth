# Docker Containerization

## Explanation

Docker allows you to package applications and their dependencies into containers that run consistently across environments. Key concepts:

- **Images vs Containers**: images are templates; containers are running instances.
- **Dockerfile**: declarative file specifying how to build an image.
- **Volumes**: for persisting data outside containers.
- **Networking**: linking containers, exposing ports.
- **Best practices**: small images, multi-stage builds, avoiding root.

In Python projects, you typically build images that install requirements and run your app with a WSGI/ASGI server.

## Examples

### Sample Dockerfile for a Django app
```Dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt ./
RUN pip install -r requirements.txt
COPY . .
CMD ["gunicorn", "myproject.wsgi:application", "--bind", "0.0.0.0:8000"]
```

### Running with Docker Compose
```yaml
version: '3'
services:
  web:
    build: .
    ports:
      - "8000:8000"
    volumes:
      - .:/app
  db:
    image: postgres:14
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: pass
```

## Tasks

### Beginner
1. Install Docker and run `docker run hello-world` to verify setup.
2. Write a simple Dockerfile for a Python script and build/run it.

### Intermediate
1. Use a multi-stage build to reduce image size.
2. Add a non-root user and switch to it in your Dockerfile.

### Advanced
1. Integrate Docker builds into CI pipelines with caching.
2. Use Docker security scanning tools to inspect your images.

## Quick Review
- What’s the difference between `docker build` and `docker run`?
- Why are multi-stage builds beneficial?

---