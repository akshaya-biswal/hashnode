---
title: "Bucket Sort"
datePublished: Wed Jun 26 2024 08:29:53 GMT+0000 (Coordinated Universal Time)
cuid: clxvkrkol000008lfci29261b
slug: bucket-sort
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719389345878/82617d81-04b0-4330-b7bb-27b96b6e25be.png
tags: python, sorting, dsa, bucket-sort

---

Bucket Sort is a sorting algorithm that splits the unsorted array into groups called buckets. Each bucket is then sorted.

### How it works

* Put elements into the buckets
    
* Sort the elements in each bucket
    
* Collect elements from each bucket
    

### Code

```python
def bucket_sort(array):
    bucket = []

    # Create empty buckets
    for i in range(len(array)):
        bucket.append([])

    # Insert elements into their respective buckets
    for j in array:
        index_b = int(10 * j)
        bucket[index_b].append(j)

    # Sort the elements of each bucket
    for i in range(len(array)):
        bucket[i] = sorted(bucket[i])

    # Get the sorted elements
    k = 0
    for i in range(len(array)):
        for j in range(len(bucket[i])):
            array[k] = bucket[i][j]
            k += 1
    return array


data = [0.42, 0.32, 0.33, 0.52, 0.37, 0.47, 0.51]
print(bucket_sort(data))  # [0.32, 0.33, 0.37, 0.42, 0.47, 0.51, 0.52]
```

### Explanation

Create empty buckets

```python
# Since array has 7 elements, create 7 empty buckets initially.
bucket = [[], [], [], [], [], [], []]
```

Insert elements into their respective buckets

```python
index_b for each element:
0.42 -> index_b = int(10 * 0.42) = 4 -> bucket[4] -> [0.42]
0.32 -> index_b = int(10 * 0.32) = 3 -> bucket[3] -> [0.32]
0.33 -> index_b = int(10 * 0.33) = 3 -> bucket[3] -> [0.32, 0.33]
0.52 -> index_b = int(10 * 0.52) = 5 -> bucket[5] -> [0.52]
0.37 -> index_b = int(10 * 0.37) = 3 -> bucket[3] -> [0.32, 0.33, 0.37]
0.47 -> index_b = int(10 * 0.47) = 4 -> bucket[4] -> [0.42, 0.47]
0.51 -> index_b = int(10 * 0.51) = 5 -> bucket[5] -> [0.52, 0.51]
```

Sort the elements of each bucket

```python
# Before Sorting
bucket = [[0.32, 0.33, 0.37], [], [], [], [0.42, 0.47], [0.52, 0.51], []]

# After Sorting
bucket = [[0.32, 0.33, 0.37], [], [], [], [0.42, 0.47], [0.51, 0.52], []]
```

Get the sorted elements

```python
# Insert all buckets back into the original array, in order.
[0.32, 0.33, 0.37, 0.42, 0.47, 0.51, 0.52]
```

### Time complexity

* Distributing Elements into Buckets: `O(n)`
    
* Sorting Individual Buckets, if we use insertion sort: `O(nlogn)`
    
* Merging Buckets: `O(n)`
    

`O(n)+O(nlogn)+O(n) = O(nlogn)`