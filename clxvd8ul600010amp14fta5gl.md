---
title: "Radix Sort"
datePublished: Wed Jun 26 2024 04:59:22 GMT+0000 (Coordinated Universal Time)
cuid: clxvd8ul600010amp14fta5gl
slug: radix-sort
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719377883906/f0f1aee6-4992-48d0-a710-01a591a9d6ed.png
tags: python, sorting, dsa, radix-sort

---

The Radix Sort algorithm sorts an array by each digit, starting with the rightmost digit, and usually works with positive numbers.

### How it works

1. Start with the least significant digit (rightmost digit).
    
2. Sort the values based on the digit in focus by first putting the values in the correct bucket based on the digit in focus, and then put them back into array in the correct order.
    
3. Move to the next digit, and sort again, like in the step above, until there are no digits left.
    

### Code

```python
def radix_sort(arr):
    # Initialize the radix array with 10 buckets (0-9)
    radixArray = [[], [], [], [], [], [], [], [], [], []]

    # Find the maximum value in the array to determine number of passes
    maxVal = max(arr)

    # Start with the least significant digit (units place)
    exp = 1

    # Loop until all digits are sorted
    while maxVal // exp > 0:

        # Distribute elements into buckets based on the current digit (exp)
        while len(arr) > 0:
            val = arr.pop()
            radixIndex = (val // exp) % 10
            radixArray[radixIndex].append(val)

        # Collect elements from buckets back into the original array
        for bucket in radixArray:
            while len(bucket) > 0:
                val = bucket.pop()
                arr.append(val)

        # Move to the next digit (next significant place value)
        exp *= 10


data = [170, 45, 75, 90, 802, 24, 2, 66]
radix_sort(data)
print(data)
```

### Explanation

```python
# exp = 1
radixArray = [[170, 90], [], [802, 2], [], [24], [45, 75], [66], [], [], []]
arr = [170, 90, 802, 2, 24, 45, 75, 66]

# exp = 10
radixArray = [[802, 2], [], [24], [], [45], [], [66], [170, 75], [], [90]]
arr = [802, 2, 24, 45, 66, 170, 75, 90]

# exp = 100
radixArray = [[2, 24, 45, 66, 75, 90], [170], [], [], [], [], [], [], [802], []]
arr = [2, 24, 45, 66, 75, 90, 170, 802]
```