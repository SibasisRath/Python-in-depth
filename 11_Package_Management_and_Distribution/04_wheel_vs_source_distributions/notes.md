# Wheel vs Source Distributions

## Explanation

Python packages can be distributed as source distributions (`sdist`) or built distributions (wheels, `.whl`). A source distribution contains the raw files and requires building on the target machine, while a wheel is a pre-built archive which can be installed quickly. Wheels can be `pure` Python or include platform-specific compiled extensions.

Key distinctions:
- `sdist` usage when building C extensions or for compatibility
- Wheel tags indicate Python version, ABI, and platform
- Universal wheels (`py2.py3-none-any`) vs platform-specific

## Examples

```
python setup.py sdist
python setup.py bdist_wheel

# inspect wheel contents
unzip -l dist/mypkg-0.1.0-py3-none-any.whl
```

Use `pip install dist/mypkg-0.1.0-py3-none-any.whl` to install locally.

## Tasks

### Beginner
1. Build both sdist and wheel for a simple package and compare file sizes.
2. Install each type on a clean virtual environment and note any differences.

### Intermediate
1. Create a platform-specific wheel by compiling a simple C extension.
2. Use `wheel` package to repair or convert wheels for different Python tags.

### Advanced
1. Investigate how `pip` chooses between sdist and wheel when both are available.
2. Write a script that extracts metadata from a wheel file programmatically.

## Quick Review
- What command generates a wheel from `setup.py`?
- Why might you upload both wheel and sdist to PyPI?
