# Technical Paper & Cheat Sheet on Python Core Concepts

## Table of Contents

1. Array (List) Methods
2. String Methods
3. Objects and Object-Oriented Programming (OOP)
4. SOLID Principles in Python

## Introduction

Python is a powerful and easy-to-learn programming language known for its clear and simple syntax.
It allows developers to work quickly and efficiently while writing readable and organized code.
This content explains how to handle data using lists and strings, introduces the basics of Object-Oriented Programming (OOP), and covers the SOLID principles that help in writing clean, reusable, and maintainable Python programs.

## 1. Array (List) Methods

In Python, arrays are typically represented as lists — dynamic, mutable sequences that can hold elements of different types.

### Python List Methods

| **Method**    | **Description**                        | **Example**             |
|----------------|----------------------------------------|--------------------------|
| `append(x)`    | Adds element `x` to the end of list     | `nums.append(10)`        |
| `extend(iterable)` | Adds all elements from another iterable | `nums.extend([4,5,6])`  |
| `insert(i, x)` | Inserts `x` at index `i`               | `nums.insert(2, 99)`     |
| `remove(x)`    | Removes first occurrence of `x`        | `nums.remove(3)`         |
| `pop([i])`     | Removes and returns element at index `i` | `nums.pop(1)`          |
| `index(x)`     | Returns index of `x`                   | `nums.index(4)`          |
| `count(x)`     | Counts occurrences of `x`              | `nums.count(5)`          |
| `sort()`       | Sorts list in ascending order          | `nums.sort()`            |
| `reverse()`    | Reverses order of elements             | `nums.reverse()`         |
| `copy()`       | Returns a shallow copy                 | `new_list = nums.copy()` |
| `clear()`      | Removes all items                      | `nums.clear()`           |

#### Example:
``` python
nums = [3, 1, 4, 2]
nums.append(5)
nums.sort()
print(nums)  # Output: [1, 2, 3, 4, 5]
```

## 2. String Methods

Strings in Python are immutable sequences of characters.
They support numerous built-in methods for text manipulation and formatting.

### Common String Methods


| **Method**            | **Description**                         | **Example**                          |
|------------------------|------------------------------------------|--------------------------------------|
| `upper()`              | Converts to uppercase                    | `"hello".upper()` → `"HELLO"`        |
| `lower()`              | Converts to lowercase                    | `"HELLO".lower()` → `"hello"`        |
| `title()`              | Capitalizes first letter of each word    | `"python guide".title()`             |
| `capitalize()`         | Capitalizes first character              | `"hello".capitalize()`               |
| `strip()`              | Removes whitespace                       | `" hi ".strip()`                     |
| `replace(old, new)`    | Replaces substring                       | `"hi".replace("h", "H")`             |
| `split(sep)`           | Splits string into list                  | `"a,b,c".split(",")`                 |
| `join(iterable)`       | Joins list into string                   | `",".join(['a','b','c'])`            |
| `startswith(sub)`      | Checks prefix                            | `"Python".startswith("Py")`          |
| `endswith(sub)`        | Checks suffix                            | `"file.txt".endswith(".txt")`        |
| `find(sub)`            | Returns index of substring               | `"hello".find("e")`                  |
| `count(sub)`           | Counts occurrences                       | `"banana".count("a")`                |


#### Example:
``` python
text = " Python Programming "
clean = text.strip().upper().replace(" ", "_")
print(clean)  # Output: PYTHON_PROGRAMMING
```

## 3. Objects and Object-Oriented Programming (OOP)

### What are Objects?
In Python, **everything is an object** — numbers, strings, lists, functions, and even classes.  
An **object** is something that has **data (attributes)** and **behavior (methods)**.  
For example, a car has attributes like *color* and *brand*, and behaviors like *start()* or *stop()*.

---

### What is a Class?
A **class** is like a **blueprint** or **template** used to create objects.  
It defines what data (attributes) and actions (methods) an object will have.

Think of a class as a plan for building something, and an object as the actual thing built from that plan.

---

#### Example of Class and Object

