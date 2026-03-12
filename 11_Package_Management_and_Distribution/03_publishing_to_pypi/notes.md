# Publishing to PyPI

## Explanation

The Python Package Index (PyPI) is the central repository for Python packages. Publishing involves preparing your distribution files (source and/or wheel), registering an account, and uploading via tools like `twine`. You should also understand versioning, release practices, and how to manage credentials securely (`~/.pypirc` or environment variables).

Important points:
- Use semantic versioning
- Include a `README.md` and `LICENSE`
- Sign packages with GPG if desired
- Upload to Test PyPI first for testing

## Examples

```bash
python -m build    # creates dist/*
twine upload --repository testpypi dist/*

# once verified:
twine upload dist/*
```

`~/.pypirc` example:
```ini
[distutils]
index-servers =
    pypi
    testpypi

[pypi]
username = __token__
password = pypi-AgENd...   # API token

[testpypi]
username = __token__
password = pypi-AgENd...
```

## Tasks

### Beginner
1. Create a dummy package and upload it to Test PyPI. Verify installation with `pip install --index-url https://test.pypi.org/simple/ yourpkg`.
2. Read the Test PyPI documentation and locate how to create an account.

### Intermediate
1. Automate the release process with a GitHub Actions workflow using `pypa/gh-action-pypi-publish`.
2. Handle pre-releases (alpha/beta) and upload them appropriately.

### Advanced
1. Configure package signing and verify signatures after upload.
2. Explore migrating project metadata to the new `pyproject.toml` format and ensure compatibility with PyPI.

## Quick Review
- Which command uploads packages to PyPI securely?
- Why should you test on Test PyPI before uploading to the real index?
