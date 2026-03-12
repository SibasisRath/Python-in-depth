# JWT Tokens and Authentication

## Explanation

JSON Web Tokens (JWT) are compact, self-contained tokens for authentication. They consist of header, payload, and signature. Use for stateless auth in APIs; store sensitive data in payload but avoid secrets. Libraries like `PyJWT` handle encoding/decoding. Implement refresh tokens for security.

Key components:
- Header: algorithm and token type
- Payload: claims (user ID, expiration)
- Signature: verifies integrity
- Expiration and issuer claims

## Examples

Using PyJWT:
```python
import jwt
from datetime import datetime, timedelta

# Create token
payload = {
    'user_id': 123,
    'exp': datetime.utcnow() + timedelta(hours=1)
}
token = jwt.encode(payload, 'secret', algorithm='HS256')

# Decode
decoded = jwt.decode(token, 'secret', algorithms=['HS256'])
print(decoded['user_id'])
```

## Tasks

### Beginner
1. Generate a JWT with basic payload and decode it.
2. Handle JWT expiration by catching exceptions.

### Intermediate
1. Implement JWT-based login in a Flask/FastAPI app.
2. Add role-based access control using JWT claims.

### Advanced
1. Implement refresh tokens to handle token expiration.
2. Secure JWTs with asymmetric keys (RS256).

## Quick Review
- What are the three parts of a JWT?
- Why should JWTs have an expiration time?
