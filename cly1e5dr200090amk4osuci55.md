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

| Numeric | `int`, `float`, `complex` |
| --- | --- |
| String | `str` |
| Sequence | `list`, `tuple`, `range` |
| Mapping | `dict` |
| Set | `set`, `frozenset` |
| Boolean | `bool` |
| Binary | `bytes`, `bytearray`, `memoryview` |
| None | `NoneType` |

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
countries = ["India", "Sri Lanka", "Nepal"]

print(len(countries))  # 3

print(type(countries))  # list

print(countries[0])  # India
print(countries[-1])  # Nepal

print(countries[0:2])  # ['India', 'Sri Lanka']
print(countries[:1])  # ['India']
print(countries[1:])  # ['Sri Lanka', 'Nepal']

if "India" in countries:
    print("Greatest!!!")

# Change
countries[2] = "Bhutan"
print(countries)  # ['India', 'Sri Lanka', 'Bhutan']

# Add
countries.insert(3, "Nepal")  # At index
print(countries)  # ['India', 'Sri Lanka', 'Bhutan', 'Nepal']

countries.append("UK")  # At end
print(countries)  # ['India', 'Sri Lanka', 'Bhutan', 'Nepal', 'UK']

countries.append("USA")  # At end
print(countries)  # ['India', 'Sri Lanka', 'Bhutan', 'Nepal', 'UK', 'USA']

# Remove
countries.remove("UK")
print(countries)  # ['India', 'Sri Lanka', 'Bhutan', 'Nepal', 'USA']

countries.pop(1)  # At specified index
print(countries)  # ['India', 'Bhutan', 'Nepal', 'USA']

countries.pop()  # At end
print(countries)  # ['India', 'Bhutan', 'Nepal']

countries.clear()
print(countries)  # []

# Loop - Values
fruits = ["apple", "banana", "cherry"]
for x in fruits:
    print(x)

# Loop - Index and Values
for i in range(len(fruits)):
    print(i, fruits[i])

# Comprehension: create a new list based on the values of an existing list
new_fruits1 = [x for x in fruits if "a" in x]
new_fruits2 = [x for x in fruits if x != "apple"]
new_fruits3 = [x.upper() for x in fruits]
new_fruits4 = ["hello" for x in fruits]

print(new_fruits1, new_fruits2, new_fruits3, new_fruits4)
# ['apple', 'banana'] ['banana', 'cherry'] ['APPLE', 'BANANA', 'CHERRY'] ['hello', 'hello', 'hello']

countries = ["India", "Sri Lanka", "Nepal"]
countries.sort()
print(countries)  # ['India', 'Nepal', 'Sri Lanka']

countries.sort(reverse=True)
print(countries)  # ['Sri Lanka', 'Nepal', 'India']

# Copy
languages = ["Python", "JavaScript", "HTML", "CSS"]
languages_copy1 = languages.copy()
languages_copy2 = list(languages)
print(languages_copy1, languages_copy2)

# Join
list1 = ["a", "b", "c"]
list2 = [1, 2, 3]

list1.extend(list2)
print(list1)  # ['a', 'b', 'c', 1, 2, 3]

# count: returns the number of elements with the specified value.
x = list1.count("a")
print(x)  # 1

# index: returns the position at the first occurrence
y = list1.index("a")
print(y)  # 0

# reverse
fruits = ["apple", "banana", "cherry"]
fruits.reverse()
```

### Tuple

* It is a collection which is ordered and unchangeable.
    
* Allows duplicate members.
    

```python
days = ("Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday")
print(type(days))

# Access
print(days[0])  # Monday

# Length
print(len(days))  # 7

# Range
print(days[0:5])  # ('Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday')

# Is exist
if "January" in days:
    print("Yes, 'January' is in the days tuple")
else:
    print("No, 'January' is't in the days tuple")


# Change
fruits = ("apple", "banana", "cherry")

fruits_list = list(fruits)
fruits_list[1] = "kiwi"
fruits = tuple(fruits_list)

print(fruits)  # ('apple', 'kiwi', 'cherry')

# Remove
fruits = ("apple", "banana", "cherry")

fruits_list = list(fruits)
fruits_list.remove("cherry")
fruits = tuple(fruits_list)

print(fruits)  # ('apple', 'banana')

# Delete
fruits = ("apple", "banana", "cherry")
del fruits
# print(fruits) # error, it's no longer exists


# Unpacking
fruits = ("apple", "banana", "cherry")
(green, yellow, red) = fruits

# Loop - items
fruits = ("apple", "banana", "cherry")
for x in fruits:
    print(x)

# Loop - items and index
for i in range(len(fruits)):
    print(fruits[i])

# Join
tuple1 = ("a", "b", "c")
tuple2 = (1, 2, 3)

tuple3 = tuple1 + tuple2
print(tuple3)  # ('a', 'b', 'c', 1, 2, 3)

# Count
num = (1, 3, 7, 8, 7, 5, 4, 6, 8, 5)
x = num.count(5)
print(x)  # 2

# Index
num = (1, 3, 7, 8, 7, 5, 4, 6, 8, 5)
x = num.index(5)
print(x)  # 5
```

### Set

* It a collection which is unordered, unchangeable, and unindexed.
    
* Sets are unordered, so you cannot be sure in which order the items will appear.
    
* Set items are unchangeable, but you can remove items and add new items.
    
* No duplicate members.
    
* The values `True` and `1` are considered the same value in sets, and are treated as duplicates.
    

### Dictionaries

* It is a collection which is ordered and changeable.
    
* No duplicate members.