# CI/CD Pipelines

## Explanation

Continuous Integration (CI) and Continuous Deployment (CD) automate building, testing, and deploying applications. Pipelines define stages such as install, test, build, and deploy.

Tools include GitHub Actions, GitLab CI, Travis CI, CircleCI, and Jenkins. Pipelines are often described in YAML files checked into the repository.

## Examples

### GitHub Actions workflow (basic)
```yaml
name: CI

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Set up Python
        uses: actions/setup-python@v2
        with:
          python-version: '3.11'
      - name: Install dependencies
        run: pip install -r requirements.txt
      - name: Run tests
        run: pytest
```

## Tasks

### Beginner
1. Configure a simple CI pipeline that runs tests on every push.
2. Add a badge to README showing build status.

### Intermediate
1. Add caching for dependencies to speed up builds.
2. Create separate jobs for linting, testing, and building docs.

### Advanced
1. Implement CD: automatically deploy to staging when tests pass.
2. Use matrix builds to test multiple Python versions or OSes.

## Quick Review
- What’s the difference between CI and CD?
- How do you trigger a pipeline on pull requests?

---