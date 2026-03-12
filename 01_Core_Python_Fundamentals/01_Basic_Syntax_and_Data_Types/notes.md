# Basic Syntax and Data Types - Notes

## Overview
This section covers the fundamental building blocks of Python programming: variables, data types, type conversion, and basic operations.

## 1. Variables, Constants, and Naming Conventions

### Variables
Variables are containers for storing data values. Python is dynamically typed, so you don't need to declare the type explicitly.

```python
# Variable assignment
name = "Alice"
age = 25
height = 5.7
is_student = True

# Multiple assignment
x, y, z = 1, 2, 3

# Same value to multiple variables
a = b = c = 10
```

### Constants
Python doesn't have built-in constant types, but we use uppercase naming convention for constants.

```python
PI = 3.14159
MAX_CONNECTIONS = 100
DATABASE_URL = "postgresql://localhost/mydb"
```

### Naming Conventions
- **snake_case** for variables and functions: `user_name`, `calculate_total()`
- **PascalCase** for classes: `UserAccount`, `DataProcessor`
- **UPPER_CASE** for constants: `MAX_SIZE`, `DEFAULT_TIMEOUT`
- Avoid starting with numbers or using reserved keywords

## 2. Basic Data Types

### Integers (int)
Whole numbers, positive or negative.

```python
# Integer examples
positive = 42
negative = -17
zero = 0
big_number = 999999999999999999
```

### Floating Point (float)
Numbers with decimal points.

```python
# Float examples
pi = 3.14159
temperature = -5.5
scientific = 1.23e-4  # 0.000123
```

### Strings (str)
Sequence of characters enclosed in quotes.

```python
# String examples
single_quotes = 'Hello'
double_quotes = "World"
multi_line = """This is a
multi-line string"""
```

### Booleans (bool)
True or False values.

```python
# Boolean examples
is_active = True
has_permission = False
is_admin = True
```

## 3. Type Conversion and Casting

### Implicit Conversion
Python automatically converts types in some cases.

```python
# Implicit conversion
result = 5 + 2.5  # int + float = float (7.5)
print(type(result))  # <class 'float'>
```

### Explicit Conversion (Casting)

```python
# int() - Convert to integer
num_str = "42"
num_int = int(num_str)  # 42

float_num = 3.7
int_num = int(float_num)  # 3 (truncates decimal)

# float() - Convert to float
str_num = "3.14"
float_num = float(str_num)  # 3.14

int_val = 5
float_val = float(int_val)  # 5.0

# str() - Convert to string
number = 123
str_num = str(number)  # "123"

boolean = True
str_bool = str(boolean)  # "True"

# bool() - Convert to boolean
# Falsy values: 0, 0.0, "", [], {}, None
# Everything else is Truthy

bool(0)        # False
bool(1)        # True
bool("")       # False
bool("hello")  # True
bool([])       # False
bool([1,2,3])  # True
```

## 4. String Operations and Formatting

### String Operations

```python
# Concatenation
first = "Hello"
second = "World"
result = first + " " + second  # "Hello World"

# Repetition
repeat = "Ha" * 3  # "HaHaHa"

# Length
text = "Python"
len(text)  # 6

# Indexing (0-based)
text[0]  # 'P'
text[-1]  # 'n' (last character)

# Slicing
text[0:3]   # 'Pyt'
text[2:]    # 'thon'
text[:4]    # 'Pyth'
text[::-1]  # 'nohtyP' (reverse)
```

### String Methods

```python
text = "hello world"

# Case conversion
text.upper()      # 'HELLO WORLD'
text.lower()      # 'hello world'
text.title()      # 'Hello World'
text.capitalize() # 'Hello world'

# Searching
text.find('world')    # 6
text.startswith('he') # True
text.endswith('ld')   # True

# Replacing
text.replace('world', 'Python')  # 'hello Python'

# Splitting and joining
words = text.split()        # ['hello', 'world']
' '.join(words)             # 'hello world'

# Stripping whitespace
"  hello  ".strip()   # 'hello'
"  hello  ".lstrip()  # 'hello  '
"  hello  ".rstrip()  # '  hello'
```

