---
title: "Quick Sort: A Beginner's Tutorial"
datePublished: Tue Jun 25 2024 19:24:46 GMT+0000 (Coordinated Universal Time)
cuid: clxuspwx500000amd9avt7lir
slug: quick-sort
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719343383431/9ca20456-c557-48f6-8d35-f6b6bd1ff79a.png
tags: python, sorting, quick-sort, dsa

---

As the name suggests, Quicksort is one of the fastest sorting algorithms.

* The pivot element is placed between a sub-array with lower values on the left side and a sub-array with higher values on the right side.
    
* The algorithm calls itself twice, once for the sub-array on the left side and once for the sub-array on the right side.
    
* It keeps calling itself until the sub-arrays are too small to sort.
    

```python
def quick_sort(arr):
    quick_sort_recursive(arr, 0, len(arr) - 1)
    return arr
```

```python
def quick_sort_recursive(arr, low, high):
    if low < high:
        pi = partition(arr, low, high)
        quick_sort_recursive(arr, low, pi - 1)
        quick_sort_recursive(arr, pi + 1, high)
```

* It first checks if `low` is less than `high` to ensure there are at least two elements to sort.
    
* It calls the `partition()` to get the pivot index (`pi`).
    
* It recursively sorts the elements before and after the pivot.
    

```python
def partition(arr, low, high):
    pivot = arr[high]
    i = low - 1  # Index of smaller element
    for j in range(low, high):
        if arr[j] < pivot:
            i += 1
            arr[i], arr[j] = arr[j], arr[i]
    arr[i + 1], arr[high] = arr[high], arr[i + 1]
    return i + 1
```

* It selects the pivot element as the last element in the sub-array `arr[high]`.
    
* It initializes the index of the smaller element `i` to `low - 1`.
    
* It iterates through the sub-array from `low` to `high - 1`.
    
    * If an element is smaller than the pivot, it increments `i` and swaps the element at `i` with the element at `j`.
        
* After the loop, it swaps the pivot element with the element at `i + 1`.
    
* It returns the index of the pivot element after partitioning.