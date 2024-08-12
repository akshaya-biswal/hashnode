---
title: "Bubble Sort"
datePublished: Mon Aug 12 2024 10:48:54 GMT+0000 (Coordinated Universal Time)
cuid: clzqvfea4000n08la9ksobwrg
slug: bubble-sort
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1723459672160/5f2bf619-e66b-4305-91c1-407f85d4ef0f.png
tags: algorithms, javascript, data-structures, sorting, dsa, bubble-sort

---

### Explanation

1. **Outer Loop (**`for` loop):
    
    * This loop runs from the beginning of the array to the end.
        
    * The variable `start` represents the current pass through the array.
        
    * At the beginning of each pass, `swapped` is set to `false`.
        
2. **Inner Loop (**`for` loop):
    
    * This loop iterates over the array elements from the beginning to the last unsorted element.
        
    * `curr` represents the current element being compared.
        
    * The condition `curr < end - start - 1` ensures that the loop only goes up to the last unsorted element, reducing the number of comparisons needed in each pass.
        
3. **Comparison and Swapping**:
    
    * `if (arr[curr] > arr[curr + 1])` checks if the current element is greater than the next element.
        
    * If true, the elements are swapped using array destructuring: `[arr[curr], arr[curr + 1]] = [arr[curr + 1], arr[curr]]`.
        
    * After a swap, `swapped` is set to `true` indicating that a swap has occurred during this pass.
        
4. **Early Exit Optimization**:
    
    * `if (!swapped) break;` checks if no elements were swapped during the current pass.
        
    * If `swapped` is still `false`, the array is already sorted, and the loop breaks early, improving efficiency by avoiding unnecessary passes.
        
5. **Return Sorted Array**:
    
    * After the sorting is complete, the function returns the sorted array.
        

### Code

```javascript
function bubbleSort(arr) {
  const end = arr.length;
  let swapped;

  for (let start = 0; start < end; start++) {
    swapped = false;

    for (let curr = 0; curr < end - start - 1; curr++) {
      if (arr[curr] > arr[curr + 1]) {
        [arr[curr], arr[curr + 1]] = [arr[curr + 1], arr[curr]];
        swapped = true;
      }
    }

    if (!swapped) break;
  }

  return arr;
}

console.log(bubbleSort([-2, 45, 0, 11, -9])); // [ -9, -2, 0, 11, 45 ]
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723459556860/deaa1873-bb17-4445-80ba-6c61351b40b5.png align="center")