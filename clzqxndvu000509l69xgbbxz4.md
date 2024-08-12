---
title: "Merge Sort"
datePublished: Mon Aug 12 2024 11:51:06 GMT+0000 (Coordinated Universal Time)
cuid: clzqxndvu000509l69xgbbxz4
slug: merge-sort
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/IhTPaCjsfR8/upload/af100bd79d3e4a88e7bb21db6ab75aaf.jpeg
tags: algorithms, javascript, sorting, dsa, merge-sort, datastructure

---

* Merge sort divides the array into two halves, recursively sorts each half, and then merges them back together in sorted order.
    
* It follows the divide-and-conquer approach, achieving a time complexity of `O(nlogn)`.
    

### Code

```javascript
function mergeSort(arr) {
  const length = arr.length;

  if (length <= 1) {
    return arr;
  }

  const mid = Math.floor(length / 2);
  const leftArr = arr.slice(0, mid);
  const rightArr = arr.slice(mid);

  return merge(mergeSort(leftArr), mergeSort(rightArr));
}

function merge(leftArr, rightArr) {
  const sortedArr = [];

  while (leftArr.length && rightArr.length) {
    if (leftArr[0] <= rightArr[0]) {
      sortedArr.push(leftArr.shift());
    } else {
      sortedArr.push(rightArr.shift());
    }
  }

  return [...sortedArr, ...leftArr, ...rightArr];
}

console.log(mergeSort([6, 5, 12, 10, 9, 1]));
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1723463419047/acf60a91-4190-4c1f-91ee-88ce878d0bfe.png align="center")