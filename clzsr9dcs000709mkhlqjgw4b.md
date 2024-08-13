---
title: "Binary Search"
datePublished: Tue Aug 13 2024 18:27:47 GMT+0000 (Coordinated Universal Time)
cuid: clzsr9dcs000709mkhlqjgw4b
slug: binary-search
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1723575290733/0c7d5448-d560-4170-b276-3e3efae27889.png
tags: algorithms, javascript, dsa, binary-search-algorithm, datast

---

### Introduction

* Binary search is an efficient searching algorithm used to find the position of a target element in a **sorted** list or array.
    
* It works by repeatedly dividing the search interval in half and comparing the target element with the middle element of the current interval.
    
* Binary search is much faster than linear search for large datasets but requires the list to be sorted.
    

### Code - Using Loop

```javascript
const binarySearch = (arr, target) => {
  let left = 0;
  let right = arr.length - 1;

  while (left <= right) {
    const mid = Math.floor((left + right) / 2);

    if (arr[mid] === target) return mid;

    arr[mid] < target ? (left = mid + 1) : (right = mid - 1);
  }
  return -1;
};

console.log(binarySearch([2, 3, 4, 5, 7, 8], 7));
```

### Code - Using Recursion

```javascript
const binarySearch = (arr, target, left = 0, right = arr.length - 1) => {
  if (left > right) return -1;

  const mid = Math.floor((left + right) / 2);

  if (arr[mid] === target) return mid;

  if (arr[mid] < target) {
    return binarySearch(arr, target, mid + 1, right);
  } else {
    return binarySearch(arr, target, left, mid - 1);
  }
};

console.log(binarySearch([2, 3, 4, 5, 7, 8], 7));
```

### **Complexity**

* **Time Complexity**: O(log n), where n is the number of elements in the list. This makes it significantly faster than linear search for large datasets.
    
* **Space Complexity**: O(1) for the iterative version, as it only requires a few variables for tracking indices.