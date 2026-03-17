# 🐍 Python - Complete Beginner's Revision Guide

> Master Python from basics to advanced with explanations + code + output 🎯

---

## 1. 📌 Introduction to Python

**Python** = Simple, powerful, readable programming language

**Why Python?**
- ✅ Easy to learn & read (simple syntax)
- ✅ Used everywhere (web, data science, AI, automation)
- ✅ Huge community & libraries
- ✅ Highly demanded in placements

**Python vs Others:**
| Language | Use Case | Difficulty |
|---|---|---|
| Python | Data science, AI, automation | Easy |
| Java | Backend, enterprise apps | Medium |
| C++ | Gaming, system software | Hard |
| JavaScript | Web frontend | Easy |

---

## 2. 💾 Variables & Data Types

### Variables:
```python
name = "Alice"
age = 25
height = 5.7
is_student = True

print(name)      # Output: Alice
print(age)       # Output: 25
print(height)    # Output: 5.7
print(is_student) # Output: True
```

> 💡 Python automatically detects data type — no need to declare

### Data Types:

| Type | Example | Use |
|---|---|---|
| `int` | `10`, `-5`, `0` | Whole numbers |
| `float` | `3.14`, `-2.5` | Decimal numbers |
| `str` | `"hello"`, `'text'` | Text |
| `bool` | `True`, `False` | True/False |
| `list` | `[1, 2, 3]` | Ordered, changeable |
| `tuple` | `(1, 2, 3)` | Ordered, unchangeable |
| `dict` | `{"key": "value"}` | Key-value pairs |
| `set` | `{1, 2, 3}` | Unique items, unordered |

```python
# Check type
print(type(10))         # Output: <class 'int'>
print(type(3.14))       # Output: <class 'float'>
print(type("hello"))    # Output: <class 'str'>
print(type([1, 2, 3]))  # Output: <class 'list'>
```

### Type Casting:
```python
# Convert between types
num = int("42")         # "42" → 42
text = str(100)         # 100 → "100"
decimal = float(5)      # 5 → 5.0
is_true = bool(1)       # 1 → True
is_false = bool(0)      # 0 → False

print(num, text, decimal, is_true, is_false)
# Output: 42 100 5.0 True False
```

---

## 3. 🔧 Operators

### Arithmetic:
```python
a, b = 10, 3

print(a + b)      # 13 (addition)
print(a - b)      # 7  (subtraction)
print(a * b)      # 30 (multiplication)
print(a / b)      # 3.333... (division → float)
print(a // b)     # 3  (floor division → int)
print(a % b)      # 1  (modulo → remainder)
print(a ** b)     # 1000 (power)
```

### Comparison:
```python
print(10 > 5)     # True
print(10 == 5)    # False
print(10 != 5)    # True
print(10 >= 5)    # True
print(10 <= 5)    # False
```

### Logical:
```python
print(True and False)   # False
print(True or False)    # True
print(not True)         # False

# Real example
age = 25
is_employed = True
if age >= 18 and is_employed:
    print("Can apply for loan")
# Output: Can apply for loan
```

### Assignment:
```python
x = 5
x += 3      # x = x + 3 → 8
x -= 2      # x = x - 2 → 6
x *= 2      # x = x * 2 → 12
x /= 3      # x = x / 3 → 4.0
x //= 2     # x = x // 2 → 2
```

---

## 4. 📝 Strings

### Creating Strings:
```python
single = 'Hello'
double = "World"
multi = """This is a
multi-line
string"""

print(single)   # Output: Hello
print(double)   # Output: World
print(multi)    # Output: This is a
                #         multi-line
                #         string
```

### String Methods:
```python
text = "Hello World"

print(text.lower())         # hello world
print(text.upper())         # HELLO WORLD
print(text.capitalize())    # Hello world
print(text.replace("World", "Python"))  # Hello Python
print(text.split())         # ['Hello', 'World']
print(text.startswith("Hello"))  # True
print(text.endswith("World"))    # True
print(len(text))            # 11 (length)
print("Hello" in text)      # True (contains)
```

