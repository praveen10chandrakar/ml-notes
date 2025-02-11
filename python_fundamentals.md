# Module 1: Python Fundamentals

## Overview
This module covers essential Python programming concepts with clear examples and explanations.

## Table of Contents
1. [Basic Python Concepts](#1-basic-python-concepts)
2. [Control Flow](#2-control-flow)
3. [Data Structures](#3-data-structures)
4. [Functions](#4-functions)
5. [Advanced Python Concepts](#5-advanced-python-concepts)
6. [Practice Exercises](#6-practice-exercises)

## 1. Basic Python Concepts

### 1.1 Variables and Data Types
Python is dynamically typed, meaning you don't need to declare variable types explicitly.

```python
# Numbers
integer_num = 42          # Integer
float_num = 3.14         # Float
complex_num = 2 + 3j     # Complex number

# Type conversion
str_num = "123"
converted_int = int(str_num)    # String to integer
converted_float = float("3.14") # String to float

# Strings
text = "Hello, Python!"
multiline = """
This is a
multiline string
"""

# String operations
name = "Python"
print(len(name))         # Length: 6
print(name.upper())      # PYTHON
print(name.lower())      # python
print(name[0:2])        # Py (slicing)

# Boolean
is_valid = True
is_ready = False
result = is_valid and is_ready  # Boolean operations
```

### 1.2 Basic Operators
```python
# Arithmetic operators
x = 10
y = 3
addition = x + y        # 13
subtraction = x - y     # 7
multiplication = x * y  # 30
division = x / y        # 3.333...
floor_division = x // y # 3
modulus = x % y        # 1
power = x ** y         # 1000

# Comparison operators
equals = x == y        # False
not_equals = x != y    # True
greater_than = x > y   # True
less_than = x < y      # False
```

## 2. Control Flow

### 2.1 If-Else Statements
```python
# Basic if-else
number = 5
if number > 0:
    print("Positive")
elif number < 0:
    print("Negative")
else:
    print("Zero")

# Nested if statements
age = 25
has_license = True

if age >= 18:
    if has_license:
        print("Can drive")
    else:
        print("Need license")
else:
    print("Too young to drive")
```

### 2.2 Loops
```python
# For loop with range
for i in range(5):
    print(i)  # Prints 0 to 4

# For loop with list
fruits = ["apple", "banana", "orange"]
for fruit in fruits:
    print(fruit)

# While loop
counter = 0
while counter < 5:
    print(counter)
    counter += 1

# Loop control
for i in range(10):
    if i == 3:
        continue  # Skip 3
    if i == 8:
        break    # Stop at 8
    print(i)
```

## 3. Data Structures

### 3.1 Lists
```python
# Creating lists
numbers = [1, 2, 3, 4, 5]
mixed = [1, "hello", 3.14, True]

# List operations
numbers.append(6)        # Add element
numbers.remove(3)        # Remove element
numbers.insert(0, 0)     # Insert at position
first = numbers[0]       # Indexing
last = numbers[-1]       # Negative indexing
subset = numbers[1:3]    # Slicing

# List comprehension
squares = [x**2 for x in range(5)]
evens = [x for x in range(10) if x % 2 == 0]
```

### 3.2 Dictionaries
```python
# Creating dictionaries
person = {
    "name": "John",
    "age": 30,
    "city": "New York"
}

# Dictionary operations
person["email"] = "john@example.com"  # Add new key-value
del person["age"]                     # Remove key-value
age = person.get("age", 0)           # Safe get with default
keys = person.keys()                 # Get all keys
values = person.values()             # Get all values

# Dictionary comprehension
squares_dict = {x: x**2 for x in range(5)}
```

### 3.3 Sets
```python
# Creating sets
numbers = {1, 2, 3, 4, 5}
more_numbers = {4, 5, 6, 7, 8}

# Set operations
numbers.add(6)                # Add element
numbers.remove(3)             # Remove element
union = numbers | more_numbers        # Union
intersection = numbers & more_numbers # Intersection
difference = numbers - more_numbers   # Difference
```

### 3.4 Tuples
```python
# Creating tuples (immutable)
coordinates = (10, 20)
person = ("John", 30, "New York")

# Tuple operations
x, y = coordinates     # Unpacking
name, age, city = person
first = coordinates[0]  # Indexing
```

## 4. Functions

### 4.1 Basic Functions
```python
# Function definition
def greet(name):
    """Simple greeting function"""
    return f"Hello, {name}!"

# Function with default parameters
def power(base, exponent=2):
    return base ** exponent

# Multiple return values
def divide_mod(a, b):
    return a // b, a % b

# Lambda functions
square = lambda x: x**2
```

### 4.2 Function Arguments
```python
# Positional and keyword arguments
def person_info(name, age, city):
    return f"{name} is {age} years old from {city}"

# Different ways to call
print(person_info("John", 30, "New York"))  # Positional
print(person_info(age=30, name="John", city="New York"))  # Keyword

# Variable arguments
def sum_all(*args):
    return sum(args)

def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")
```

## 5. Advanced Python Concepts

### 5.1 Object-Oriented Programming
```python
# Basic class definition
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    def area(self):
        return self.width * self.height
    
    def perimeter(self):
        return 2 * (self.width + self.height)

# Inheritance
class Square(Rectangle):
    def __init__(self, side):
        super().__init__(side, side)

# Using classes
rect = Rectangle(5, 3)
print(rect.area())        # 15
print(rect.perimeter())   # 16

square = Square(4)
print(square.area())      # 16
```

### 5.2 Error Handling
```python
# Basic try-except
def divide_numbers(a, b):
    try:
        result = a / b
        return result
    except ZeroDivisionError:
        return "Cannot divide by zero"
    except TypeError:
        return "Invalid input types"
    finally:
        print("Division operation completed")

# Custom exceptions
class ValueTooLargeError(Exception):
    """Raised when the input value is too large"""
    pass

def check_value(x):
    if x > 100:
        raise ValueTooLargeError("Value must be less than 100")
    return x
```

### 5.3 Generators and Iterators
```python
# Generator function
def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

# Using generator
fib = fibonacci(5)
for num in fib:
    print(num)    # 0, 1, 1, 2, 3

# Custom iterator
class CountDown:
    def __init__(self, start):
        self.start = start

    def __iter__(self):
        return self

    def __next__(self):
        if self.start <= 0:
            raise StopIteration
        self.start -= 1
        return self.start + 1

# Using iterator
countdown = CountDown(3)
for num in countdown:
    print(num)    # 3, 2, 1
```

### 5.4 Decorators
```python
# Function decorator
def timer(func):
    from time import time
    
    def wrapper(*args, **kwargs):
        start = time()
        result = func(*args, **kwargs)
        end = time()
        print(f"{func.__name__} took {end - start:.2f} seconds")
        return result
    return wrapper

@timer
def slow_function():
    import time
    time.sleep(1)
    return "Done"

# Class decorator
def singleton(cls):
    instances = {}
    
    def get_instance(*args, **kwargs):
        if cls not in instances:
            instances[cls] = cls(*args, **kwargs)
        return instances[cls]
    
    return get_instance
```

### 5.5 Context Managers
```python
# Context manager using class
class FileHandler:
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode
        self.file = None

    def __enter__(self):
        self.file = open(self.filename, self.mode)
        return self.file

    def __exit__(self, exc_type, exc_val, exc_tb):
        if self.file:
            self.file.close()

# Context manager using decorator
from contextlib import contextmanager

@contextmanager
def temporary_file(filename):
    file = open(filename, 'w')
    try:
        yield file
    finally:
        file.close()
```

## 6. Practice Exercises

### Exercise 1: Basic Data Structures
```python
def process_student_grades():
    """
    Create a program that manages student grades using dictionaries and lists.
    Calculate average grades and find top performers.
    """
    students = {
        'John': [85, 90, 88],
        'Alice': [92, 95, 88],
        'Bob': [78, 85, 82]
    }
    
    # Calculate average for each student
    averages = {}
    for student, grades in students.items():
        averages[student] = sum(grades) / len(grades)
    
    # Find top performer
    top_student = max(averages, key=averages.get)
    
    return averages, top_student

# Test the function
averages, top_student = process_student_grades()
print(f"Averages: {averages}")
print(f"Top student: {top_student}")
```

### Exercise 2: Object-Oriented Programming
```python
class BankAccount:
    """
    Implement a bank account class with deposit, withdraw, and balance check.
    Include error handling for insufficient funds.
    """
    def __init__(self, owner, initial_balance=0):
        self.owner = owner
        self.balance = initial_balance
        self.transactions = []

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            self.transactions.append(f"Deposit: +{amount}")
            return True
        return False

    def withdraw(self, amount):
        if amount > 0 and amount <= self.balance:
            self.balance -= amount
            self.transactions.append(f"Withdrawal: -{amount}")
            return True
        return False

    def get_balance(self):
        return self.balance

    def get_transaction_history(self):
        return self.transactions

# Test the BankAccount class
account = BankAccount("John Doe", 1000)
account.deposit(500)
account.withdraw(200)
print(f"Balance: {account.get_balance()}")
print(f"Transactions: {account.get_transaction_history()}")
```

### Exercise 3: Advanced Concepts
```python
def create_data_processor():
    """
    Create a program that demonstrates generators, decorators, and context managers.
    Process data in chunks efficiently.
    """
    @contextmanager
    def data_loader(filename):
        file = open(filename, 'r')
        try:
            yield file
        finally:
            file.close()

    def chunk_generator(data, chunk_size):
        for i in range(0, len(data), chunk_size):
            yield data[i:i + chunk_size]

    @timer
    def process_data(filename, chunk_size=100):
        results = []
        with data_loader(filename) as file:
            data = file.readlines()
            for chunk in chunk_generator(data, chunk_size):
                # Process each chunk
                results.extend([line.strip().upper() for line in chunk])
        return results

    return process_data

# Test the data processor
processor = create_data_processor()
# processor('data.txt')  # Uncomment to test with actual file
```

## Summary
This module covered:
- Python fundamentals and basic syntax
- Control flow and data structures
- Functions and their advanced usage
- Object-oriented programming concepts
- Advanced Python features
- Practical exercises for reinforcement

## Next Steps
- Practice the exercises
- Explore the Python standard library
- Learn about modules and packages
- Start working on real-world projects 
