---
title: "Counting Sort"
datePublished: Mon Aug 12 2024 11:35:08 GMT+0000 (Coordinated Universal Time)
cuid: clzqx2use00060alabrrp8z55
slug: counting-sort
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/i3rBo3b9QbA/upload/908a72060f0ce342fbe83ad72a227225.jpeg
tags: algorithms, javascript, sorting, dsa, counting-sort

---

### Introduction

1. **Edge Case Check:**
    
    * If the input array is empty, return it immediately.
        
2. **Find Maximum Element:**
    
    * Use `Math.max(...arr)` to find the maximum value in the array. This will help in determining the size of the count array.
        
3. **Initialize Count Array:**
    
    * Create a count array of size `max + 1` (to accommodate the maximum value) and initialize all elements to `0`.
        
4. **Count Occurrences:**
    
    * Iterate through the input array and increment the count of each element in the count array.
        
5. **Reconstruct Sorted Array:**
    
    * Iterate through the count array and place each element at its correct position in the original array. Decrement the count for each element placed.
        
6. **Return Sorted Array:**
    
    * Return the sorted array.
        

### Code

```javascript
function countingSort(arr) {
  // If the array is empty, return it
  if (arr.length === 0) return arr;

  // Find the maximum element in the array to determine the size of the count array
  const max = Math.max(...arr);

  // Create a count array with size max + 1, initialized to zeros
  const count = new Array(max + 1).fill(0);

  // Count the occurrences of each element in the input array
  for (const num of arr) {
    count[num]++;
  }

  // Reconstruct the sorted array using the count array
  let index = 0; // Index for placing elements in the original array
  for (let i = 0; i < count.length; i++) {
    while (count[i] > 0) {
      arr[index++] = i;
      count[i]--;
    }
  }

  // Return the sorted array
  return arr;
}

// Example usage:
console.log(countingSort([4, 2, 2, 8, 3, 3, 1])); // [1, 2, 2, 3, 3, 4, 8]
```