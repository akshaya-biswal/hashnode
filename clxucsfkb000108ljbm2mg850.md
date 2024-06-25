---
title: "Merge Sort: A Complete Guide"
datePublished: Tue Jun 25 2024 11:58:50 GMT+0000 (Coordinated Universal Time)
cuid: clxucsfkb000108ljbm2mg850
slug: merge-sort-a-complete-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719339531538/86d16007-5a02-4de5-8f5d-b799262e2984.png
tags: python, dsa, merge-sort

---

The Merge Sort algorithm is a divide-and-conquer algorithm that sorts an array by breaking it into smaller parts and then putting it back together in the right order.

**How it works:**

1. Divide the unsorted array into two sub-arrays, half the size of the original
    
2. Keep dividing the smaller arrays until each piece has only one element
    
3. Merge two small arrays by always placing the smallest value first
    
4. Continue merging until there are no sub-arrays left
    

```python
def merge_sort(array):
    if len(array) <= 1:
        return array

    # Find the middle point and divide the array
    mid = len(array) // 2
    left = array[:mid]
    right = array[mid:]

    # Recursively sort the halves
    left_sorted = merge_sort(left)
    right_sorted = merge_sort(right)

    return merge(left_sorted, right_sorted)


data = [12, 11, 13, 5, 6, 7]
sorted_data = merge_sort(data)
print(sorted_data)
```

```python
def merge(left, right):
    merged = []
    i = j = 0

    # Merge the two arrays while comparing elements
    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            merged.append(left[i])
            i += 1
        else:
            merged.append(right[j])
            j += 1

    # If there are remaining elements in the left array, add them
    while i < len(left):
        merged.append(left[i])
        i += 1

    # If there are remaining elements in the right array, add them
    while j < len(right):
        merged.append(right[j])
        j += 1

    return merged
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719339618741/0ec14a63-7939-45ed-b75b-c711bd556057.png align="center")

**Time Complexity:** O(n\*logn)