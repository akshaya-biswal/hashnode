---
title: "Leetcode 1877: Minimize Maximum Pair Sum in Array"
datePublished: Sun Jul 14 2024 19:03:11 GMT+0000 (Coordinated Universal Time)
cuid: clylxbc2h000a0amaanuy42ez
slug: leetcode-1877-minimize-maximum-pair-sum-in-array
tags: javascript, coding, leetcode, two-pointers

---

[Leetcode Link](https://leetcode.com/problems/minimize-maximum-pair-sum-in-array/description/)

we need to pair the elements in a way that minimizes the maximum pair sum.

### Steps

1. **Sort the Array**: First, sort the array in ascending order.
    
2. **Pair Elements**: Pair the smallest element with the largest element, the second smallest with the second largest, and so on.
    
3. **Calculate Pair Sums**: Calculate the sums of these pairs.
    
4. **Find the Maximum Sum**: The answer will be the maximum sum of these pairs.
    

### Code

```javascript
const min_pair_sum = (array) => {
  array.sort((a, b) => a - b);

  let max_pair_sum = 0;
  let left = 0;
  let right = array.length - 1;

  while (left < right) {
    const current_sum = array[left] + array[right];
    max_pair_sum = Math.max(max_pair_sum, current_sum);
    left++;
    right--;
  }

  return max_pair_sum;
};

console.log(min_pair_sum([3, 5, 2, 3])); // 7
console.log(min_pair_sum([3, 5, 4, 2, 4, 6])); // 8
```

### Explanation

* **Sorting**: The array is sorted in ascending order. For example, if the input is `[3, 5, 2, 3]`, the sorted array will be `[2, 3, 3, 5]`.
    
* **Pairing**: We pair the smallest with the largest, second smallest with the second largest, etc. In the example, pairs would be `(2, 5)` and `(3, 3)`.
    
* **Calculating Sums**: For each pair, we calculate the sum:
    
    * `(2, 5)` gives `7`
        
    * `(3, 3)` gives `6`
        
* **Maximum Pair Sum**: We find the maximum of these sums. In this example, the maximum pair sum is `7`.
    

### Time Complexity

The time complexity of the `min_pair_sum` function is determined by two main operations:

1. **Sorting the array**: The array is sorted using the `sort()` method, which has a time complexity of `O(nlog⁡n)`, where `n` is the number of elements in the array.
    
2. **Iterating through the array**: After sorting, we use a while loop to iterate through the array to find the maximum pair sum. This loop runs `O(n/2)` times, which simplifies to `O(n)`.
    

Therefore, the overall time complexity is: `O(nlog⁡n) + O(n) = O(nlog⁡n)`

### Space Complexity

The space complexity of the `min_pair_sum` function is determined by the additional space used by the algorithm:

1. **Sorting the array**: The in-place sorting algorithm typically requires `O(log⁡n)` additional space.
    
2. **Pointers and variables**: We use a few variables (`left`, `right`, and `maxPairSum`), which require `O(1)` space.
    

Thus, the overall space complexity is: `O(log⁡n)+O(1)=O(log⁡n)`