# HTTPS and SSL/TLS

## Explanation

HTTPS encrypts HTTP traffic using SSL/TLS certificates. It protects against eavesdropping, tampering, and man-in-the-middle attacks. Use Let's Encrypt for free certificates; configure web servers (Nginx, Apache) for TLS 1.2+. In Python, use `ssl` module for custom connections; frameworks handle HTTPS automatically.

Key concepts:
- Certificate Authority (CA) validation
- TLS handshake process
- Mixed content issues
- HSTS (HTTP Strict Transport Security)

## Examples

Using requests with HTTPS:
```python
import requests

# Verify SSL certificate
response = requests.get('https://api.example.com', verify=True)
print(response.json())
```

Custom SSL context:
```python
import ssl
import socket

context = ssl.create_default_context()
with socket.create_connection(('example.com', 443)) as sock:
    with context.wrap_socket(sock, server_hostname='example.com') as ssock:
        print(ssock.version())
```

## Tasks

### Beginner
1. Make an HTTPS request with requests and inspect the certificate.
2. Test a site with SSL Labs to check TLS configuration.

### Intermediate
1. Configure a local server (Flask/Django) with self-signed certificates.
2. Handle SSL errors gracefully in your code.

### Advanced
1. Implement client certificate authentication.
2. Set up HSTS and certificate pinning.

## Quick Review
- What does HTTPS protect against that HTTP does not?
- Why is certificate validation important?
