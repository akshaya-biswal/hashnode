---
title: "Leetcode 26: Remove Duplicates from Sorted Array"
datePublished: Sun Jul 14 2024 05:36:56 GMT+0000 (Coordinated Universal Time)
cuid: clyl4ihso00000al7hplzb9kp
slug: leetcode-26-remove-duplicates-from-sorted-array
tags: code, javascript, leetcode, two-pointers

---

To remove duplicates from a sorted array in JavaScript, we can use a `Two Pointer` approach, which is efficient with a time complexity of O(n).

### Code

```javascript
function removeDuplicates(array) {
  if (array.length === 0) return 0;

  let uniqueIndex = 0;

  for (let i = 1; i < array.length; i++) {
    if (array[i] !== array[uniqueIndex]) {
      uniqueIndex++;
      array[uniqueIndex] = array[i];
    }
  }

  return array.slice(0, uniqueIndex + 1);
}

console.log(removeDuplicates([0, 0, 1, 1, 1, 2, 2, 3, 3, 4]));
// [ 0, 1, 2, 3, 4 ]
```

### Explanation

1. **Initial Check**: If the array is empty, return 0 as there are no elements to process.
    
2. **Pointers Initialization**:
    
    * `uniqueIndex` is initialized to 0, representing the position of the last unique element found.
        
    * Start iterating from the second element (index 1) because the first element is always unique.
        
3. **Loop through Array**:
    
    * For each element, compare it with the element at `uniqueIndex`.
        
    * If the current element is different from the element at `uniqueIndex`, increment `uniqueIndex` and update the value at `uniqueIndex` to the current element.
        
4. **Return**: After processing all elements, return an array using slice method `uniqueIndex + 1`, which is the number of unique elements in the array.