### String Formatting

#### f-strings (Python 3.6+)
```python
name = "Alice"
age = 25
height = 5.7

# f-string formatting
message = f"My name is {name}, I'm {age} years old, and {height:.1f}m tall."
# "My name is Alice, I'm 25 years old, and 5.7m tall."

# Expressions in f-strings
result = f"The sum of 5 and 3 is {5 + 3}"
# "The sum of 5 and 3 is 8"
```

#### format() method
```python
# Positional arguments
"{} {} {}".format("Hello", "World", "!")  # "Hello World !"

# Named arguments
"{name} is {age} years old".format(name="Bob", age=30)

# Format specifiers
"Value: {:.2f}".format(3.14159)  # "Value: 3.14"
"Number: {:04d}".format(42)      # "Number: 0042"
```

#### % formatting (old style)
```python
# Old-style formatting
"Name: %s, Age: %d" % ("Alice", 25)  # "Name: Alice, Age: 25"
"Price: %.2f" % 19.99                # "Price: 19.99"
```

## 5. Collections: Lists, Tuples, Sets, Dictionaries

### Lists
Mutable, ordered sequences.

```python
# Creating lists
empty_list = []
numbers = [1, 2, 3, 4, 5]
mixed = [1, "hello", 3.14, True]

# List operations
numbers.append(6)        # [1, 2, 3, 4, 5, 6]
numbers.insert(0, 0)     # [0, 1, 2, 3, 4, 5, 6]
numbers.remove(3)        # [0, 1, 2, 4, 5, 6]
numbers.pop()            # [0, 1, 2, 4, 5] (removes last)
numbers.pop(2)           # [0, 1, 4, 5] (removes index 2)

# List methods
numbers.sort()           # [0, 1, 4, 5]
numbers.reverse()        # [5, 4, 1, 0]
numbers.count(1)         # 1
numbers.index(4)         # 2

# Slicing
numbers[1:4]   # [4, 1, 0]
numbers[::-1]  # [0, 1, 4, 5] (reverse)
```

### Tuples
Immutable, ordered sequences.

```python
# Creating tuples
empty_tuple = ()
single_item = (42,)  # Note the comma!
coordinates = (10, 20)
mixed_tuple = (1, "hello", 3.14)

# Tuple operations (limited due to immutability)
len(coordinates)     # 2
coordinates[0]       # 10
coordinates.count(10) # 1
coordinates.index(20) # 1

# Tuple unpacking
x, y = coordinates   # x=10, y=20
a, b, c = mixed_tuple # a=1, b="hello", c=3.14
```

### Sets
Unordered, unique elements.

```python
# Creating sets
empty_set = set()
numbers = {1, 2, 3, 4, 5}
from_list = set([1, 2, 2, 3, 3, 3])  # {1, 2, 3}

# Set operations
numbers.add(6)      # {1, 2, 3, 4, 5, 6}
numbers.remove(3)    # {1, 2, 4, 5, 6}
numbers.discard(10)  # No error if element not found

# Set theory operations
set1 = {1, 2, 3, 4}
set2 = {3, 4, 5, 6}

union = set1 | set2        # {1, 2, 3, 4, 5, 6}
intersection = set1 & set2  # {3, 4}
difference = set1 - set2    # {1, 2}
symmetric_diff = set1 ^ set2 # {1, 2, 5, 6}
```

### Dictionaries
Key-value pairs, unordered (Python 3.7+ maintains insertion order).

```python
# Creating dictionaries
empty_dict = {}
person = {
    "name": "Alice",
    "age": 25,
    "city": "New York"
}

# Alternative syntax
person2 = dict(name="Bob", age=30, city="London")

# Dictionary operations
person["email"] = "alice@example.com"  # Add new key-value
person["age"] = 26                     # Update value
del person["city"]                     # Remove key-value

# Dictionary methods
person.keys()     # dict_keys(['name', 'age', 'email'])
person.values()   # dict_values(['Alice', 26, 'alice@example.com'])
person.items()    # dict_items([('name', 'Alice'), ('age', 26), ...])

person.get("name")        # 'Alice'
person.get("phone", "N/A") # 'N/A' (default if key not found)

# Checking membership
"name" in person  # True
"phone" in person # False
```

