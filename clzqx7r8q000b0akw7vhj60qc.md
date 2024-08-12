---
title: "Selection Sort"
datePublished: Mon Aug 12 2024 11:38:57 GMT+0000 (Coordinated Universal Time)
cuid: clzqx7r8q000b0akw7vhj60qc
slug: selection-sort
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/lRoX0shwjUQ/upload/0f6132d0014398c989fc268c6dd6a8e3.jpeg
tags: algorithms, javascript, dsa, datastructure, selection-sort

---

### Introduction

1. **Initialization:**
    
    * The function `selectionSort` accepts an array `arr` as its argument.
        
    * The variable `n` stores the length of the array.
        
2. **Outer Loop:**
    
    * The outer loop iterates through each element in the array, treating each element as the starting point.
        
3. **Finding the Minimum:**
    
    * Assume the first element of the unsorted part as the minimum (`minIndex = i`).
        
    * The inner loop starts from the next element (`j = i + 1`) and checks each element to find the smallest one.
        
    * If a smaller element is found, update `minIndex` to the index of that element.
        
4. **Swapping Elements:**
    
    * After finding the minimum element in the unsorted part, swap it with the first element of the unsorted part.
        
    * Only perform the swap if the minimum element is different from the starting element.
        
5. **Return the Result:**
    
    * After all elements are processed, the sorted array `arr` is returned.
        

### Code

```javascript
function selectionSort(arr) {
  const length = arr.length;

  // Loop through each element in the array
  for (let curr = 0; curr < length; curr++) {
    let minIndex = curr;

    // Check the rest of the array for a smaller element
    for (let next = curr + 1; next < length; next++) {
      if (arr[next] < arr[minIndex]) {
        minIndex = next;
      }
    }

    // Swap the minimum element with current index
    if (curr != minIndex) {
      [arr[curr], arr[minIndex]] = [arr[minIndex], arr[curr]];
    }
  }

  return arr;
}

console.log(selectionSort([20, 12, 10, 15, 2]));
```