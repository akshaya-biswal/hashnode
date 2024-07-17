---
title: "Leetcode 1750: Minimum Length of String After Deleting Similar Ends"
datePublished: Wed Jul 17 2024 06:18:53 GMT+0000 (Coordinated Universal Time)
cuid: clypgbzqo001209l0dqew2d0h
slug: leetcode-1750-minimum-length-of-string-after-deleting-similar-ends
tags: 2articles1week

---

To find the minimum length of a string after deleting similar characters from both ends using a simple two-pointers approach in JavaScript

### Explanation

* Initialize two pointers, `left` starting from the beginning of the string and `right` starting from the end of the string.
    
* Move the `left` pointer to the right as long as the characters at the `left` and `right` pointers are the same.
    
* Move the `right` pointer to the left as long as the characters at the `left` and `right` pointers are the same.
    
* When the pointers meet or cross, stop the process.
    
* The remaining length of the string will be `right - left + 1`.
    

### Code

```javascript
const minimum_length = (str) => {
  let left = 0;
  let right = str.length - 1;

  while (left < right && str[left] === str[right]) {
    const char = str[left];

    while (left <= right && str[left] === char) {
      left++;
    }

    while (left <= right && str[right] === char) {
      right--;
    }
  }

  return right - left + 1;
};

console.log(minimum_length("abcaacba"));
```

### Time Complexity:

The time complexity of the function is **O(n)**, where **n** is the length of the string. This is because each character in the string is checked at most once by either the `left` or `right` pointer as they move towards the center of the string.

### Space Complexity:

The space complexity of the function is **O(1)**. This is because the function uses only a fixed amount of extra space (for the `left` and `right` pointers and a few variables) regardless of the input size.