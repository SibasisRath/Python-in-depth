# Classes and Objects - Notes

## Overview
Object-oriented programming (OOP) enables structuring code using objects and classes. This section introduces class definitions, object instantiation, and basic OOP principles.

## 1. Class Definition and Instantiation

```python
# Define a simple class
class Person:
    pass

# Create an instance
p = Person()
print(type(p))  # <class '__main__.Person'>
```

### __init__ Method (Constructor)

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

p1 = Person("Alice", 30)
print(p1.name, p1.age)  # Alice 30
```

### Instance vs Class Variables

```python
class Dog:
    species = "Canis familiaris"  # class variable

    def __init__(self, name, age):
        self.name = name  # instance variable
        self.age = age

# Accessing class variable
print(Dog.species)  # Canis familiaris

# Each object has its own instance variables
dog1 = Dog("Buddy", 5)
dog2 = Dog("Milo", 2)
print(dog1.name, dog2.name)  # Buddy Milo
```

### Methods (Instance, Class, Static)

```python
class Circle:
    pi = 3.14159

    def __init__(self, radius):
        self.radius = radius

    # instance method
    def area(self):
        return Circle.pi * self.radius ** 2

    # class method
    @classmethod
    def from_diameter(cls, diameter):
        return cls(diameter / 2)

    # static method
    @staticmethod
    def circumference(radius):
        return 2 * Circle.pi * radius

c = Circle(3)
print(c.area())  # 28.27431
c2 = Circle.from_diameter(10)
print(c2.radius)  # 5.0
print(Circle.circumference(3))  # 18.84954
```

### Properties and Property Decorators

```python
class Rectangle:
    def __init__(self, width, height):
        self._width = width
        self._height = height

    @property
    def area(self):
        return self._width * self._height

    @property
    def width(self):
        return self._width

    @width.setter
    def width(self, value):
        if value < 0:
            raise ValueError("Width must be non-negative")
        self._width = value

r = Rectangle(3, 4)
print(r.area)  # 12
r.width = 5
print(r.area)  # 20
```

### Encapsulation Principles
- Use underscore prefix `_` for protected attributes
- Use `__` double underscore for name mangling (private)
- Provide getters/setters via properties rather than direct access

## 2. Practice Tasks

### Beginner
1. Create a `Car` class with make, model, year attributes and a method to display info.
2. Instantiate multiple objects and print their attributes.

### Intermediate
1. Add a class variable to count how many `Car` objects have been created.
2. Implement a method that updates the mileage and prevents negative values via property setter.

### Advanced
1. Create a `BankAccount` class with deposit, withdraw methods and balance property. Handle overdrafts with custom exceptions.
2. Implement `__str__` and `__repr__` methods for readable output.

## 3. Quick Review
- **Class**: blueprint for objects
- **Instance**: object created from class
- **__init__**: constructor
- **self**: reference to the instance
- **class vs instance variables**: shared vs unique
- **methods**: instance (`def method(self)`), class (`@classmethod`), static (`@staticmethod`)
- **property**: manage attribute access with decorators

### Common Patterns
```python
class Example:
    def __init__(self, value):
        self._value = value

    @property
    def value(self):
        return self._value

    @value.setter
    def value(self, new):
        if new < 0:
            raise ValueError("Must be non-negative")
        self._value = new

    def __str__(self):
        return f"Example({self._value})"
```