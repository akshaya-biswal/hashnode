---
title: "Radix Sort"
datePublished: Mon Aug 12 2024 12:33:58 GMT+0000 (Coordinated Universal Time)
cuid: clzqz6i3v000408l0digv6wqe
slug: radix-sort
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/InD2tBJODcM/upload/58f9ade4636cd07c71c9fdc5ffebf004.jpeg
tags: algorithms, javascript, data-structures, sorting, dsa, radix-sort

---

### Introduction

1. **getDigit(num, place):**
    
    * Returns the digit at the specified place value in the number.
        
    * Example: `getDigit(1234, 0)` returns `4`, `getDigit(1234, 1)` returns `3`.
        
2. **digitCount(num):**
    
    * Returns the number of digits in the given number.
        
    * Example: `digitCount(1234)` returns `4`, `digitCount(7)` returns `1`.
        
3. **mostDigits(nums):**
    
    * Returns the maximum number of digits in any number from the array.
        
    * Example: `mostDigits([1234, 56, 7])` returns `4`.
        
4. **radixSort(arrOfNums):**
    
    * Sorts the array of numbers using the Radix Sort algorithm.
        
    * For each digit place value (starting from the least significant digit to the most significant digit), the numbers are grouped into buckets based on the digit at the current place value.
        
    * The buckets are then concatenated to form the new order of the array for the next iteration.
        
    * This process continues until all digit places are processed.
        

### Code

```javascript
function getDigit(num, place) {
  return Math.floor(Math.abs(num) / Math.pow(10, place)) % 10;
}

function digitCount(num) {
  if (num === 0) return 1;
  return Math.floor(Math.log10(Math.abs(num))) + 1;
}

function mostDigits(nums) {
  let maxDigits = 0;
  for (let i = 0; i < nums.length; i++) {
    maxDigits = Math.max(maxDigits, digitCount(nums[i]));
  }
  return maxDigits;
}

function radixSort(arrOfNums) {
  let maxDigitCount = mostDigits(arrOfNums);
  for (let k = 0; k < maxDigitCount; k++) {
    let digitBuckets = Array.from({ length: 10 }, () => []); // [[], [], [],...]
    for (let i = 0; i < arrOfNums.length; i++) {
      let digit = getDigit(arrOfNums[i], k);
      digitBuckets[digit].push(arrOfNums[i]);
    }
    // New order after each loop
    arrOfNums = [].concat(...digitBuckets);
  }
  return arrOfNums;
}

console.log(radixSort([1, 33, 444, 0, 3, 2])); // [0, 1, 2, 3, 33, 444]
```

### Visualisation of the Process

1. **Initial Array:**`[1, 33, 444, 0, 3, 2]`
    
2. **Sorting by Units Place (k = 0):**
    
    * Buckets: `[ [0], [1], [2], [3], [], [], [], [], [], [33, 444] ]`
        
    * Concatenated: `[0, 1, 2, 3, 33, 444]`
        
3. **Sorting by Tens Place (k = 1):**
    
    * Buckets: `[ [0, 1, 2, 3], [], [], [33], [], [], [], [], [], [444] ]`
        
    * Concatenated: `[0, 1, 2, 3, 33, 444]`
        
4. **Sorting by Hundreds Place (k = 2):**
    
    * Buckets: `[ [0, 1, 2, 3, 33], [], [], [], [444], [], [], [], [], [] ]`
        
    * Concatenated: `[0, 1, 2, 3, 33, 444]`
        
5. The final sorted array is `[0, 1, 2, 3, 33, 444]`, as expected.