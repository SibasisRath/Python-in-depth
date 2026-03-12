# Type Hints and mypy

## Explanation

Type hints annotate function parameters and return types, improving code readability and enabling static type checking with `mypy`. Python 3.5+ supports the `typing` module; use annotations like `int`, `str`, `List[int]`, and `Optional[str]`. Mypy catches type errors without running code, reducing bugs.

Key features:
- Basic types: `int`, `str`, `bool`, `float`
- Generic types: `List`, `Dict`, `Tuple`, `Set`
- `Optional` for nullable types
- `Union` for multiple types
- `Callable` for functions

## Examples

```python
from typing import List, Optional, Dict

def greet(name: str) -> str:
    return f"Hello, {name}"

def process_items(items: List[int]) -> Dict[str, int]:
    return {'count': len(items)}

def maybe_int(x: Optional[int] = None) -> int:
    return x if x is not None else 0
```

Run mypy: `mypy script.py`

## Tasks

### Beginner
1. Add type hints to a simple function and run mypy.
2. Use `Optional` to annotate nullable parameters.

### Intermediate
1. Define custom types using `TypeVar` and generics.
2. Use `Protocol` for structural subtyping.

### Advanced
1. Configure mypy with a `mypy.ini` file for strict checking.
2. Integrate mypy into CI/CD pipeline.

## Quick Review
- What is the syntax for annotating a function parameter?
- How do you indicate a return type in Python?
