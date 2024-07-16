---
title: "Leetcode 2963: Count the Number of Good Partitions"
datePublished: Tue Jul 16 2024 20:26:00 GMT+0000 (Coordinated Universal Time)
cuid: clyov5jqn000b09jxdqv57n0s
slug: leetcode-2963-count-the-number-of-good-partitions
tags: javascript, leetcode, two-pointers

---

[Leetcode Link](https://leetcode.com/problems/count-the-number-of-good-partitions/description/)

This algorithm essentially finds the number of good partitions by leveraging the last occurrence indices of elements and a two-pointer technique to identify valid partition points, doubling the number of partitions each time a valid point is found.

### Two-Pointer Technique

* A `while` loop runs until `left` reaches the end of the array.
    
* If `left` surpasses `right`, a partition point is found, and `result` is doubled and taken modulo `MOD`.
    
* Result is multiplied by 2 because once we found a new subarray we have two options.
    
    * it can be added on existing
        
    * it can be treated as separate
        
* `right` is updated to the maximum of its current value and the last occurrence index of the current element.
    
* `left` is incremented to move to the next element.
    

### Code

```javascript
const MOD = 1e9 + 7;

const number_of_good_partitions = (array) => {
  const length = array.length;
  const last_index = new Map();

  // Fill the last index map with the last occurrence of each number
  for (let i = 0; i < array.length; i++) {
    last_index.set(array[i], i);
  }

  let result = 1;

  // Two pointers
  let left = 0;
  let right = Math.max(0, last_index.get(array[0]));

  while (left < length) {
    // we found one partition
    if (left > right) {
      result = (result * 2) % MOD;
    }

    right = Math.max(right, last_index.get(array[left]));
    left++;
  }

  return result;
};

console.log(number_of_good_partitions([1, 2, 3, 4]));
```

**Reference**

Watch video after 18min  
[https://www.youtube.com/watch?v=fyyjpElDeuY&list=PLpIkg8OmuX-LtRw7om1-EV6aJMRKjbSSR&index=8](https://www.youtube.com/watch?v=fyyjpElDeuY&list=PLpIkg8OmuX-LtRw7om1-EV6aJMRKjbSSR&index=8)