---
title: "Binary Search"
datePublished: Wed Jun 26 2024 11:50:13 GMT+0000 (Coordinated Universal Time)
cuid: clxvrx7o600090alcco4o5cq5
slug: binary-search
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719402574646/185c71da-2644-42c0-8287-98bd4bd3e6de.png
tags: search, python, dsa, binary-search-algorithm

---

Binary Search is a way to find an element's position in a sorted array.

In this method, the element is always searched in the middle of a part of the array.

### Code: Iterative Approach

```python
def binary_search(array, x, low, high):

    # Repeat until the pointers low and high meet each other
    while low <= high:

        mid = low + (high - low) // 2

        if array[mid] == x:
            return mid

        elif array[mid] < x:
            low = mid + 1

        else:
            high = mid - 1

    return -1


data = [3, 4, 5, 6, 7, 8, 9]
result = binary_search(data, 4, 0, len(data) - 1)

if result != -1:
    print("Element is present at index " + str(result))
else:
    print("Not found")
```

### Code: Recursive Approach

```python
def binary_search(array, x, low, high):

    if high >= low:

        mid = low + (high - low) // 2

        # If found at mid, then return it
        if array[mid] == x:
            return mid

        # Search the left half
        elif array[mid] > x:
            return binary_search(array, x, low, mid - 1)

        # Search the right half
        else:
            return binary_search(array, x, mid + 1, high)

    else:
        return -1


data = [3, 4, 5, 6, 7, 8, 9]
result = binary_search(data, 4, 0, len(data) - 1)

if result != -1:
    print("Element is present at index " + str(result))
else:
    print("Not found")
```

### Time Complexities

* Best : `O(1)`
    
* Average : `O(log n)`
    
* Worst : `O(log n)`