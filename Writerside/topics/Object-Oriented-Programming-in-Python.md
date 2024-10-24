# Object-Oriented Programming in Python

Object-Oriented Programming (OOP) is a programming paradigm based on the concept of objects, which can contain both 
data (attributes) and functions (methods). Python is an object-oriented language, and almost everything in Python is 
an object.

## Classes

A class is a blueprint for creating objects. Objects are instances of a class.

```Python
class Dog:
    species = 'Canis lupus familiaris'

    def __init__(self, name, age):
        self.name = name
        self.age = age

    def bark(self):
        return f"{self.name} says woof!"

my_dog = Dog('Buddy', 5)
print(my_dog.bark())
```

## Inheritance

Inheritance allows a class (child class) to inherit attributes and methods from another class (parent class). 
This promotes code reusability.

```Python
class Animal:
    def __init__(self, name):
    self.name = name

    def speak(self):
        raise NotImplementedError("Subclass must implement this method")

# Child class inheriting from Animal
class Dog(Animal):
    def speak(self):
        return f"{self.name} says Woof!"

class Cat(Animal):
    def speak(self):
        return f"{self.name} says Meow!"


dog = Dog("Buddy")
cat = Cat("Whiskers")
print(dog.speak())  # Output: Buddy says Woof!
print(cat.speak())  # Output: Whiskers says Meow!
```

## Encapsulation

Encapsulation refers to the bundling of data (attributes) and methods into a single unit or class, and restricting 
access to some of the object's components. You can protect the inner workings of a class using private and protected 
access specifiers.

- Private Members: In Python, attributes can be made private by prefixing the attribute with double underscores (__).
- Protected Members: Protected members are prefixed with a single underscore (_), indicating that they are intended for 
internal use but not strictly private.

```Python
class Car:
    def __init__(self, model, year):
    self.model = model  # Public attribute
    self._year = year   # Protected attribute
    self.__mileage = 0  # Private attribute

    def add_mileage(self, miles):
        self.__mileage += miles
    
    def get_mileage(self):
        return self.__mileage

# Create an instance of Car
car = Car("Toyota", 2020)
print(car.model)  # Output: Toyota (public attribute)

car.add_mileage(500)
print(car.get_mileage())  # Output: 500

# Direct access to a private attribute will raise an AttributeError
# print(car.__mileage)  # This will raise an error

# But you can access it with name mangling
print(car._Car__mileage)  # Output: 500 (access private attribute using name mangling)
```

## Methods

Python provides three types of methods in a class:

- Instance Methods: Operate on an instance of the class and can access both the instance and class variables.
- Class Methods: Operate on the class itself and can only access class variables.
- Static Methods: Neither access instance nor class variables but can perform independent tasks.

```Python
class MyClass:
    class_variable = 42

    def __init__(self, value):
        self.instance_variable = value

    # Instance method
    def instance_method(self):
        return self.instance_variable

    # Class method
    @classmethod
    def class_method(cls):
        return cls.class_variable

    # Static method
    @staticmethod
    def static_method():
        return "This is a static method."


obj = MyClass(10)

print(obj.instance_method())  # Output: 10
print(MyClass.class_method())  # Output: 42
print(MyClass.static_method())  # Output: This is a static method.
```