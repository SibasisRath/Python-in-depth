# Control Flow - Notes

## Overview
Control flow statements allow you to control the execution path of your program based on conditions and loops. This section covers conditional statements, loops, and flow control mechanisms.

## 1. Conditional Statements (if/elif/else)

### Basic if Statement
Executes code only if a condition is True.

```python
# Basic if statement
age = 18
if age >= 18:
    print("You are an adult")

# Code continues here regardless of condition
print("Program continues...")
```

### if-else Statement
Executes one block if condition is True, another if False.

```python
# if-else statement
temperature = 25
if temperature > 30:
    print("It's hot outside")
else:
    print("It's not too hot")

# With boolean expression
is_raining = True
if is_raining:
    print("Take an umbrella")
else:
    print("Enjoy the weather")
```

### if-elif-else Statement
Checks multiple conditions in sequence.

```python
# if-elif-else chain
score = 85
if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
elif score >= 60:
    grade = "D"
else:
    grade = "F"

print(f"Your grade is: {grade}")
```

### Nested if Statements
if statements inside other if statements.

```python
# Nested conditionals
age = 25
has_license = True

if age >= 18:
    if has_license:
        print("You can drive")
    else:
        print("You need a license to drive")
else:
    print("You are too young to drive")
```

### Conditional Expressions (Ternary Operator)
Compact if-else in a single line.

```python
# Ternary operator
age = 20
status = "Adult" if age >= 18 else "Minor"
print(status)  # "Adult"

# Multiple conditions
score = 75
result = "Pass" if score >= 60 else "Fail" if score >= 0 else "Invalid"
```

### Truthy and Falsy Values
All values in Python have a truthiness.

```python
# Falsy values: False, 0, 0.0, "", [], {}, None, set()
# Everything else is Truthy

def check_value(value):
    if value:
        print(f"{value} is truthy")
    else:
        print(f"{value} is falsy")

check_value(0)        # 0 is falsy
check_value(1)        # 1 is truthy
check_value("")       # (empty string) is falsy
check_value("hello")  # hello is truthy
check_value([])       # [] is falsy
check_value([1,2,3])  # [1, 2, 3] is truthy
```

## 2. Loops

### for Loops
Iterate over sequences (lists, tuples, strings, ranges, etc.)

```python
# Basic for loop with list
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(f"I like {fruit}")

# Iterating over string
word = "Python"
for letter in word:
    print(letter)

# Iterating over range
for i in range(5):  # 0, 1, 2, 3, 4
    print(i)

# Iterating with index using enumerate
fruits = ["apple", "banana", "cherry"]
for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")
```

### while Loops
Repeat while a condition is True.

```python
# Basic while loop
count = 0
while count < 5:
    print(f"Count: {count}")
    count += 1

# While with user input
password = ""
while password != "secret":
    password = input("Enter password: ")
print("Access granted!")

# Infinite loop with break
while True:
    user_input = input("Enter 'quit' to exit: ")
    if user_input == "quit":
        break
    print(f"You entered: {user_input}")
```

### Loop Control Statements

#### break Statement
Exit the loop immediately.

```python
# break example
for i in range(10):
    if i == 5:
        break
    print(i)  # Prints 0, 1, 2, 3, 4

# Finding first even number
numbers = [1, 3, 5, 6, 7, 9]
for num in numbers:
    if num % 2 == 0:
        print(f"First even number: {num}")
        break
```

#### continue Statement
Skip the current iteration and continue with the next.

```python
# continue example
for i in range(10):
    if i % 2 == 0:
        continue
    print(i)  # Prints 1, 3, 5, 7, 9

# Skipping negative numbers
numbers = [1, -2, 3, -4, 5, -6]
positive_sum = 0
for num in numbers:
    if num < 0:
        continue
    positive_sum += num
print(f"Sum of positive numbers: {positive_sum}")  # 9
```

#### else Clause in Loops
Executed when loop completes normally (not via break).

```python
# else with for loop
for i in range(5):
    print(i)
else:
    print("Loop completed successfully")

# else with while loop
count = 0
while count < 3:
    print(count)
    count += 1
else:
    print("While loop finished")

# Searching with else
numbers = [1, 3, 5, 7, 9]
search_for = 4
for num in numbers:
    if num == search_for:
        print(f"Found {search_for}")
        break
else:
    print(f"{search_for} not found in list")
```

## 3. Range Function and Iteration

### range() Function
Generate sequences of numbers.

