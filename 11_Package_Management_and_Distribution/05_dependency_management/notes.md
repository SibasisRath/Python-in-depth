# Dependency Management (Poetry, Pipenv)

## Explanation

Modern Python projects often rely on tools that manage dependencies and virtual environments. `pipenv` predated `poetry` and combines `Pipfile`/`Pipfile.lock` with environment management. `Poetry` takes a more opinionated approach with `pyproject.toml` for both metadata and dependencies, and it handles publishing as well.

Differences:
- `pipenv` uses `Pipfile`; `poetry` uses `pyproject.toml`
- Poetry has built-in version resolution and lockfile, pipenv wraps pip and virtualenv
- Both support dev dependencies and can generate `requirements.txt`

## Examples

```bash
# pipenv
pipenv install requests
pipenv shell
pipenv lock

# poetry
poetry init
poetry add flask
poetry install  # creates virtualenv automatically
poetry lock
```

## Tasks

### Beginner
1. Start a new project with each tool and add two dependencies. Inspect their lockfiles.
2. Use `pipenv run` vs `poetry run` to execute commands in the managed environment.

### Intermediate
1. Convert a `requirements.txt` project to Poetry and verify the locked versions.
2. Explore how to specify dependency groups (e.g., `[tool.poetry.dev-dependencies]`).

### Advanced
1. Benchmark dependency resolution speed between pip, pipenv, and poetry on a large `requirements.txt`.
2. Write a custom plugin for Poetry to add a new command.

## Quick Review
- Which file does Poetry use to store locked dependency versions?
- Name one reason developers choose Poetry over pipenv.
