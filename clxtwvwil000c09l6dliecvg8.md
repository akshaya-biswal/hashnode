---
title: "Bubble Sort"
datePublished: Tue Jun 25 2024 04:33:38 GMT+0000 (Coordinated Universal Time)
cuid: clxtwvwil000c09l6dliecvg8
slug: bubble-sort
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719408085632/a1a9a317-4240-4a5d-b756-2fee05a97cc9.png
tags: python, sorting, dsa, bubble-sort, sorting-algorithms

---

Bubble Sort is an algorithm that sorts an array from the highest value to the lowest value.

The word 'Bubble' comes from how this algorithm works, it makes the highest values 'bubble up'.

**Explanation**

* **Outer Loop:** Goes through each element of the array.
    
* **Inner Loop:** Compares elements in the array. The `-i` part skips the already sorted elements.
    
* **Swapping:** If the current element is bigger than the next one, they are swapped.
    

```python
def bubble_sort(array):
    for i in range(len(array)):
        for j in range(0, len(array) - i - 1):
            if array[j] > array[j + 1]:
                temp = array[j]
                array[j] = array[j + 1]
                array[j + 1] = temp


data = [-2, 45, 0, 11, -9]
bubble_sort(data)
print(data)  # [-9, -2, 0, 11, 45]
```

### Bubble Sort Optimized

* In the above algorithm, all comparisons are made even if the array is already sorted.
    
* To fix this, we can add an extra variable called swapped. If elements are swapped, the value of swapped is set to true. Otherwise, it is set to false.
    
* After an iteration, if there is no swapping, the value of swapped will be false. This means the elements are already sorted, and we don't need more iterations.
    

```python
def bubble_sort(array):
    for i in range(len(array)):
        # keep track of swapping
        swapped = False
        for j in range(0, len(array) - i - 1):
            if array[j] > array[j + 1]:
                temp = array[j]
                array[j] = array[j + 1]
                array[j + 1] = temp
                swapped = True

        if not swapped:
            break


data = [-2, 45, 0, 11, -9]
bubble_sort(data)
print(data)  # [-9, -2, 0, 11, 45]
```