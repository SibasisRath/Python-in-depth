# Password Hashing (bcrypt, argon2)

## Explanation

Password hashing transforms plaintext passwords into irreversible hashes for secure storage. Use slow, salted algorithms like bcrypt or Argon2 to resist brute-force attacks. Never store plain passwords; use libraries like `bcrypt` or `passlib`. Salt adds randomness; pepper adds extra secret salt.

Key concepts:
- Hashing vs encryption (hashing is one-way)
- Salt prevents rainbow table attacks
- Work factor adjusts computational cost
- Upgrade hashes when algorithms improve

## Examples

Using bcrypt:
```python
import bcrypt

# Hash a password
password = b"mysecretpassword"
salt = bcrypt.gensalt()
hashed = bcrypt.hashpw(password, salt)

# Verify
if bcrypt.checkpw(password, hashed):
    print("Password matches")
```

Using passlib:
```python
from passlib.hash import argon2

# Hash
hash = argon2.hash("password")

# Verify
if argon2.verify("password", hash):
    print("Valid")
```

## Tasks

### Beginner
1. Hash a password with bcrypt and verify it.
2. Experiment with different salt rounds and measure timing.

### Intermediate
1. Implement password hashing in a simple user registration/login system.
2. Compare bcrypt and Argon2 performance.

### Advanced
1. Create a script to upgrade legacy MD5 hashes to bcrypt.
2. Implement peppering for additional security.

## Quick Review
- Why should passwords be hashed instead of encrypted?
- What is the purpose of a salt in password hashing?
