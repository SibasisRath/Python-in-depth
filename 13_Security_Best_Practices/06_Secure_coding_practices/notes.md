# Secure Coding Practices

## Explanation

Secure coding involves defensive programming to minimize vulnerabilities. Follow principles like least privilege, fail-safe defaults, and secure defaults. Use tools like `bandit` for static analysis; keep dependencies updated. Regularly audit code and handle errors securely (no sensitive info in exceptions).

Key practices:
- Input validation and output encoding
- Secure configuration management
- Error handling without information leakage
- Dependency scanning and updates
- Principle of least privilege

## Examples

Using bandit for security linting:
```bash
pip install bandit
bandit -r myproject/
```

Secure random generation:
```python
import secrets

# Secure random token
token = secrets.token_hex(16)

# Instead of random module for security
```

## Tasks

### Beginner
1. Run bandit on a sample script and fix reported issues.
2. Implement secure password generation using `secrets`.

### Intermediate
1. Configure environment variables for sensitive data instead of hardcoding.
2. Add proper error handling that doesn't expose stack traces.

### Advanced
1. Implement secure logging that sanitizes sensitive data.
2. Set up automated security scanning in CI/CD.

## Quick Review
- Why should you avoid hardcoding secrets in code?
- What tool can you use for static security analysis in Python?
