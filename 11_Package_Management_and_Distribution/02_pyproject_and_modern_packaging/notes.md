# pyproject.toml and Modern Packaging

## Explanation

`PEP 518` introduced `pyproject.toml` as a standardized configuration file for Python project metadata and build requirements. It decouples build system logic (setuptools, poetry, flit) from project code and enables tools to understand how to build the package. Modern packaging encourages using declarative configuration and tools like Poetry or Flit.

Key sections:
- `[build-system]` specifying requires and build-backend
- `[tool.<name>]` for tool-specific configuration (e.g., `[tool.poetry]`, `[tool.flit.metadata]`)
- Dependencies and development dependencies in `[tool.poetry.dependencies]` etc.

## Examples

### Minimal pyproject.toml for setuptools
```toml
[build-system]
requires = ["setuptools>=42", "wheel"]
build-backend = "setuptools.build_meta"

[tool.setuptools]
packages = ["myproject"]

[tool.setuptools.package-data]
"" = ["data/*.dat"]
```

### Poetry example
```toml
[tool.poetry]
name = "myproject"
version = "0.1.0"
description = "Example package"
authors = ["You <you@example.com>"]

[tool.poetry.dependencies]
python = ">=3.8"
requests = "^2.25"

[tool.poetry.dev-dependencies]
pytest = "^6.0"
```

## Tasks

### Beginner
1. Create a `pyproject.toml` with `[build-system]` and use `pip wheel .` to build the package.
2. Compare the resulting distribution files with those built by `setup.py`.

### Intermediate
1. Migrate a simple `setup.py` project to `pyproject.toml` only (no `setup.py`).
2. Use Poetry to manage the project and add/remove dependencies.

### Advanced
1. Create a custom build backend plugin and test it via pyproject configuration.
2. Explore editable installs (`pip install -e .`) with pyproject-managed projects.

## Quick Review
- What section of `pyproject.toml` defines the build backend?
- Name two tools that use `pyproject.toml` for project configuration.
