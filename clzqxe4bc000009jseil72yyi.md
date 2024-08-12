---
title: "Bucket Sort"
datePublished: Mon Aug 12 2024 11:43:54 GMT+0000 (Coordinated Universal Time)
cuid: clzqxe4bc000009jseil72yyi
slug: bucket-sort
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/gBaXljNA6HI/upload/681ec3b87115e893280ad18360838348.jpeg
tags: javascript, sorting, dsa, bucket-sort

---

Bucket Sort is a distribution sort that divides the elements into several buckets, sorts each bucket individually, and then combines the sorted buckets to get the final sorted array.

### Introduction

1. **Edge Case Check:**
    
    * If the input array is empty, return it immediately.
        
2. **Determine Range:**
    
    * Find the minimum and maximum values in the array using `Math.min(...arr)` and `Math.max(...arr)`.
        
3. **Initialize Buckets:**
    
    * Calculate the number of buckets needed based on the range of the elements and the `bucketSize`.
        
    * Create an array of buckets, where each bucket is an empty array.
        
4. **Distribute Elements:**
    
    * Iterate through the input array and place each element into the appropriate bucket based on its value.
        
5. **Sort Buckets:**
    
    * Sort each bucket individually. Here, the built-in `Array.prototype.sort()` method is used for simplicity.
        
6. **Concatenate Buckets:**
    
    * Combine the sorted buckets back into the original array.
        
7. **Return Sorted Array:**
    
    * Return the sorted array.
        

### Code - Without using ES6

```javascript
function bucketSort(arr, bucketSize = 5) {
  if (arr.length === 0) {
    return arr;
  }

  // Determine minimum and maximum values
  let minValue = Math.min(...arr);
  let maxValue = Math.max(...arr);

  // Initialize buckets
  let bucketCount = Math.floor((maxValue - minValue) / bucketSize) + 1;
  let buckets = new Array(bucketCount);
  
  for (let i = 0; i < buckets.length; i++) {
    buckets[i] = [];
  }

  // Distribute input array values into buckets
  arr.forEach(element => {
    let bucketIndex = Math.floor((element - minValue) / bucketSize);
    buckets[bucketIndex].push(element);
  });

  // Sort each bucket and concatenate the results
  arr.length = 0;
  
  for (let i = 0; i < buckets.length; i++) {
    if (buckets[i].length > 0) {
      buckets[i].sort((a, b) => a - b); // Sort individual bucket using any sorting algorithm
      arr.push(...buckets[i]);
    }
  }

  return arr;
}

// Example usage:
console.log(bucketSort([42, 32, 33, 52, 37, 47, 51])); // [32, 33, 37, 42, 47, 51, 52]
```

### Code - Using ES6

```javascript
function bucketSort(arr) {
  const bucketCount = arr.length;
  const buckets = Array.from({ length: bucketCount }, () => []);

  // Add elements to buckets
  arr.forEach((element) => {
    const index = Math.floor(element * bucketCount);
    buckets[index].push(element);
  });

  // Sort each bucket and concatenate them
  return buckets.flatMap((bucket) => bucket.sort((a, b) => a - b));
}

const arr = [0.42, 0.32, 0.33, 0.52, 0.37, 0.47, 0.51];
console.log(bucketSort(arr));
```