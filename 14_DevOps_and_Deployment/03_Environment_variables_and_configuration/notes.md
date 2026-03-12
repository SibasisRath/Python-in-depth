# Environment Variables and Configuration

## Explanation

Managing configuration via environment variables follows the [Twelve-Factor App](https://12factor.net/config) methodology. This keeps secrets and environment-specific settings out of source code.

Key points:

- Use libraries like `python-dotenv` to load `.env` files in development.
- Differentiate between development, staging, and production configs.
- Never commit secrets; use vaults or secrets managers in production.

## Examples

### Loading variables from `.env`
```python
from dotenv import load_dotenv
import os

load_dotenv()

DB_URL = os.getenv('DATABASE_URL')
```

### Using environment variables in Django settings
```python
import os
from pathlib import Path

BASE_DIR = Path(__file__).resolve().parent.parent
SECRET_KEY = os.environ['SECRET_KEY']
DEBUG = os.environ.get('DEBUG', 'False') == 'True'
```

## Tasks

### Beginner
1. Create a `.env` file and load it using `python-dotenv` in a small script.
2. Print environment variables and explain their visibility to processes.

### Intermediate
1. Set environment variables in a Docker container and verify they’re available.
2. Use a configuration library (e.g., `dynaconf` or `pydantic-settings`) to manage settings.

### Advanced
1. Integrate a secrets manager (AWS Secrets Manager, HashiCorp Vault) into your app.
2. Automate rotating credentials and reloading configuration without restarting services.

## Quick Review
- Why is it unsafe to store configuration in source code?
- What tools help manage environment variables for Python apps?

---