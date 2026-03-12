# Mocking and Patching

## Explanation

Mocking allows you to replace parts of your system under test with mock objects and make assertions about how they were used. The `unittest.mock` module (available in Python’s standard library) provides `Mock`, `patch`, and related helpers.

- `patch()` can be used as a decorator or context manager to substitute an object in a module with a mock.
- `Mock` and `MagicMock` track calls, return values, and allow configuration.
- `side_effect` and `return_value` customize mock behavior.

## Examples

```python
from unittest.mock import patch, MagicMock

# patching a function
@patch('module.function_to_patch')
def test_patch(mock_func):
    mock_func.return_value = 42
    assert module.function_to_patch() == 42

# using MagicMock
m = MagicMock()
m.foo.return_value = 'bar'
assert m.foo() == 'bar'

# patch as context manager
with patch('module.ClassName') as MockClass:
    instance = MockClass()
    instance.method.return_value = 'baz'
```

## Tasks

### Beginner
1. Mock a network call in a function so tests don’t perform real HTTP requests.
2. Use `patch` to replace a class with a mock and assert that it was instantiated.

### Intermediate
1. Configure a mock’s `side_effect` to raise an exception and test error handling.
2. Use `patch.dict` to temporarily modify a dictionary (e.g., `os.environ`).

### Advanced
1. Write tests that assert a mock was called with specific arguments multiple times.
2. Explore `autospec=True` to create mocks that enforce the interface of the real object.

## Quick Review
- What does `patch()` replace, and when is the original object restored?
- How can you configure a mock to behave differently on successive calls?

---