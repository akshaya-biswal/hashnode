---
title: "Insertion Sort"
datePublished: Mon Aug 12 2024 11:01:33 GMT+0000 (Coordinated Universal Time)
cuid: clzqvvnc300020ajjglw5hyty
slug: insertion-sort
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/GZ9aJw1DMBA/upload/07b7ddcbb6d1b6fbeb167b33ba81cb04.jpeg
tags: algorithms, javascript, insertion-sort, sorting, dsa

---

### Introduction

* **Initialization:**
    
    * The function `insertionSort` accepts an array `arr` as its argument.
        
    * `const end = arr.length;` stores the length of the array in the variable `end`.
        
* **Element Comparison:**
    
    * The outer loop starts at the second element (`let start = 1`) and iterates through the array until the end (`start < end`).
        
* **Inner Loop:**
    
    * For each element `arr[start]`, it's stored in the variable `curr`.
        
    * The variable `prev` is initialized to `start - 1`, representing the index of the element before the current element.
        
* **Shifting Elements:**
    
    * The inner `while` loop compares `curr` with the elements before it (`arr[prev]`).
        
    * If `arr[prev]` is greater than `curr`, `arr[prev]` is moved one position ahead to make space for `curr`.
        
    * This continues until `curr` is greater than or equal to `arr[prev]` or `prev` becomes `1`.
        
* **Insertion:**
    
    * Once the correct position is found, `curr` is inserted at that position (`arr[prev + 1]`).
        
* **Returning the Result:**
    
    * After all elements are processed, the sorted array `arr` is returned.
        

```javascript
function insertionSort(arr) {
  const end = arr.length;

  for (let start = 1; start < end; start++) {
    let curr = arr[start];
    let prev = start - 1;

    while (prev >= 0 && arr[prev] > curr) {
      arr[prev + 1] = arr[prev];
      --prev;
    }

    arr[prev + 1] = curr;
  }

  return arr;
}

console.log(insertionSort([9, 5, 1, 4, 3]));
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723459945680/3044a3fa-f5ab-4f00-8fb8-7ab0ee9c17c1.png align="center")