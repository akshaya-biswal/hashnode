---
title: "Linear Search"
datePublished: Tue Aug 13 2024 18:20:30 GMT+0000 (Coordinated Universal Time)
cuid: clzsr00ie00010al6hdy0d02x
slug: linear-search
tags: search, algorithms, javascript, dsa, datastructure

---

Linear search is a simple searching algorithm used to find an element in a list or an array. It works by sequentially checking each element of the list until it finds the target element or reaches the end of the list.

### Code

```javascript
function linearSearch(arr, target) {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === target) {
      return i;
    }
  }
  return -1;
}

console.log(linearSearch([10, 20, 30, 40, 50], 40));
```