## 6. Comprehensions

### List Comprehensions
```python
# Basic list comprehension
squares = [x**2 for x in range(10)]  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# With condition
even_squares = [x**2 for x in range(10) if x % 2 == 0]  # [0, 4, 16, 36, 64]

# Nested comprehension
matrix = [[i*j for j in range(3)] for i in range(3)]
# [[0, 0, 0], [0, 1, 2], [0, 2, 4]]

# Complex example
words = ["hello", "world", "python", "programming"]
upper_words = [word.upper() for word in words if len(word) > 5]
# ['PYTHON', 'PROGRAMMING']
```

### Dictionary Comprehensions
```python
# Basic dict comprehension
squares_dict = {x: x**2 for x in range(5)}  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

# From two lists
keys = ['a', 'b', 'c']
values = [1, 2, 3]
combined = {k: v for k, v in zip(keys, values)}  # {'a': 1, 'b': 2, 'c': 3}

# Conditional
even_squares = {x: x**2 for x in range(10) if x % 2 == 0}
```

### Set Comprehensions
```python
# Basic set comprehension
squares_set = {x**2 for x in range(10)}  # {0, 1, 4, 9, 16, 25, 36, 49, 64, 81}

# With condition
even_squares_set = {x**2 for x in range(10) if x % 2 == 0}
```

### Tuple Comprehensions (Generator Expressions)
```python
# Generator expression (not tuple comprehension)
squares_gen = (x**2 for x in range(10))  # <generator object>

# Convert to tuple
squares_tuple = tuple(x**2 for x in range(5))  # (0, 1, 4, 9, 16)
```

## 7. None and Null Handling

### None Type
None represents the absence of a value.

```python
# None examples
result = None
empty_variable = None

# Checking for None
if result is None:
    print("No result found")

# None vs False vs 0 vs empty string
print(None == False)  # False
print(None == 0)      # False
print(None == "")     # False

# Proper None checking
value = None
if value is None:     # Use 'is' not '=='
    print("Value is None")

# Default values
def get_name(name=None):
    if name is None:
        return "Anonymous"
    return name
```

## Practice Tasks

### Beginner Level
1. Create variables for your name, age, and favorite color
2. Convert a string "123" to integer and add 10 to it
3. Create a list of 5 numbers and print the sum
4. Create a dictionary with 3 key-value pairs about yourself
5. Use string formatting to create a greeting message

### Intermediate Level
1. Write a program that takes user input and determines its data type
2. Create a list comprehension that filters even numbers from 1-20
3. Build a simple calculator using functions and user input
4. Create a dictionary comprehension that maps numbers to their squares
5. Write a program that counts vowels in a string

### Advanced Level
1. Implement a function that converts between different data types safely
2. Create a nested data structure (dict of lists) and perform operations on it
3. Write a program that parses a CSV-like string into a list of dictionaries
4. Implement a simple inventory system using dictionaries and lists
5. Create a function that validates and sanitizes user input

## Quick Review

### Key Concepts
- **Variables**: Containers for data, dynamically typed
- **Data Types**: int, float, str, bool, list, tuple, set, dict
- **Type Conversion**: int(), float(), str(), bool()
- **String Formatting**: f-strings (preferred), format(), %
- **Collections**: Choose based on needs (mutability, order, uniqueness)
- **Comprehensions**: Concise way to create collections
- **None**: Represents absence of value, check with `is None`

### Common Patterns
```python
# Safe type conversion
def safe_int(value, default=0):
    try:
        return int(value)
    except (ValueError, TypeError):
        return default

# List comprehension with condition
filtered = [x for x in data if condition(x)]

# Dictionary get with default
value = my_dict.get('key', 'default_value')

# String formatting best practice
message = f"Hello, {name}! You are {age} years old."
```

### Best Practices
- Use descriptive variable names
- Prefer f-strings for formatting (Python 3.6+)
- Use `is None` instead of `== None`
- Choose appropriate data structures for your use case
- Use comprehensions for readable, concise code
- Handle type conversion errors gracefully