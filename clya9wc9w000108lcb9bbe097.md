---
title: "Leetcode 2239 - Find Closest Number to Zero"
datePublished: Sat Jul 06 2024 15:22:12 GMT+0000 (Coordinated Universal Time)
cuid: clya9wc9w000108lcb9bbe097
slug: leetcode-2239
tags: python, python3, leetcode, codenewbies

---

Given an integer array `nums` of size `n`, return *the number with the value* ***closest*** *to* `0` *in* `nums`. If there are multiple answers, return *the number with the* ***largest*** *value*.

```python
Input: nums = [-4,-2,1,4,8]
Output: 1

Input: nums = [2,-1,1]
Output: 1
```

```python
from typing import List

class Solution:
    def findClosestNumber(self, nums: List[int]) -> int:
        closest = nums[0]
        for num in nums:
            if abs(num) < abs(closest):
                closest = num
        if closest < 0 and abs(closest) in nums:
            return abs(closest)
        else:
            return closest


solution = Solution()
ans = solution.findClosestNumber([1, -2, 3, -4, 5])
print(ans)
```

Time complexity: `O(n)`

```python
for num in nums: # n
abs(closest) in nums # n

# -> n + n -> 2n -> O(n)
```

Space complexity: `O(1)`