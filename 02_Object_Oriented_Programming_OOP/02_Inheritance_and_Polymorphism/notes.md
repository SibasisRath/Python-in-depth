# Inheritance and Polymorphism - Notes

## Overview
Inheritance allows a class to derive properties and behavior from another class. Polymorphism enables using a single interface for different data types.

## 1. Single Inheritance

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        raise NotImplementedError("Subclasses must implement speak()")

class Dog(Animal):
    def speak(self):
        return "Woof!"

class Cat(Animal):
    def speak(self):
        return "Meow!"

pets = [Dog("Buddy"), Cat("Whiskers")]
for pet in pets:
    print(f"{pet.name} says {pet.speak()}")
```

## 2. Multiple Inheritance and MRO

```python
class Flyer:
    def fly(self):
        return "Flying"

class Swimmer:
    def swim(self):
        return "Swimming"

class Duck(Flyer, Swimmer):
    pass

d = Duck()
print(d.fly(), d.swim())

# MRO (Method Resolution Order)
print(Duck.mro())
```

### Diamond Problem Example

```python
class A:
    def say(self):
        return "A"

class B(A):
    def say(self):
        return "B"

class C(A):
    def say(self):
        return "C"

class D(B, C):
    pass

print(D().say())  # Uses B then C due to MRO
```

## 3. Method Overriding and super()

```python
class Vehicle:
    def __init__(self, make):
        self.make = make

    def drive(self):
        return "Driving"

class Car(Vehicle):
    def __init__(self, make, model):
        super().__init__(make)
        self.model = model

    def drive(self):
        return f"Driving {self.make} {self.model}"

c = Car("Toyota", "Camry")
print(c.drive())  # Driving Toyota Camry
```

## 4. Abstract Base Classes (ABC)

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Square(Shape):
    def __init__(self, side):
        self.side = side

    def area(self):
        return self.side * self.side

# s = Shape()  # Error: can't instantiate abstract class
sq = Square(4)
print(sq.area())  # 16
```

## 5. Polymorphism and Duck Typing

```python
def process_animal(animal):
    print(animal.speak())

class Bird:
    def speak(self):
        return "Tweet"

process_animal(Dog("Rex"))
process_animal(Cat("Mittens"))
process_animal(Bird())
```

## 6. Composition vs Inheritance

```python
class Engine:
    def start(self):
        return "Engine starting"

class Car:
    def __init__(self):
        self.engine = Engine()  # composition

    def start(self):
        return self.engine.start()

car = Car()
print(car.start())
```

## Practice Tasks

### Beginner
1. Create a base class `Vehicle` and derive `Car` and `Bike` with override methods.
2. Instantiate and call polymorphic methods.

### Intermediate
1. Implement multiple inheritance with `AmphibiousVehicle` combining `Car` and `Boat`.
2. Explore MRO using custom classes.

### Advanced
1. Create an abstract class `Employee` and implement `Manager` and `Developer` subclasses.
2. Write a function that accepts any object with a `work()` method (duck typing).

## Quick Review
- **Inheritance**: subclass inherits attributes and methods from parent
- **super()**: call parent implementation
- **MRO**: determines method lookup order in multiple inheritance
- **Abstract classes**: use `abc` module to enforce interface
- **Polymorphism**: same interface, different implementations
- **Composition**: class contains instances of other classes

### Common Patterns
```python
# Mixin example
class JsonSerializable:
    def to_json(self):
        import json
        return json.dumps(self.__dict__)

class Person(JsonSerializable):
    def __init__(self, name, age):
        self.name = name
        self.age = age

p = Person("Alice", 30)
print(p.to_json())
```