# Code Coverage Tools

## Explanation

Code coverage measures how much of your code is exercised by tests. Tools like `coverage.py` and built-in support in `pytest` can generate reports showing untested lines.

Common features:
- Running tests under a coverage tool to collect data.
- Generating HTML, XML, or terminal reports.
- Configuring branch coverage, excluding files (e.g., tests themselves).

## Examples

```bash
# install coverage
pip install coverage

# run tests with coverage
coverage run -m pytest

# generate report
coverage report
coverage html
```

## Tasks

### Beginner
1. Run a simple test suite with `coverage` and view the report.
2. Identify untested functions and add tests.

### Intermediate
1. Configure `.coveragerc` to omit certain directories.
2. Use coverage in CI to fail builds that drop below a threshold.

### Advanced
1. Analyze branch coverage and write tests to increase it.
2. Integrate coverage with multiple test runners or languages.

## Quick Review
- What does branch coverage measure that line coverage doesn’t?
- How can you exclude files or lines from coverage reports?

---