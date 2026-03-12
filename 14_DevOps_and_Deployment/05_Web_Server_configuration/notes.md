# Web Server Configuration (Nginx/Gunicorn/Uvicorn)

## Explanation

For deploying Python web applications, a common pattern uses a reverse proxy/web server (Nginx) in front of an application server like Gunicorn (for WSGI) or Uvicorn (for ASGI/FastAPI).

- **Nginx**: handles static files, SSL termination, load balancing, and can proxy requests to backend servers.
- **Gunicorn**: WSGI HTTP server for synchronous frameworks like Django.
- **Uvicorn**: ASGI server for asynchronous frameworks like FastAPI.

Configuration includes setting worker counts, timeouts, and binding to sockets.

## Examples

### Nginx config snippet
```
server {
    listen 80;
    server_name example.com;

    location /static/ {
        alias /path/to/static/;
    }

    location / {
        proxy_pass http://127.0.0.1:8000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```

### Gunicorn command
```
gunicorn myproject.wsgi:application --workers 3 --bind 127.0.0.1:8000
```

### Uvicorn command for FastAPI
```
uvicorn main:app --host 0.0.0.0 --port 8000 --workers 4
```

## Tasks

### Beginner
1. Install Nginx locally and configure it to proxy to a simple Flask app.
2. Run Gunicorn with a Django project and verify it serves requests.

### Intermediate
1. Set up HTTPS with Let’s Encrypt certificates in Nginx config.
2. Configure Nginx to serve both static and media files efficiently.

### Advanced
1. Use Nginx load balancing across multiple Gunicorn/Uvicorn workers or servers.
2. Benchmark different worker classes (`sync`, `gevent`, etc.) and tune for performance.

## Quick Review
- What role does Nginx play in a typical Python web deployment?
- How do Gunicorn and Uvicorn differ, and when would you use each?

---