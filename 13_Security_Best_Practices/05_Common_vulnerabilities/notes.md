# Common Vulnerabilities (XSS, CSRF, SQL Injection)

## Explanation

Common web vulnerabilities exploit poor input handling. XSS injects malicious scripts; CSRF tricks users into unwanted actions; SQL injection manipulates database queries. Prevent with input validation, parameterized queries, and security headers. Use OWASP guidelines for best practices.

Key vulnerabilities:
- XSS: reflected, stored, DOM-based
- CSRF: cross-site request forgery
- SQL injection: union-based, blind
- Prevention: prepared statements, CSP, CSRF tokens

## Examples

Preventing SQL injection:
```python
import sqlite3

# Unsafe
cursor.execute(f"SELECT * FROM users WHERE id = {user_id}")

# Safe
cursor.execute("SELECT * FROM users WHERE id = ?", (user_id,))
```

Preventing XSS in HTML:
```python
from html import escape

user_input = "<script>alert('xss')</script>"
safe_output = f"<p>{escape(user_input)}</p>"
```

## Tasks

### Beginner
1. Demonstrate SQL injection vulnerability and fix it with parameterized queries.
2. Sanitize user input for HTML output.

### Intermediate
1. Implement CSRF protection in a web form using tokens.
2. Test for XSS in a simple web app.

### Advanced
1. Set up Content Security Policy (CSP) headers.
2. Perform a security audit on a sample application.

## Quick Review
- What is the primary way to prevent SQL injection?
- How does CSRF differ from XSS?
