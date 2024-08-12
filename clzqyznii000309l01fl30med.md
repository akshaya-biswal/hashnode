---
title: "Quick Sort"
datePublished: Mon Aug 12 2024 12:28:38 GMT+0000 (Coordinated Universal Time)
cuid: clzqyznii000309l01fl30med
slug: quick-sort
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/BwXsi8tcXlk/upload/7748d9744c6f426ce070119cb190ef1e.jpeg
tags: algorithms, javascript, sorting, quick-sort, dsa, datastructure

---

### Introduction

* Quick sort follows the divide-and-conquer approach, selecting a pivot element and partitioning the array into two subarrays: elements less than the pivot and elements greater than the pivot.
    
* It recursively sorts the subarrays and combines them to produce the sorted array.
    

### Code - Using ES6

```javascript
function quickSort(arr) {
  if (arr.length <= 1) return arr;
  
  // We choose the last element as the pivot.
  const pivot = arr.pop();
  
  // We use the filter to separate the elements less than and greater than or equal to the pivot.
  return [
    ...quickSort(arr.filter(num => num < pivot)),
    pivot,
    ...quickSort(arr.filter(num => num >= pivot))
  ];
}

console.log(quickSort([8, 7, 2, 1, 0, 9, 6]));
```

### Code - Without using ES6

```javascript
function quickSort(arr) {
  const length = arr.length;

  if (length <= 1) {
    return arr;
  }

  // we have already taken last index as pivot
  const pivot = arr[length - 1];
  const left = [];
  const right = [];

  // Last index is already sorted, because we have taken as pivot
  for (let i = 0; i <= length - 2; i++) {
    if (arr[i] < pivot) {
      left.push(arr[i]);
    } else {
      right.push(arr[i]);
    }
  }

  return [...quickSort(left), pivot, ...quickSort(right)];
}

console.log(quickSort([8, 7, 2, 1, 0, 9, 6]));
```

### Code - In Place Quick Sort Implementation

```javascript
function quickSort(arr, left = 0, right = arr.length - 1) {
  if (left < right) {
    const pivotIndex = partition(arr, left, right);
    quickSort(arr, left, pivotIndex - 1);
    quickSort(arr, pivotIndex + 1, right);
  }
  return arr;
}

function partition(arr, left, right) {
  const pivot = arr[right]; // Use the rightmost element as the pivot
  let i = left - 1; // Place for swapping

  for (let j = left; j < right; j++) {
    if (arr[j] < pivot) {
      i++;
      [arr[i], arr[j]] = [arr[j], arr[i]]; // Swap elements
    }
  }
  [arr[i + 1], arr[right]] = [arr[right], arr[i + 1]]; // Swap the pivot element
  return i + 1; // Return the pivot index
}

console.log(quickSort([38, 27, 43, 3, 9, 82, 10])); // [3, 9, 10, 27, 38, 43, 82]
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723465678774/08cb9011-0ebb-4bcf-9bc2-fc57491da371.png align="center")