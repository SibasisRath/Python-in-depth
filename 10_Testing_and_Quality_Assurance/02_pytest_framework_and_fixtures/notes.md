# `pytest` Framework and Fixtures

## Explanation

`pytest` is a popular third-party testing framework known for its simplicity and powerful features. Tests are written as functions and use plain `assert` statements. Fixtures provide reusable setup/teardown logic.

Key features:
- Simple test functions prefixed with `test_`.
- Rich plugin ecosystem and extensions.
- Fixtures via the `@pytest.fixture` decorator, with scope control (`function`, `module`, `session`).
- Parameterized tests using `@pytest.mark.parametrize`.
- Detailed failure introspection and built-in assertion rewriting.

## Examples

```python
# test_sample.py
import pytest

@pytest.fixture
def temp_file(tmp_path):
    file = tmp_path / "data.txt"
    file.write_text("hello")
    return file

def test_read(temp_file):
    assert temp_file.read_text() == "hello"

@pytest.mark.parametrize("a,b,expected", [(1,2,3), (2,3,5)])
def test_add(a, b, expected):
    assert a + b == expected
```

Run with:
```
pytest -q
```

## Tasks

### Beginner
1. Install `pytest` and convert an existing `unittest` suite into `pytest` style.
2. Create a fixture that provides a temporary directory.

### Intermediate
1. Use `parametrize` to test a function with multiple input combinations.
2. Write a fixture that depends on another fixture.

### Advanced
1. Explore writing a custom plugin or a hook to modify test collection.
2. Profile slow tests with `pytest --durations` and optimize.

## Quick Review
- How do you mark a test to expect failure (`xfail`) or to skip it?
- What is the default scope of a fixture?

---