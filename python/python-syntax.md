
# Frequently Used Python Syntax Guide

This guide covers commonly used Python syntax and commands for essential programming tasks.

---

## 1. Print Statement

In Python, `print` is used to output text or variable values to the console.

```python
print('Hello, World!')
```

### Print Multiple Items

Use commas to print multiple items, or format them for more control.

```python
name = "Alice"
age = 30
print("Name:", name, "Age:", age)
print(f"Name: {name}, Age: {age}")  # f-string formatting
```

---

## 2. Working with Lists (Arrays)

### Reverse the List

Reverse the order of elements in a list:

```python
my_list = [1, 2, 3, 4, 5]
my_list.reverse()  # In-place reversal
print(my_list)  # Output: [5, 4, 3, 2, 1]

# Alternative method using slicing
reversed_list = my_list[::-1]
print(reversed_list)
```

### Sort a List

Sort a list in ascending or descending order:

```python
numbers = [5, 2, 9, 1]
numbers.sort()  # Ascending order
print(numbers)

numbers.sort(reverse=True)  # Descending order
print(numbers)
```

---

## 3. Basic String Operations

### Concatenate Strings

Combine strings using `+` or `f-strings`.

```python
greeting = "Hello"
name = "Bob"
message = greeting + ", " + name
print(message)  # Output: "Hello, Bob"

# Using f-string
print(f"{greeting}, {name}")
```

### Convert to Upper and Lower Case

Convert all characters to uppercase or lowercase:

```python
text = "Hello World"
print(text.upper())  # "HELLO WORLD"
print(text.lower())  # "hello world"
```

### Check Substring Presence

```python
text = "Hello World"
if "World" in text:
    print("Found!")
```

---

## 4. Dictionary Operations

### Access and Modify Dictionary Items

```python
person = {"name": "Alice", "age": 30}
print(person["name"])  # Accessing item

person["age"] = 31  # Modifying item
print(person)
```

### Add and Remove Items

```python
person["city"] = "New York"  # Adding item
print(person)

del person["city"]  # Removing item
print(person)
```

### Looping Through Dictionary Keys and Values

```python
for key, value in person.items():
    print(f"{key}: {value}")
```

---

## 5. Functions and Lambda Expressions

### Define and Call a Function

Functions are reusable blocks of code:

```python
def greet(name):
    return f"Hello, {name}"

print(greet("Alice"))
```

### Lambda Functions

Anonymous functions defined with `lambda`.

```python
square = lambda x: x ** 2
print(square(5))  # Output: 25
```

---

## 6. Conditional Statements

### If-Else Conditions

Execute code based on conditions:

```python
x = 10
if x > 5:
    print("x is greater than 5")
else:
    print("x is 5 or less")
```

### Ternary (One-Line If-Else)

```python
status = "Positive" if x > 0 else "Negative"
print(status)
```

---

## 7. Loops

### For Loop

Loop through a range of numbers or items in a list:

```python
for i in range(5):
    print(i)

colors = ["red", "blue", "green"]
for color in colors:
    print(color)
```

### While Loop

Repeat until a condition is met:

```python
count = 0
while count < 5:
    print(count)
    count += 1
```

---

## 8. List Comprehensions

Compact syntax for creating lists:

```python
squares = [x ** 2 for x in range(10)]
print(squares)  # Output: [0, 1, 4, 9, ..., 81]
```

---

## 9. Exception Handling

### Try-Except for Error Handling

Handle errors gracefully:

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
```

---

## 10. Importing Libraries

### Import a Module or Library

Import standard libraries or external packages:

```python
import math
print(math.sqrt(16))  # Output: 4.0
```

### Import Specific Functions

```python
from math import sqrt, pi
print(sqrt(25), pi)  # Output: 5.0, 3.14159...
```

---

## 11. File Handling

### Read a File

```python
with open("file.txt", "r") as file:
    content = file.read()
    print(content)
```

### Write to a File

```python
with open("file.txt", "w") as file:
    file.write("Hello, World!")
```

---

This guide provides an overview of frequently used Python syntax for common tasks like data manipulation, string operations, file handling, and more.
