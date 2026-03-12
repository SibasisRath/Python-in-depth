# HTTP and Web Basics

## Explanation

This section covers the fundamentals of the web and the HTTP protocol:

- **HTTP methods**: GET, POST, PUT, DELETE, PATCH – actions clients request from servers.
- **Status codes**: 200 OK, 404 Not Found, 500 Internal Server Error, etc.
- **Headers**: metadata sent with requests and responses (Content-Type, Authorization).
- **RESTful API principles**: resources, statelessness, use of HTTP verbs.
- **JSON**: a common data interchange format used in APIs.
- **Cookies and sessions**: mechanisms for preserving state across requests.
- **CORS and security**: Cross-Origin Resource Sharing, same-origin policy, basic web security concerns.

Understanding these concepts is critical before jumping into frameworks like Django or FastAPI.

## Examples

### Simple HTTP request using `requests` library
```python
import requests

response = requests.get('https://httpbin.org/get')
print(response.status_code)
print(response.json())
```

### JSON response handling
```python
data = {'name': 'Alice', 'age': 30}
import json
serialized = json.dumps(data)
print(serialized)
print(json.loads(serialized))
```

### Basic Flask-like pseudo-server (for illustration only)
```python
from http.server import BaseHTTPRequestHandler, HTTPServer

class SimpleHandler(BaseHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.send_header('Content-type','text/html')
        self.end_headers()
        self.wfile.write(b"Hello, world!")

if __name__ == '__main__':
    server = HTTPServer(('localhost', 8000), SimpleHandler)
    print('Starting server on port 8000...')
    server.serve_forever()
```

## Tasks

### Beginner
1. Use `curl` or `httpie` to send a GET and POST request to httpbin.org and inspect the response.
2. Write a Python script that fetches JSON from an API and prints a specific field.

### Intermediate
1. Implement a small HTTP client using `socket` that performs a GET request to a server.
2. Simulate cookie handling by storing and sending headers manually with `requests.Session`.

### Advanced
1. Create a mock REST API specification and write tests that verify correct status codes and headers.
2. Research and document common security headers (e.g., `X-Content-Type-Options`) and implement them in a simple server.

## Quick Review
- What is the difference between PUT and PATCH?
- Explain how cookies and sessions differ in tracking user state.
- Why are CORS restrictions in place and how can you permit cross-origin requests?

---