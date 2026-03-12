# Input Validation and Sanitization

## Explanation

Input validation ensures data meets expected criteria before processing; sanitization cleans potentially harmful data. Use libraries like `marshmallow` or `pydantic` for structured validation. Always validate on server-side; client-side is for UX. Common issues: SQL injection, XSS, command injection.

Key practices:
- Whitelist allowed inputs over blacklist
- Use parameterized queries for databases
- Escape output for HTML contexts
- Validate data types and ranges

## Examples

Using pydantic:
```python
from pydantic import BaseModel, ValidationError

class User(BaseModel):
    name: str
    age: int

try:
    user = User(name="Alice", age=30)
    print(user)
except ValidationError as e:
    print(e)
```

Manual validation:
```python
def validate_email(email):
    import re
    pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
    return bool(re.match(pattern, email))
```

## Tasks

### Beginner
1. Write a function to validate a phone number using regex.
2. Use pydantic to validate a simple form with required fields.

### Intermediate
1. Implement input sanitization for HTML content using `html.escape()`.
2. Create a custom validator for password strength.

### Advanced
1. Build a validation pipeline for API endpoints using FastAPI/Pydantic.
2. Handle file uploads with validation for type, size, and content.

## Quick Review
- Why is server-side validation essential?
- What is the difference between validation and sanitization?