### String Indexing & Slicing:
```python
text = "Python"
#       012345 (indices)

print(text[0])      # P (first char)
print(text[5])      # n (last char)
print(text[-1])     # n (last char using -1)
print(text[0:3])    # Pyt (chars 0,1,2)
print(text[2:])     # thon (from index 2 to end)
print(text[:3])     # Pyt (from start to index 2)
print(text[::2])    # Pto (every 2nd character)
```

### String Formatting:
```python
name = "Alice"
age = 25
score = 95.5

# Method 1: f-string (modern, best)
print(f"Name: {name}, Age: {age}, Score: {score:.1f}")
# Output: Name: Alice, Age: 25, Score: 95.5

# Method 2: format()
print("Name: {}, Age: {}".format(name, age))
# Output: Name: Alice, Age: 25

# Method 3: % formatting (old)
print("Name: %s, Age: %d" % (name, age))
# Output: Name: Alice, Age: 25
```

---

## 5. 📊 Lists

### Creating Lists:
```python
numbers = [1, 2, 3, 4, 5]
mixed = [1, "hello", 3.14, True]
empty = []

print(numbers)      # [1, 2, 3, 4, 5]
print(mixed)        # [1, 'hello', 3.14, True]
```

### List Operations:
```python
lst = [1, 2, 3]

lst.append(4)           # [1, 2, 3, 4] - add at end
lst.insert(0, 0)        # [0, 1, 2, 3, 4] - add at position
lst.extend([5, 6])      # [0, 1, 2, 3, 4, 5, 6] - add multiple
lst.remove(3)           # Remove first occurrence of 3
lst.pop()               # Remove and return last item
lst.pop(0)              # Remove and return item at index 0
lst.clear()             # Remove all items
lst.sort()              # Sort in ascending order
lst.reverse()           # Reverse order
lst.count(2)            # Count occurrences
lst.index(2)            # Find index of item
```

### List Indexing & Slicing:
```python
lst = [10, 20, 30, 40, 50]

print(lst[0])       # 10
print(lst[-1])      # 50
print(lst[1:4])     # [20, 30, 40]
print(lst[::2])     # [10, 30, 50] (every 2nd)
```

### List Comprehension:
```python
# Create list of squares
squares = [x**2 for x in range(5)]
print(squares)      # [0, 1, 4, 9, 16]

# With condition
evens = [x for x in range(10) if x % 2 == 0]
print(evens)        # [0, 2, 4, 6, 8]
```

---

## 6. 🗂️ Tuples

