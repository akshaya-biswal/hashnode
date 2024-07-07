---
title: "List - Data Structure"
datePublished: Sun Jul 07 2024 07:58:57 GMT+0000 (Coordinated Universal Time)
cuid: clyb9i65h00050ajsgc9p46th
slug: list
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720296100017/a3ca68f8-bbea-431a-aeab-6e61768c0fbc.jpeg
tags: code, python, data-structures, python3, list, codenewbies

---

They are ordered, mutable collections that can hold a variety of object types.

### Creating a List

```python
# Empty list
my_list = []

# List with initial elements
my_list = [1, 2, 3, 4, 5]

# List with mixed data types
my_list = [1, "hello", 3.14, True]
```

### Accessing Elements

```python
my_list = [1, 2, 3, 4, 5]

# Accessing elements by index (0-based)
print(my_list[0])  # Output: 1
print(my_list[4])  # Output: 5

# Negative indexing
print(my_list[-1])  # Output: 5 (last element)
print(my_list[-2])  # Output: 4
```

### Slicing

```python
my_list = [1, 2, 3, 4, 5]

# Slicing the list[start:stop:step]
print(my_list[1:3])   # Output: [2, 3]
print(my_list[:3])    # Output: [1, 2, 3]
print(my_list[3:])    # Output: [4, 5]
print(my_list[::2])   # Output: [1, 3, 5]
print(my_list[::-1])  # Output: [5, 4, 3, 2, 1] (reversed list)
```

### Modifying Lists

```python
my_list = [1, 2, 3, 4, 5]

# Changing a single element
my_list[2] = 10
print(my_list)  # Output: [1, 2, 10, 4, 5]

# Changing a slice
my_list[1:3] = [20, 30]
print(my_list)  # Output: [1, 20, 30, 4, 5]
```

### Adding Elements

```python
my_list = [1, 2, 3, 4, 5]

# append() - Adds an element at the end
my_list.append(6)
print(my_list)  # Output: [1, 2, 3, 4, 5, 6]

# insert() - Inserts an element at a specified index
my_list.insert(2, 10)
print(my_list)  # Output: [1, 2, 10, 3, 4, 5, 6]

# extend() - Extends the list by adding elements from another list
my_list.extend([7, 8])
print(my_list)  # Output: [1, 2, 10, 3, 4, 5, 6, 7, 8]
```

### Removing Elements

```python
my_list = [1, 2, 3, 4, 5, 3]

# remove() - Removes the first occurrence of a value
my_list.remove(3)
print(my_list)  # Output: [1, 2, 4, 5, 3]

# pop() - Removes and returns an element at a given index (default is the last element)
last_element = my_list.pop()
print(last_element)  # Output: 3
print(my_list)       # Output: [1, 2, 4, 5]

# del - Deletes elements by index or slice
del my_list[1]
print(my_list)  # Output: [1, 4, 5]
del my_list[1:3]
print(my_list)  # Output: [1]
```

### Searching for Elements

```python
my_list = [1, 2, 3, 4, 5]

# index() - Returns the index of the first occurrence of a value
print(my_list.index(3))  # Output: 2

# in - Checks if an element exists in the list
print(4 in my_list)  # Output: True
print(6 in my_list)  # Output: False
```

### List Operations

```python
# Concatenation
list1 = [1, 2, 3]
list2 = [4, 5, 6]
combined = list1 + list2
print(combined)  # Output: [1, 2, 3, 4, 5, 6]

# Repetition
repeated = list1 * 3
print(repeated)  # Output: [1, 2, 3, 1, 2, 3, 1, 2, 3]
```

### Useful Methods

```python
my_list = [3, 1, 4, 1, 5, 9]

# len() - Returns the number of elements in the list
print(len(my_list))  # Output: 6

# count() - Counts the number of occurrences of a value
print(my_list.count(1))  # Output: 2

# sort() - Sorts the list in ascending order
my_list.sort()
print(my_list)  # Output: [1, 1, 3, 4, 5, 9]

# reverse() - Reverses the list in place
my_list.reverse()
print(my_list)  # Output: [9, 5, 4, 3, 1, 1]

# sorted() - Returns a new sorted list
sorted_list = sorted(my_list)
print(sorted_list)  # Output: [1, 1, 3, 4, 5, 9]
```

### List Comprehensions

```python
# Basic list comprehension
squares = [x**2 for x in range(1, 6)]
print(squares)  # Output: [1, 4, 9, 16, 25]

# List comprehension with condition
evens = [x for x in range(1, 11) if x % 2 == 0]
print(evens)  # Output: [2, 4, 6, 8, 10]
```