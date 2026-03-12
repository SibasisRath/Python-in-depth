# `unittest` Framework

## Explanation

`unittest` is Python’s built-in testing framework modeled after Java’s JUnit. It provides a `TestCase` class, assertion methods, test discovery, and test runners.

Key features:
- Organize tests in classes derived from `unittest.TestCase`.
- Use setup/teardown methods (`setUp`, `tearDown`, `setUpClass`, `tearDownClass`).
- A variety of assertions (`assertEqual`, `assertTrue`, `assertRaises`, etc.).
- Command-line test discovery with `python -m unittest`.

## Examples

```python
import unittest

class TestMath(unittest.TestCase):
    def test_add(self):
        self.assertEqual(1 + 1, 2)

    def test_divide(self):
        with self.assertRaises(ZeroDivisionError):
            _ = 1 / 0

if __name__ == '__main__':
    unittest.main()
```

## Tasks

### Beginner
1. Write a `TestCase` with two simple tests for arithmetic functions.
2. Practice running tests via the command line and exploring output options.

### Intermediate
1. Use `setUp` and `tearDown` to create temporary files before each test and clean up afterwards.
2. Write a parameterized test by dynamically creating subtests with `self.subTest()`.

### Advanced
1. Create a custom test runner to change formatting of results.
2. Integrate `unittest` with a CI pipeline (GitHub Actions, Travis CI) and ensure tests run on each push.

## Quick Review
- What method do you override to run code before each test?
- How do you assert that an exception is raised?

---