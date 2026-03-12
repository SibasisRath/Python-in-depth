# Custom Exception Classes

## Explanation

Python allows you to create custom exception classes to handle specific error conditions in your code. Custom exceptions should inherit from the built-in `Exception` class or one of its subclasses. This allows them to integrate seamlessly with Python's exception handling system.

### Why Create Custom Exceptions?

1. **Clarity**: Make your code more readable by using descriptive exception names.
2. **Specificity**: Handle different error conditions with targeted exception handling.
3. **Modularity**: Encapsulate error handling logic within your modules.
4. **Inheritance**: Create exception hierarchies that mirror your application's structure.

### Best Practices

1. **Inherit from Exception**: Always inherit from `Exception` or its subclasses, not `BaseException`.
2. **Descriptive Names**: Use clear, descriptive names ending with "Error" or "Exception".
3. **Docstrings**: Provide docstrings explaining when the exception should be raised.
4. **Minimal Initialization**: Keep `__init__` methods simple, focusing on error messages.
5. **Don't Overuse**: Only create custom exceptions when they add value.

## Examples

### Example 1: Basic Custom Exception

```python
class InvalidAgeError(Exception):
    """Raised when an invalid age is provided."""
    pass

def set_age(age):
    if age < 0 or age > 150:
        raise InvalidAgeError(f"Age {age} is not valid")
    return age

try:
    set_age(-5)
except InvalidAgeError as e:
    print(f"Error: {e}")
```

### Example 2: Custom Exception with Additional Information

```python
class InsufficientFundsError(Exception):
    """Raised when account balance is insufficient for a transaction."""
    
    def __init__(self, balance, amount):
        self.balance = balance
        self.amount = amount
        super().__init__(f"Insufficient funds: balance ${balance}, needed ${amount}")

class BankAccount:
    def __init__(self, balance):
        self.balance = balance
    
    def withdraw(self, amount):
        if amount > self.balance:
            raise InsufficientFundsError(self.balance, amount)
        self.balance -= amount
        return self.balance

account = BankAccount(100)
try:
    account.withdraw(150)
except InsufficientFundsError as e:
    print(f"Transaction failed: {e}")
    print(f"Current balance: ${e.balance}")
    print(f"Attempted withdrawal: ${e.amount}")
```

### Example 3: Exception Hierarchy

```python
class ValidationError(Exception):
    """Base class for validation errors."""
    pass

class EmailValidationError(ValidationError):
    """Raised when email validation fails."""
    pass

class PhoneValidationError(ValidationError):
    """Raised when phone validation fails."""
    pass

def validate_contact(email, phone):
    if '@' not in email:
        raise EmailValidationError("Invalid email format")
    if not phone.isdigit() or len(phone) != 10:
        raise PhoneValidationError("Invalid phone number")
    return True

try:
    validate_contact("invalid-email", "123")
except ValidationError as e:
    print(f"Validation error: {e}")
except EmailValidationError as e:
    print(f"Email error: {e}")
except PhoneValidationError as e:
    print(f"Phone error: {e}")
```

## Tasks

### Beginner

1. Create a custom exception called `NegativeNumberError` that is raised when a negative number is provided where only positive numbers are expected.
2. Write a function that validates user input and raises a custom exception for empty strings.
3. Create a `TemperatureError` exception for invalid temperature values.

### Intermediate

1. Implement a custom exception hierarchy for a library management system (e.g., `BookNotFoundError`, `BookAlreadyBorrowedError`).
2. Create a `DatabaseError` class with subclasses for different database operation failures.
3. Write a user registration system that raises specific custom exceptions for various validation failures.

### Advanced

1. Design a comprehensive exception hierarchy for an e-commerce application with nested exception classes.
2. Implement a custom exception that includes error codes, timestamps, and context information.
3. Create a logging system that automatically logs custom exceptions with additional metadata.
4. Build a REST API error handling system using custom exceptions that map to HTTP status codes.

## Quick Review

- **Base Class**: Inherit from `Exception`
- **Naming**: Use descriptive names ending with "Error" or "Exception"
- **Initialization**: Keep `__init__` simple, focus on error messages
- **Hierarchy**: Create base exceptions with specific subclasses
- **Integration**: Custom exceptions work with all Python exception handling constructs
- **Best Practice**: Only create when they add clarity or specificity