```python
# range(stop) - from 0 to stop-1
for i in range(5):  # 0, 1, 2, 3, 4
    print(i)

# range(start, stop) - from start to stop-1
for i in range(2, 8):  # 2, 3, 4, 5, 6, 7
    print(i)

# range(start, stop, step) - with step size
for i in range(0, 10, 2):  # 0, 2, 4, 6, 8
    print(i)

# Negative step (counting down)
for i in range(10, 0, -1):  # 10, 9, 8, 7, 6, 5, 4, 3, 2, 1
    print(i)

# Converting range to list
numbers = list(range(5))  # [0, 1, 2, 3, 4]
```

### Advanced Iteration Patterns

```python
# Iterating over multiple sequences
names = ["Alice", "Bob", "Charlie"]
ages = [25, 30, 35]

for name, age in zip(names, ages):
    print(f"{name} is {age} years old")

# Iterating with index
fruits = ["apple", "banana", "cherry"]
for index, fruit in enumerate(fruits, start=1):
    print(f"{index}. {fruit}")

# Reversing iteration
for fruit in reversed(fruits):
    print(fruit)

# Sorting during iteration
numbers = [3, 1, 4, 1, 5, 9, 2]
for num in sorted(numbers):
    print(num)
```

## 4. Nested Loops and Control Structures

### Nested for Loops
Loop inside another loop.

```python
# Multiplication table
for i in range(1, 4):
    for j in range(1, 4):
        print(f"{i} * {j} = {i*j}")
    print()  # Empty line after each row

# Iterating over 2D list
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

for row in matrix:
    for element in row:
        print(element, end=" ")
    print()  # New line after each row
```

### Nested while Loops
```python
# Nested while loops
i = 1
while i <= 3:
    j = 1
    while j <= 3:
        print(f"({i}, {j})", end=" ")
        j += 1
    print()
    i += 1
```

### Loop Control in Nested Structures
```python
# Breaking out of nested loops
for i in range(3):
    for j in range(3):
        if i == 1 and j == 1:
            break  # Only breaks inner loop
        print(f"({i}, {j})")

# Using flag to break outer loop
found = False
for i in range(3):
    for j in range(3):
        if i == 1 and j == 1:
            found = True
            break
        print(f"({i}, {j})")
    if found:
        break
```

### List Comprehensions with Nested Logic
```python
# Nested list comprehension
matrix = [[i*j for j in range(1, 4)] for i in range(1, 4)]
# [[1, 2, 3], [2, 4, 6], [3, 6, 9]]

# Flattening nested lists
nested = [[1, 2], [3, 4], [5, 6]]
flattened = [item for sublist in nested for item in sublist]
# [1, 2, 3, 4, 5, 6]
```

## Practice Tasks

### Beginner Level
1. Write a program that checks if a number is positive, negative, or zero
2. Create a for loop that prints numbers from 1 to 10
3. Write a while loop that counts down from 10 to 1
4. Create a program that prints even numbers from 1 to 20 using continue
5. Write a simple menu system using if-elif-else

### Intermediate Level
1. Create a program that finds the largest number in a list
2. Write a nested loop to print a triangle pattern of stars
3. Create a number guessing game using loops and conditionals
4. Write a program that validates user input (must be a number between 1-100)
5. Create a simple calculator that continues until user chooses to quit

### Advanced Level
1. Implement the FizzBuzz problem (multiples of 3=Fizz, 5=Buzz, both=FizzBuzz)
2. Write a program that finds prime numbers up to a given limit
3. Create a nested loop that generates a multiplication table
4. Implement a simple text-based menu system with multiple options
5. Write a program that processes a list of dictionaries using nested loops

## Quick Review

### Key Concepts
- **if/elif/else**: Conditional execution based on boolean expressions
- **for loops**: Iterate over sequences (lists, strings, ranges)
- **while loops**: Repeat while condition is True
- **break**: Exit loop immediately
- **continue**: Skip current iteration
- **else in loops**: Execute when loop completes normally
- **range()**: Generate number sequences
- **Nested loops**: Loops inside loops for complex iteration

### Common Patterns
```python
# Input validation loop
while True:
    try:
        age = int(input("Enter age: "))
        if age < 0:
            print("Age cannot be negative")
            continue
        break
    except ValueError:
        print("Please enter a valid number")

# Searching with early exit
def find_item(items, target):
    for item in items:
        if item == target:
            return True
    return False

# Menu system
def show_menu():
    while True:
        print("\n1. Add item\n2. Remove item\n3. Quit")
        choice = input("Choose option: ")
        if choice == "1":
            # add logic
        elif choice == "2":
            # remove logic
        elif choice == "3":
            break
        else:
            print("Invalid choice")
```

### Best Practices
- Use for loops when you know the number of iterations
- Use while loops for indefinite repetition
- Avoid deep nesting (more than 2-3 levels)
- Use break and continue sparingly for readable code
- Prefer list comprehensions over complex nested loops when possible
- Always consider edge cases in conditional logic
- Use meaningful variable names in loops