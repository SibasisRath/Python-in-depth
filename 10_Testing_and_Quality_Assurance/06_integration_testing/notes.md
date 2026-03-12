# Integration Testing

## Explanation

Integration tests verify that different parts of a system work together as expected. These tests often involve multiple components (e.g., database, network, filesystem) and may run slower than unit tests.

Strategies include:
- Using test databases or fixtures to simulate production environments.
- Running API endpoints against a running server instance.
- Employing tools like Docker Compose to spin up dependent services.

Integration tests catch issues that unit tests might miss, such as configuration errors or protocol mismatches.

## Examples

### Simple Flask app integration test
```python
import pytest
from myapp import app

@pytest.fixture
def client():
    app.config['TESTING'] = True
    with app.test_client() as client:
        yield client

def test_home(client):
    response = client.get('/')
    assert response.status_code == 200
```

### Using Docker Compose in tests
```
# docker-compose.yml defines web and db services

# in pytest setup
import subprocess

def start_services():
    subprocess.run(['docker-compose', 'up', '-d'], check=True)
    yield
    subprocess.run(['docker-compose', 'down'], check=True)
```

## Tasks

### Beginner
1. Write an integration test for a simple CLI application that reads and writes files.
2. Use a temporary database file for integration testing (e.g., SQLite).

### Intermediate
1. Set up a test suite that starts a local database and web server before running tests.
2. Use mocking to simulate external APIs while still exercising internal components.

### Advanced
1. Incorporate integration tests into a CI pipeline that spins up real service instances.
2. Analyze trade-offs between test isolation and realism; evaluate test flakiness.

## Quick Review
- What’s the main difference between unit tests and integration tests?
- Why might integration tests be slower or more brittle?

---