Tuples are **immutable** (can't change after creation).

```python
coordinates = (10, 20)
rgb = (255, 128, 0)

print(coordinates[0])   # 10
print(len(rgb))         # 3

# Unpacking
x, y = coordinates
print(x, y)             # 10 20

# Immutable — can't change
# rgb[0] = 100  # ❌ ERROR
```

### When to use:
- **List:** When data changes
- **Tuple:** When data is constant/fixed

```python
# Function returns multiple values (tuple)
def get_student():
    return "Alice", 25, "Delhi"

name, age, city = get_student()
print(f"{name} is {age} from {city}")
# Output: Alice is 25 from Delhi
```

---

## 7. 🔤 Dictionaries

Key-value pairs (like maps/objects in other languages).

```python
student = {
    "name": "Alice",
    "age": 25,
    "city": "Delhi",
    "gpa": 3.8
}

print(student["name"])      # Alice
print(student["age"])       # 25
print(student.get("city"))  # Delhi
print(student.get("email", "Not Found"))  # Not Found (default)

# Add/update
student["email"] = "alice@example.com"
student["age"] = 26

# Remove
del student["city"]  # Remove key
student.pop("email") # Remove and return value

# Iterate
for key in student:
    print(key, student[key])

# All keys
print(student.keys())       # dict_keys(['name', 'age', 'gpa', ...])

# All values
print(student.values())     # dict_values(['Alice', 26, 3.8, ...])

# Key-value pairs
print(student.items())      # dict_items([('name', 'Alice'), ...])
```

---

## 8. 📦 Sets

Unordered, unique items. **Duplicates removed automatically**.

```python
colors = {1, 2, 3, 2, 1}
print(colors)       # {1, 2, 3} (duplicates removed)

# Add items
colors.add(4)       # {1, 2, 3, 4}

# Remove items
colors.remove(2)    # {1, 3, 4}
colors.discard(5)   # No error if doesn't exist

# Set operations
a = {1, 2, 3}
b = {2, 3, 4}

print(a | b)        # {1, 2, 3, 4} - union
print(a & b)        # {2, 3} - intersection
print(a - b)        # {1} - difference
print(a ^ b)        # {1, 4} - symmetric difference
```

---

## 9. 🔁 Loops

### While Loop:
```python
count = 0
while count < 3:
    print(f"Count: {count}")
    count += 1

# Output:
# Count: 0
# Count: 1
# Count: 2
```

### For Loop:
```python
# Loop through list
for item in [1, 2, 3]:
    print(item)

# Loop with range
for i in range(3):      # 0, 1, 2
    print(i)

for i in range(1, 4):   # 1, 2, 3
    print(i)

for i in range(0, 10, 2): # 0, 2, 4, 6, 8 (step by 2)
    print(i)

# Loop with index
fruits = ["apple", "banana", "cherry"]
for idx, fruit in enumerate(fruits):
    print(f"{idx}: {fruit}")

# Output:
# 0: apple
# 1: banana
# 2: cherry
```

### Break & Continue:
```python
for i in range(5):
    if i == 2:
        break       # Exit loop
    print(i)        # 0, 1

for i in range(5):
    if i == 2:
        continue    # Skip this iteration
    print(i)        # 0, 1, 3, 4
```

---

## 10. ❓ Conditionals

### If-Else:
```python
age = 18

if age < 13:
    print("Child")
elif age < 18:
    print("Teen")
else:
    print("Adult")

# Output: Adult
```

### Ternary Operator:
```python
status = "Pass" if score >= 50 else "Fail"

# Same as:
if score >= 50:
    status = "Pass"
else:
    status = "Fail"
```

---

## 11. 🔧 Functions

### Basic Function:
```python
def greet(name):
    """This function greets someone"""
    return f"Hello, {name}!"

result = greet("Alice")
print(result)       # Hello, Alice!
```

### Default Parameters:
```python
def add(a, b=5):    # b has default value
    return a + b

print(add(10))      # 15 (uses default b=5)
print(add(10, 20))  # 30 (overrides b)
```

### Multiple Return Values:
```python
def get_student():
    return "Alice", 25, "Delhi"

name, age, city = get_student()
print(name, age, city)  # Alice 25 Delhi
```

### *args (Variable Arguments):
```python
def sum_all(*args):
    total = 0
    for num in args:
        total += num
    return total

print(sum_all(1, 2, 3, 4))      # 10
print(sum_all(5, 10))            # 15
```

### **kwargs (Keyword Arguments):
```python
def print_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

print_info(name="Alice", age=25, city="Delhi")
# Output:
# name: Alice
# age: 25
# city: Delhi
```

### Combined:
```python
def full_function(a, b, *args, **kwargs):
    print(f"a={a}, b={b}")
    print(f"args={args}")
    print(f"kwargs={kwargs}")

full_function(1, 2, 3, 4, name="Alice", age=25)
# Output:
# a=1, b=2
# args=(3, 4)
# kwargs={'name': 'Alice', 'age': 25}
```

---

## 12. 📚 Classes & Objects

### Basic Class:
```python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def introduce(self):
        return f"Hi, I'm {self.name}, age {self.age}"

alice = Student("Alice", 25)
print(alice.introduce())        # Hi, I'm Alice, age 25
```

### Class vs Instance:
```python
class Car:
    wheels = 4      # Class variable (shared by all)
    
    def __init__(self, color):
        self.color = color  # Instance variable (unique)

car1 = Car("red")
car2 = Car("blue")

print(car1.color)       # red
print(car2.color)       # blue
print(Car.wheels)       # 4 (same for both)
```

### Methods:
```python
class BankAccount:
    def __init__(self, balance):
        self.balance = balance
    
    def deposit(self, amount):
        self.balance += amount
        return f"Deposited: {amount}, Balance: {self.balance}"
    
    def withdraw(self, amount):
        if amount <= self.balance:
            self.balance -= amount
            return f"Withdrawn: {amount}, Balance: {self.balance}"
        else:
            return "Insufficient balance"

account = BankAccount(1000)
print(account.deposit(500))     # Deposited: 500, Balance: 1500
print(account.withdraw(200))    # Withdrawn: 200, Balance: 1300
```

### Inheritance:
```python
class Animal:
    def speak(self):
        return "Some sound"

class Dog(Animal):
    def speak(self):
        return "Woof!"

class Cat(Animal):
    def speak(self):
        return "Meow!"

dog = Dog()
cat = Cat()
print(dog.speak())      # Woof!
print(cat.speak())      # Meow!
```

### Special Methods:
```python
class Student:
    def __init__(self, name):
        self.name = name
    
    def __str__(self):
        return f"Student: {self.name}"
    
    def __repr__(self):
        return f"Student('{self.name}')"
    
    def __len__(self):
        return len(self.name)

s = Student("Alice")
print(str(s))           # Student: Alice
print(repr(s))          # Student('Alice')
print(len(s))           # 5
```

---

## 13. 🔍 File Operations

### Read File:
```python
# Read entire file
with open("file.txt", "r") as f:
    content = f.read()
    print(content)

# Read line by line
with open("file.txt", "r") as f:
    for line in f:
        print(line.strip())

# Read all lines as list
with open("file.txt", "r") as f:
    lines = f.readlines()
```

### Write File:
```python
# Write (overwrites if exists)
with open("file.txt", "w") as f:
    f.write("Hello World\n")
    f.write("Line 2\n")

# Append (adds to end)
with open("file.txt", "a") as f:
    f.write("Line 3\n")
```

### File Modes:
| Mode | Purpose |
|---|---|
| `"r"` | Read (default) |
| `"w"` | Write (overwrites) |
| `"a"` | Append (add to end) |
| `"x"` | Create (fails if exists) |
| `"b"` | Binary mode (images, etc.) |

---

## 14. 🐛 Error Handling

### Try-Except:
```python
try:
    num = int("abc")  # Error!
except ValueError:
    print("Invalid number")

# Output: Invalid number
```

### Multiple Exceptions:
```python
try:
    result = 10 / 0  # Error!
except ValueError:
    print("Invalid value")
except ZeroDivisionError:
    print("Can't divide by zero")

# Output: Can't divide by zero
```

### Finally:
```python
try:
    f = open("file.txt", "r")
    content = f.read()
except FileNotFoundError:
    print("File not found")
finally:
    f.close()  # Always runs
```

### Raise Exception:
```python
age = 10
if age < 18:
    raise ValueError("Must be 18+")
```

---

## 15. 🎁 Lambda & Map/Filter

### Lambda (Anonymous Function):
```python
# Regular function
def add(a, b):
    return a + b

# Lambda function
add = lambda a, b: a + b

print(add(5, 3))        # 8
```

### Map (Apply function to all items):
```python
numbers = [1, 2, 3, 4]

# Double each number
doubled = list(map(lambda x: x * 2, numbers))
print(doubled)          # [2, 4, 6, 8]

# Same with list comprehension (preferred)
doubled = [x * 2 for x in numbers]
```

### Filter (Keep items matching condition):
```python
numbers = [1, 2, 3, 4, 5, 6]

# Keep even numbers
evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)            # [2, 4, 6]

# Same with list comprehension (preferred)
evens = [x for x in numbers if x % 2 == 0]
```

---

## 16. 📦 Modules & Imports

### Built-in Modules:
```python
import math
print(math.sqrt(16))    # 4.0
print(math.pi)          # 3.14159...

import random
print(random.randint(1, 10))    # Random number 1-10
print(random.choice([1, 2, 3])) # Random item from list

import datetime
now = datetime.datetime.now()
print(now)              # 2024-03-17 15:30:45.123456

import os
print(os.getcwd())      # Current directory
```

### Import Specific:
```python
from math import sqrt, pi, floor
print(sqrt(16))         # 4.0
print(pi)               # 3.14159...

from random import choice
print(choice([1, 2, 3]))
```

### Alias:
```python
import numpy as np
import pandas as pd
from datetime import datetime as dt
```

---

## 17. 💾 JSON

```python
import json

# Python to JSON
data = {
    "name": "Alice",
    "age": 25,
    "skills": ["Python", "JavaScript"]
}

json_string = json.dumps(data)  # Dict → JSON string
print(json_string)

# Save to file
with open("data.json", "w") as f:
    json.dump(data, f)

# Load from file
with open("data.json", "r") as f:
    loaded_data = json.load(f)
    print(loaded_data)
```

---

## 18. 🔤 Regular Expressions

```python
import re

text = "My email is alice@example.com and bob@test.org"

# Find all emails
emails = re.findall(r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b', text)
print(emails)           # ['alice@example.com', 'bob@test.org']

# Replace
new_text = re.sub(r'@\S+', '@hidden.com', text)
print(new_text)         # My email is alice@hidden.com and bob@hidden.com

# Match pattern
if re.match(r'\d{10}', "9876543210"):
    print("Valid phone")
```

---

## 19. 📋 Decorators

```python
def my_decorator(func):
    def wrapper():
        print("Before function")
        func()
        print("After function")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
# Output:
# Before function
# Hello!
# After function
```

---

## 20. 🎯 List of Important Methods

### String Methods:
```
.upper() .lower() .capitalize() .strip() .split() .join()
.replace() .find() .startswith() .endswith() .count()
```

### List Methods:
```
.append() .insert() .remove() .pop() .clear() .sort()
.reverse() .count() .index() .extend()
```

### Dictionary Methods:
```
.keys() .values() .items() .get() .pop() .update()
.clear() .copy()
```

### Set Methods:
```
.add() .remove() .discard() .clear() .union() .intersection()
.difference() .issubset() .issuperset()
```

---

## 📋 Quick Summary Table

| # | Concept | Syntax | Example |
|---|---|---|---|
| 1 | Variable | `name = value` | `x = 10` |
| 2 | List | `[item1, item2]` | `[1, 2, 3]` |
| 3 | Tuple | `(item1, item2)` | `(1, 2, 3)` |
| 4 | Dict | `{key: value}` | `{"name": "Alice"}` |
| 5 | Set | `{item1, item2}` | `{1, 2, 3}` |
| 6 | If-Else | `if cond: ... else:` | `if x > 5: print("big")` |
| 7 | For Loop | `for item in list:` | `for x in [1,2,3]: print(x)` |
| 8 | While Loop | `while condition:` | `while x < 10: x += 1` |
| 9 | Function | `def name(args):` | `def add(a,b): return a+b` |
| 10 | Class | `class Name: def __init__` | `class Car: ...` |

---

## 🧠 Placement Interview Questions

1. **List vs Tuple - difference?**
   - List is mutable, Tuple is immutable
   
2. **What are different data types in Python?**
   - int, float, str, bool, list, tuple, dict, set

3. **How to reverse a list?**
   - `lst.reverse()` or `lst[::-1]`

4. **What's the difference between append and extend?**
   - append adds one item, extend adds multiple items

5. **Explain list comprehension**
   - `[x*2 for x in range(5)]` creates list with single line

6. **What does *args do?**
   - Allows function to accept variable number of arguments

7. **What's the difference between **kwargs?**
   - Allows function to accept keyword arguments as dictionary

8. **Explain OOP concepts**
   - Classes, objects, inheritance, polymorphism, encapsulation

9. **What are lambda functions?**
   - Anonymous functions: `lambda x: x*2`

10. **How to handle exceptions?**
    - Use try-except-finally blocks

11. **What's the difference between == and is?**
    - `==` compares values, `is` compares memory address

12. **Explain decorators**
    - Functions that modify other functions/classes

13. **What are built-in functions?**
    - `len()`, `type()`, `range()`, `enumerate()`, `zip()`, `map()`, `filter()`

14. **How to read/write files?**
    - Use `open()` with `with` statement

15. **What's the GIL in Python?**
    - Global Interpreter Lock prevents true parallelism in threading

---

> 💡 **Tip:** Practice writing code daily → understand each concept → solve problems → repeat! 🚀
