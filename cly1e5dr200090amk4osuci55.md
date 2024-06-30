---
title: "Python: Complete Tutorial in One Go"
datePublished: Sun Jun 30 2024 10:11:17 GMT+0000 (Coordinated Universal Time)
cuid: cly1e5dr200090amk4osuci55
slug: python
tags: python, programmer

---

## Variables

Variables are containers for storing data values

Variables do not need to be declared with any particular type, and can even change type after they have been set

String variables can be declared either by using single or double quotes

Variable names are case-sensitive

```python
name = "Hello"
Name = "World"
name = 100
print(name)
```

### Casting

If you want to specify the data type of a variable, this can be done with casting. but the type can be changed after wards

```python
x = str(3)  # '3'
y = int(3)  # 3
z = float(3)  # 3.0
```

### Get the type

```python
x = 5
y = "John"
print(type(x))
print(type(y))
```

### Assign Multiple Values

```python
x, y, z = "Orange", "Banana", "Cherry"
print(x, y, z)

p = q = r = "Go->home"
print(p, q, r)

laptop = ["Apple", "Microsoft", "Linux"]
m, n, o = laptop
print(m, n, o)
```

### Global Variables

Variables that are created outside of a function are known as global variables

```python
feeling = "awesome"

def fn():
    print("Python is " + feeling)

fn()
```

### The global Keyword

```python
def fn():
    global x
    x = "fantastic"

fn()
print("Python is " + x)
```

## Data Types

Variables can store data of different types, and different types can do different things.

<table><tbody><tr><td colspan="1" rowspan="1"><p>Numeric</p></td><td colspan="1" rowspan="1"><p><code>int</code>, <code>float</code>, <code>complex</code></p></td></tr><tr><td colspan="1" rowspan="1"><p>String</p></td><td colspan="1" rowspan="1"><p><code>str</code></p></td></tr><tr><td colspan="1" rowspan="1"><p>Sequence</p></td><td colspan="1" rowspan="1"><p><code>list</code>, <code>tuple</code>, <code>range</code></p></td></tr><tr><td colspan="1" rowspan="1"><p>Mapping</p></td><td colspan="1" rowspan="1"><p><code>dict</code></p></td></tr><tr><td colspan="1" rowspan="1"><p>Set</p></td><td colspan="1" rowspan="1"><p><code>set</code>, <code>frozenset</code></p></td></tr><tr><td colspan="1" rowspan="1"><p>Boolean</p></td><td colspan="1" rowspan="1"><p><code>bool</code></p></td></tr><tr><td colspan="1" rowspan="1"><p>Binary</p></td><td colspan="1" rowspan="1"><p><code>bytes</code>, <code>bytearray</code>, <code>memoryview</code></p></td></tr><tr><td colspan="1" rowspan="1"><p>None</p></td><td colspan="1" rowspan="1"><p><code>NoneType</code></p></td></tr></tbody></table>

### Numeric

```python
x = 20
x = 20.10
x = 1j

# Random
import random
print("random", random.randrange(1, 10))
```

### String

```python
# String
str = "Hello World"

# Strings are Arrays
print(str[0])

# Looping Through a String
for i in str:
    print(i)

# String Length
print("String Length", len(str))

# Check String
print("Hello" in str)  # True
print("hello" in str)  # False

# Modify
print(str.upper())
print(str.lower())
print(str.title())
print(str.strip())
print(str.split(" "))

# Sequence
x = ["apple", "banana", "cherry"]
x = ("apple", "banana", "cherry")
x = range(6)
print(x)

# Format
age = 36
print(f"My name is John, I am {age}")
print(f"My name is John, I am {age + 1}")
print(f"My name is John, I am {age:.2f}")

# Single and double quotes
txt = 'We are the so-called "Vikings" from the north.'
print(txt)
```

### Booleans

```python
print(10 > 9)
print(10 == 9)
print(10 < 9)
```

### Lists

It is a collection which is ordered and changeable. Allows duplicate members.

```python
mylist = ["apple", "banana", "cherry"]
```

### Tuple

* It is a collection which is ordered and unchangeable.
    
* Allows duplicate members.
    

### Set

* It a collection which is unordered, unchangeable, and unindexed.
    
* No duplicate members.
    

### Dictionaries

* It is a collection which is ordered and changeable.
    
* No duplicate members.