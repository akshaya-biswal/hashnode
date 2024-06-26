---
title: "Linear Search"
datePublished: Wed Jun 26 2024 10:53:24 GMT+0000 (Coordinated Universal Time)
cuid: clxvpw4sg00030amc75bu63ru
slug: linear-search
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719399156879/72a0f5fe-0c59-4735-a88a-22b1f41ceb26.png
tags: search, python, dsa, linearsearch

---

Linear search is a method where we start at one end and check each item in the list until we find the one we want.

```python
def linear_search(arr, target):
    for index, value in enumerate(arr):
        if value == target:
            return index
    return -1


data = [10, 20, 30, 40, 50]
result = linear_search(data, 30)

if result != -1:
    print(f"Element found at index: {result}")
else:
    print("Element not found in the list")
```

### Time Complexity

`O(n)`