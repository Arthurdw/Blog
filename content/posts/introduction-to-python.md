+++
author = "Arthurdw"
title = "Introduction to Python"
date = "2022-12-15T17:27:51+01:00"
tags = [ "Python", "Programming", "Basics", "Functions", "Parameters", "Imports", "Classes", "Inheritance" ]
keywords = [ "Python", "Programming language", "Beginner's guide", "Basics", "Data types", "Functions", "Imports", "Classes", "Inheritance", "Private variables", "Getters and setters", "Syntax", "Readability", "Flexibility", "Fields of use", "Beginner-friendly", "High-level", "Interpreted", "Web development", "Data science", "Scientific computing" ]
description = "This article provides an introduction to the basics of Python, including its data types, functions, parameters, imports, classes, and inheritance. It explains how to use these concepts to write simple programs in Python. The article is intended for beginners who want to learn the fundamentals of the language."
color = "blue"
+++

# Introduction to Python

Python is a high-level, interpreted programming language that is widely used in many fields, including web development,
data science, and scientific computing. It is known for its simple syntax, readability, and flexibility, which makes it
a great language for beginners to learn. In this post, we will cover the basics of Python, including its data types,
functions *(and parameter options)*, imports, classes *(and how to do inheritance, private variables, getters and
setters)*.

## Data Types

In Python, data types are used to define the kind of value a variable holds. Some common data types in Python
are:

* `int`: Integer numbers, e.g. `1`, `2`, `3`
* `float`: Real numbers, e.g. `3.14`, `0.99`, `-1.5`
* `str`: Text strings, e.g. `"Hello, world!"`, `"Python is fun!"`
* `bool`: Boolean values, i.e. `True` or `False`

We can check the type of a variable using the built-in `type()` function. For example:

```py
a = 1
b = 1.5
c = "Hello, world!"
d = True

print(type(a))  # <class 'int'>
print(type(b))  # <class 'float'>
print(type(c))  # <class 'str'>
print(type(d))  # <class 'bool'>
```

## Functions

Functions are blocks of code that are used to perform specific tasks. In Python, we can define our own functions using
the `def` keyword, followed by the function name and a set of parentheses `()` containing the function's parameters. For
example:

```py
def greet():
    print("Hello, world!")
```

To call a function, we simply use its name followed by a set of parentheses `()`. For example:

```py
greet()  # Hello, world!
```

Functions can also take arguments (i.e. input values) and return output values. For example:

```py
def add(a, b):
    return a + b

result = add(1, 2)  # 3
```

### Parameters

When defining a function, we can specify its parameters in the parentheses `()` following the function name. These
parameters are used to pass input values to the function when it is called. In Python, there are three types of
parameters:

* `args`: Positional arguments, which are passed to the function in the same order as they are defined.
* `kwargs`: Keyword arguments, which are passed to the function using the name of the argument, followed by an equals
  sign `=` and the value.
* `default`: Default parameters, which are optional parameters that have predefined default values. If a default
  parameter is not specified when the function is called, its default value will be used.

Here is an example of a function that uses all three types of parameters:

```py
def display_info(name, *args, age=None, **kwargs):
    print(f"Name: {name}")
    print(f"Age: {age}")
    
    for arg in args:
        print(f"Extra argument: {arg}")
        
    for k, v in kwargs.items():
        print(f"{k}: {v}")
        
display_info("Arthur", "first extra argument", "second extra argument", extra_kwargs="this argument", age=19)
# Name: Arthur
# Age: 19
# Extra argument: first extra argument
# Extra argument: second extra argument
# extra_kwargs: this argument
```

## Imports

In Python, we can import code from other modules (i.e. files containing Python code) using the `import` keyword. This
allows us to use the functions, classes, and other objects defined in the imported module in our own code. For example,
we can import the built-in `math` module to access mathematical functions, such as `sin`, `cos`, and `sqrt`:

```py
import math

x = math.sin(1)  # 0.8414709848078965
y = math.cos(1)  # 0.5403023058681398
z = math.sqrt(2)  # 1.4142135623730951
```

We can also import specific objects from a module using the `from` keyword, followed by the module name and the object(
s) we want to import, separated by commas. For example:

```py
from math import sin, cos, sqrt

x = sin(1)  # 0.8414709848078965
y = cos(1)  # 0.5403023058681398
z = sqrt(2)  # 1.4142135623730951
```

## Classes

In Python, a class is a blueprint for creating objects. It defines the attributes (i.e. data) and methods (i.e.
functions) that an object of that class will have. To create a class, we use the `class` keyword, followed by the class
name and a colon `:`. Then, we define the attributes and methods inside the class using the self keyword to refer to the
current object. For example:

```py
class Point:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def distance(self, other):
        dx = self.x - other.x
        dy = self.y - other.y
        return math.sqrt(dx**2 + dy**2)
```

Here, we have defined a `Point` class with two attributes, `x` and `y`, and a method, `distance`, which calculates the
distance between two `Point` objects. To create an object of a class, we use the class name followed by a set of
parentheses `()` containing any required arguments. For example:

```py
p1 = Point(1, 2)
p2 = Point(3, 4)

print(p1.x)  # 1
print(p1.y)  # 2
print(p1.distance(p2))  # 2.8284271247461903
```

### Inheritance

In Python, inheritance allows us to define a new class that inherits the attributes and methods of an existing class.
This allows us to reuse code and create a hierarchical structure of classes. To create a class that inherits from
another class, we use the `class` keyword followed by the new class name, the `inherits` keyword, and the name of the
parent class. For example:

```py
class Circle(Point):
    def __init__(self, x, y, radius):
        super().__init__(x, y)  # call the parent class's __init__ method
        self.radius = radius

    def area(self):
        return math.pi * self.radius**2
```

## Private Variables and Methods

In Python, we can define private variables and methods, which cannot be accessed or modified from outside the class.
Private variables and methods are prefixed with two underscores `__`, which is called the "name mangling" syntax.
However, this syntax only serves as a convention, and does not prevent external access to the private attribute. To
truly prevent external access, we can use "getter" and "setter" methods, which are decorated with the `@property`
and `@attribute.setter` decorators, respectively.

For example:

```py
class Circle(Point):
    def __init__(self, x, y, radius):
        super().__init__(x, y)  # call the parent class's __init__ method
        self.__radius = radius

    @property
    def radius(self):
        return self.__radius

    @radius.setter
    def radius(self, radius):
        self.__radius = radius

    def area(self):
        return math.pi * self.__radius**2
```

Here, the `__radius` attribute is private, so it cannot be accessed or modified directly from outside the class.
Instead, we have defined `radius` as a property using the `@property` decorator, which allows us to access the value of
the __ radius attribute using dot notation (e.g. `circle.radius`). We have also defined the radius attribute as a setter
using the @radius.setter decorator, which allows us to update the value of the `__radius` attribute using dot notation (
e.g. `circle.radius = 4`).

For example:

```py
c = Circle(1, 2, 3)

print(c.radius)  # 3
c.radius = 4
print(c.radius)  # 4
```

Note that while getters and setters provide a more robust way to prevent external access to private attributes, they are
not completely foolproof. Therefore, private variables and methods should not be used for security purposes. They are
primarily used for encapsulation, i.e. to prevent accidental modification of an object's internal state.

## Conclusion

In conclusion, Python is a powerful, versatile programming language that is widely used in many fields. It has a simple
syntax, making it easy to learn and read. In this post, we have covered the basics of Python, including its data types,
functions, parameters, imports, classes, and inheritance. By understanding these concepts, you can start writing your
own programs in Python and take advantage of its many features.