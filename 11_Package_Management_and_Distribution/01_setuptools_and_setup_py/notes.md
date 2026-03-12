# setuptools and setup.py

## Explanation

`setuptools` has been the traditional way to package Python projects. A `setup.py` script defines metadata and build instructions for your package (name, version, dependencies, entry points, etc.). Running `python setup.py sdist bdist_wheel` creates source and wheel distributions. Even with newer tools, understanding `setup.py` helps debug legacy projects.

Key concepts:
- `setup()` function arguments (name, version, packages, install_requires)
- `find_packages()` to automatically discover modules
- Entry points for console scripts
- `setup.cfg` as an alternate static configuration file

## Examples

```python
from setuptools import setup, find_packages

setup(
    name='myproject',
    version='0.1.0',
    packages=find_packages(),
    install_requires=['requests>=2.0'],
    entry_points={
        'console_scripts': [
            'mycmd = myproject.cli:main',
        ],
    },
)
```

## Tasks

### Beginner
1. Write a simple `setup.py` for a small package with one module and install it locally using `pip install -e .`.
2. Add a console script entry point and test it after installation.

### Intermediate
1. Include package data (e.g. JSON files) using `package_data` or `include_package_data` and verify it's installed.
2. Convert part of `setup.py` arguments into a `setup.cfg` file and keep dynamic values in `setup.py`.

### Advanced
1. Create a `setup.py` that conditionally includes dependencies based on Python version or environment variables.
2. Explore subclassing `setuptools.Command` to add a custom build step.

## Quick Review
- What command builds source and wheel distributions from `setup.py`?
- How do you define a console script entry point?
