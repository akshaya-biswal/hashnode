---
title: "Counting Sort"
datePublished: Wed Jun 26 2024 03:35:22 GMT+0000 (Coordinated Universal Time)
cuid: clxva8tv500010alchsr2hgex
slug: counting-sort
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719370983237/c1159d3c-4fcf-464e-b2a1-f1b8023857b7.jpeg
tags: python, sorting, dsa, counting-sort

---

The Counting Sort algorithm sorts an array by counting how often each value appears.

### How it works

1. Create a new array to count the different values.
    
2. Go through the array that needs sorting.
    
3. For each value, increase the count in the counting array at the matching index.
    
4. After counting the values, go through the counting array to make the sorted array.
    
5. For each count in the counting array, add the right number of elements with values matching the counting array index.
    

```python
def countingSort(arr):
    max_val = max(arr)
    count = [0] * (max_val + 1)

    for num in arr:
        count[num] += 1

    sorted_arr = []
    for i in range(len(count)):
        sorted_arr.extend([i] * count[i])

    return sorted_arr


data = [4, 2, 2, 6, 3, 3, 1, 6, 5, 2, 3]
sorted_arr = countingSort(data)
print(sorted_arr)  # [1, 2, 2, 2, 3, 3, 3, 4, 5, 6, 6]
```

### **Explanation**

Find the Maximum Value and Create the Count Array:

```python
max_val = max(arr) # 6
count = [0] * (max_val + 1) # [0, 0, 0, 0, 0, 0, 0]
```

Populating the Count Array

```python
for num in arr:
    count[num] += 1
print(count) # [0, 1, 3, 3, 1, 1, 2]
```

Creating the Sorted Array

```python
    sorted_arr = []
    for i in range(len(count)):
        sorted_arr.extend([i] * count[i])
```

### Detailed Iteration

```python
# Iteration over count array

# ---------- For i = 0 ----------

count[0] = 0  # No 0s in the input array
sorted_arr.extend([0] * 0)  # No change
sorted_arr = []

# ---------- For i = 1 ----------
count[1] = 1  # One 1 in the input array
sorted_arr.extend([1] * 1)  # Add one 1 to sorted_arr
sorted_arr = [1]

# ---------- For i = 2 ----------
count[2] = 3  # Three 2s in the input array
sorted_arr.extend([2] * 3)  # Add three 2s to sorted_arr
sorted_arr = [1, 2, 2, 2]

# ---------- For i = 3 ----------
count[3] = 3  # Three 3s in the input array
sorted_arr.extend([3] * 3)  # Add three 3s to sorted_arr
sorted_arr = [1, 2, 2, 2, 3, 3, 3]

# ---------- For i = 4 ----------
count[4] = 1  # One 4 in the input array
sorted_arr.extend([4] * 1)  # Add one 4 to sorted_arr
sorted_arr = [1, 2, 2, 2, 3, 3, 3, 4]

# ---------- For i = 5 ----------
count[5] = 1  # One 5 in the input array
sorted_arr.extend([5] * 1)  # Add one 5 to sorted_arr
sorted_arr = [1, 2, 2, 2, 3, 3, 3, 4, 5]

# ---------- For i = 6 ----------
count[6] = 2  # Two 6s in the input array
sorted_arr.extend([6] * 2)  # Add two 6s to sorted_arr
sorted_arr = [1, 2, 2, 2, 3, 3, 3, 4, 5, 6, 6]
```

### Time Complexities

* Finding the maximum value: `O(n)`
    
* Creating the count array: `O(k)`
    
* Populating the count array: `O(n)`
    
* Creating the sorted array: `O(n+k)`
    

Combining these: `O(n)+O(k)+O(n)+O(n+k)=O(n+k)`

In all cases, the complexity is the same because no matter how the elements are placed in the array, the algorithm goes through `n+k` times.

* Worst: `O(n+k)`
    
* Best: `O(n+k)`
    
* Average: `O(n+k)`