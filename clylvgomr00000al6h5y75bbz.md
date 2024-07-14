---
title: "Leetcode 1498: Number of Subsequences That Satisfy the Given Sum Condition"
datePublished: Sun Jul 14 2024 18:11:21 GMT+0000 (Coordinated Universal Time)
cuid: clylvgomr00000al6h5y75bbz
slug: leetcode-1498-number-of-subsequences-that-satisfy-the-given-sum-condition
tags: code, javascript, leetcode, two-pointers

---

[Leetcode Link](https://leetcode.com/problems/number-of-subsequences-that-satisfy-the-given-sum-condition/description/)

### Code

```javascript
const MOD = 1e9 + 7;

const pre_compute_powers = (length) => {
  const pow = Array(length).fill(1);
  for (let i = 1; i < length; i++) {
    pow[i] = (pow[i - 1] * 2) % MOD;
  }
  return pow;
};

const num_of_subsequence = (array, target) => {
  array.sort((a, b) => a - b);

  let result = 0;
  let left = 0;
  let right = array.length - 1;

  const pow = pre_compute_powers(array.length);

  while (left <= right) {
    if (array[left] + array[right] <= target) {
      result = (result + pow[right - left]) % MOD;
      left++;
    } else {
      right--;
    }
  }

  return result;
};

console.log(num_of_subsequence([3, 5, 6, 7], 9)); // 4
console.log(num_of_subsequence([3, 3, 6, 8], 10)); // 6
console.log(num_of_subsequence([2, 3, 3, 4, 6, 7], 12)); // 61
```

### Explanation

**Precompute Function**:

* `pre_compute_powers(length)` takes the length of the array.
    
* It initializes an array `pow` with `1`s.
    
* It iterates from `1` to `length - 1` to fill the array with powers of 2 modulo `mod`.
    

**Main Function**:

* **Sort the array**: Sorting helps in using the two-pointer approach effectively.
    
* **Initialize variables**:
    
    * `MOD` constant and `pow` array
        
    * `result` to store the number of valid subsequences.
        
    * `left` and `right` pointers.
        
* **Precompute powers of 2**: This is used to count subsequences efficiently.
    
* **While loop:**
    
    * If we use `left < right`, the loop would miss the case where `left` and `right` point to the same element.
        
    * Using `<=` ensures that all elements are considered, including cases where `left` and `right` might end up pointing to the same element after some iterations.
        
* **Two-pointer approach**:
    
    * If `nums[left] + nums[right]` is less than or equal to `target`
        
        * all subsequences between `left` and `right` are valid. The number of such subsequences is `2^(right - left)` which is `pow[right - left]`.
            
        * Add this count to `result` and move the `left` pointer to the right.
            
    * If the sum is greater than `target`, move the `right` pointer to the left to reduce the sum.
        
* **Return the result**: The final count of valid subsequences modulo.
    

### Step-by-Step Calculation

* **Input and Sorting**:
    
    * Input array: `[3, 5, 6, 7]`
        
    * Target: `9`
        
    * Sorted array: `[3, 5, 6, 7]`
        
* **Initialize Pointers and Precompute Powers of 2**:
    
    * `left = 0`
        
    * `right = 3`
        
    * Precompute powers of 2 modulo
        
        * `pow[0] = 1`
            
        * `pow[1] = 2`
            
        * `pow[2] = 4`
            
        * `pow[3] = 8`
            
* **Two-Pointer Approach**:
    
    * **First Iteration**:
        
        * `nums[left] = 3`
            
        * `nums[right] = 7`
            
        * `3 + 7 = 10`, which is greater than the target `9`.
            
        * Move `right` pointer to the left: `right = 2`.
            
    * **Second Iteration**:
        
        * `nums[left] = 3`
            
        * `nums[right] = 6`
            
        * `3 + 6 = 9`, which is equal to the target `9`.
            
        * All subsequences between `left` and `right` are valid.
            
        * Number of valid subsequences: `2^(right - left) = 2^(2 - 0) = 4`.
            
        * Add this count to the result: `result = 0 + 4 = 4`.
            
        * Move `left` pointer to the right: `left = 1`.
            
    * **Third Iteration**:
        
        * `nums[left] = 5`
            
        * `nums[right] = 6`
            
        * `5 + 6 = 11`, which is greater than the target `9`.
            
        * Move `right` pointer to the left: `right = 1`.
            
    * **Fourth Iteration**:
        
        * `nums[left] = 5`
            
        * `nums[right] = 5`
            
        * `5 + 5 = 10`, which is greater than the target `9`.
            
        * Move `right` pointer to the left: `right = 0`.
            
* **Termination**:
    
    * The loop terminates because `left` is no longer less than or equal to `right`.
        

### Time Complexity:

* Sorting the array takes `O(nlog⁡n)`, where `n` is the length of the array.
    
* Precomputing powers of 2 takes `O(n)` time, where `n` is the length of the array.
    
* The two-pointer approach takes `O(n)` time, where `n` is the length of the array.
    

Overall, the time complexity is dominated by the sorting step, so the total time complexity is: `O(nlog⁡n)`

### Space Complexity:

* The input array itself uses `O(n)` space.
    
* The `pow` array used to store precomputed powers of 2 uses `O(n)` space.
    

No additional significant space is used apart from these, so the total space complexity is: `O(n)`