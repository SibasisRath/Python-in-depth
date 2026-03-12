# Functions - Notes

## Overview
Functions are reusable blocks of code that perform a specific task. This section covers defining functions, parameters, scope, recursion, and higher-order functions.

## 1. Function Definition and Calling

```python
def greet():
    print("Hello, world!")

# Call the function
greet()
```

### Parameters and Arguments

- **Positional arguments**

```python
def add(a, b):
    return a + b

result = add(2, 3)  # 5
```

- **Keyword arguments**

```python
def describe_person(name, age):
    print(f"{name} is {age} years old")

describe_person(age=25, name="Alice")
```

- **Default parameters**

```python
def power(base, exponent=2):
    return base ** exponent

print(power(3))      # 9
print(power(3, 3))   # 27
```

- **Variable-length arguments**

```python
def sum_all(*args):
    return sum(args)

print(sum_all(1, 2, 3))  # 6


def build_profile(**kwargs):
    return kwargs

print(build_profile(name="Bob", age=30))
# {'name': 'Bob', 'age': 30}
```

### Return Values and Multiple Returns

```python
def divide_and_remainder(a, b):
    return a // b, a % b

quotient, remainder = divide_and_remainder(10, 3)
print(quotient, remainder)  # 3 1
```

### Lambda Functions and Anonymous Functions

```python
# Lambda for small anonymous functions
square = lambda x: x * x
print(square(5))  # 25

# Use with map/filter
numbers = [1, 2, 3, 4]
squares = list(map(lambda x: x**2, numbers))
print(squares)  # [1, 4, 9, 16]
```

## 2. Function Scope and Global/Local Variables

```python
x = 10  # global variable

def modify():
    x = 5  # local variable, doesn't affect global
    print("inside", x)

modify()
print("outside", x)  # outside 10

# use global statement

def modify_global():
    global x
    x = 20

modify_global()
print(x)  # 20
```

### Nested Functions and Closures

```python
def outer(a):
    def inner(b):
        return a + b
    return inner

adder = outer(5)
print(adder(3))  # 8
```

## 3. Recursion Fundamentals

```python
def factorial(n):
    if n <= 1:
        return 1
    return n * factorial(n - 1)

print(factorial(5))  # 120
```

### Recursive vs Iterative

```python
def fib_recursive(n):
    if n <= 1:
        return n
    return fib_recursive(n-1) + fib_recursive(n-2)


def fib_iterative(n):
    a, b = 0, 1
    for _ in range(n):
        a, b = b, a + b
    return a
```

## 4. Higher-Order Functions (map, filter, reduce)

```python
from functools import reduce

numbers = [1, 2, 3, 4, 5]

# map
squares = list(map(lambda x: x**2, numbers))

# filter
evens = list(filter(lambda x: x % 2 == 0, numbers))

# reduce
sum_all = reduce(lambda a, b: a + b, numbers)
```

## Practice Tasks

### Beginner
1. Write a function that returns the maximum of two numbers.
2. Create a function that prints a multiplication table for a given number.

### Intermediate
1. Implement a recursive function to compute the nth Fibonacci number.
2. Write a function with *args and **kwargs that prints its arguments.

### Advanced
1. Compose two functions: one that doubles a number and another that adds three; use higher-order functions.
2. Create a decorator that logs function execution time.

## Quick Review

- **define** using `def` keyword
- **arguments**: positional, keyword, default, *args, **kwargs
- **return** values (can return multiple)
- **scope**: local vs global, `global` keyword
- **lambda**: concise anonymous functions
- **recursion**: function calling itself
- **higher-order**: functions that take/return functions

### Common Patterns

```python
def logger(func):
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        return func(*args, **kwargs)
    return wrapper

@logger
def say_hello():
    print("Hello")

say_hello()
```