```python
class Car:
    def __init__(self, brand, color):   # Constructor - initializes object data
        self.brand = brand              # Attribute
        self.color = color              # Attribute

    def start(self):                    # Method (behavior)
        print(f"{self.brand} car started!")

# Creating an object from the class
car1 = Car("Tesla", "Red")
car1.start()   # Output: Tesla car started!
```

### Core OOP Concepts

| **Concept**      | **Description**                           | **Example**                     |
|------------------|--------------------------------------------|----------------------------------|
| **Encapsulation** | Wrapping data & methods together           | Private attributes using `_` or `__` |
| **Abstraction**   | Hiding implementation details              | Using abstract base classes       |
| **Inheritance**   | Acquiring properties from a parent class   | `class Dog(Animal)`               |
| **Polymorphism**  | Same method behaving differently           | Method overriding                 |

 #### Example: Abstract Classes and Polymorphism

```python

from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def sound(self):
        pass

class Dog(Animal):
    def sound(self):
        return "Bark"

class Cat(Animal):
    def sound(self):
        return "Meow"

for animal in [Dog(), Cat()]:
    print(animal.sound())  # Output: Bark  Meow

```

## 4. SOLID Principles in Python

The SOLID principles are design guidelines that help developers build maintainable, scalable, and robust object-oriented software.

### 4.1 Single Responsibility Principle (SRP)

The **Single Responsibility Principle (SRP)** states that a class should have **only one reason to change** —  
each class should handle **only one responsibility**.

#### Example :

``` python
## (wrong) Violates SRP

class Report:
    def generate(self):
        pass
    def save_to_file(self):
        pass  # Saving logic belongs elsewhere

## (correct) Follows SRP
class Report:
    def generate(self):
        pass

class FileSaver:
    def save(self, report):
        pass
```

### 4.2 Open/Closed Principle (OCP)

Classes should be open for extension but closed for modification.

#### Example:

``` python
class Shape:
    def area(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
    def area(self):
        return 3.14 * self.radius ** 2

class Square(Shape):
    def __init__(self, side):
        self.side = side
    def area(self):
        return self.side ** 2
```

### 4.3 Liskov Substitution Principle (LSP)
Subclasses should be replaceable with their base classes without breaking the code.

#### Example:
``` python
class Bird:
    def fly(self):
        return "Flying"

class Sparrow(Bird):
    pass

def make_it_fly(bird: Bird):
    print(bird.fly())

make_it_fly(Sparrow()) 
```
### 4.4 Interface Segregation Principle (ISP)

No Clients should not be forced to depend on methods they don’t use. Splits large interfaces into specific ones.

#### Example:
``` python 
from abc import ABC, abstractmethod

class Printer(ABC):
    @abstractmethod
    def print_doc(self):
        pass

class Scanner(ABC):
    @abstractmethod
    def scan_doc(self):
        pass
```
### 4.5 Dependency Inversion Principle (DIP)

Depend on **abstractions**, not on **concrete implementations**.  
High-level modules should not depend on low-level modules.  
Both should depend on **abstractions (interfaces or abstract classes)**, and **abstractions should not depend on details — details should depend on abstractions**.

#### Example:

``` python
class Database(ABC):
    @abstractmethod
    def connect(self):
        pass

class MySQL(Database):
    def connect(self):
        print("Connected to MySQL")

class Application:
    def __init__(self, db: Database):
        self.db = db
    def start(self):
        self.db.connect()

app = Application(MySQL())
app.start()  # Output: Connected to MySQL

```

## References
```
• Programiz Python Guide: https://www.programiz.com/python-programming
```

```
• W3Schools Python Reference: https://www.w3schools.com/python/
```
• Python Array Tutorial: https://www.youtube.com/watch?v=nlP5kF1_efE
• Python Array(List) Methods Tutorial: https://www.youtube.com/watch?v=phRshQSU-xA&t;=607s
• Python Strings Tutorial: https://www.youtube.com/watch?v=Ctqi5Y4X-jA
• Python String Methods Tutorial: https://www.youtube.com/watch?v=ANgYwq9fFQw
• Python OOPS Tutorial: https://www.youtube.com/watch?v=qiSCMNBIP2g
• Python Solid Principies Tutorial: https://www.youtube.com/watch?v=pTB30aXS77U&t=50s , https://www.youtube.com/watch?v=B87DCLmrtT8
