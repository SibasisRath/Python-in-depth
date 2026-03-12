# Dataclasses and attrs

## Explanation

Dataclasses (Python 3.7+) automatically generate boilerplate methods like `__init__`, `__repr__`, and `__eq__` for simple classes. The `attrs` library is similar but more feature-rich. Both reduce code duplication for data-holding classes. Use for configuration objects, data transfer objects, and lightweight models.

Key features:
- `@dataclass` decorator
- Field definitions with default values
- Automatic method generation
- `field()` for fine-grained control
- Frozen dataclasses for immutability

## Examples

```python
from dataclasses import dataclass, field
from typing import List

@dataclass
class Person:
    name: str
    age: int
    hobbies: List[str] = field(default_factory=list)

p = Person("Alice", 30)
print(p)  # Person(name='Alice', age=30, hobbies=[])
```

Using attrs:
```python
import attrs

@attrs.define
class Person:
    name: str
    age: int
```

## Tasks

### Beginner
1. Create a dataclass with multiple fields and default values.
2. Test auto-generated `__repr__` and `__eq__` methods.

### Intermediate
1. Use `field(default_factory=...)` for mutable defaults.
2. Create a frozen dataclass and verify immutability.

### Advanced
1. Combine dataclasses with inheritance.
2. Compare performance of dataclasses vs manual classes.

## Quick Review
- What decorator converts a class to a dataclass?
- Why use `field(default_factory=...)` for mutable defaults?
