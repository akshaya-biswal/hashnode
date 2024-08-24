---
title: "Cartesian product of two sets"
datePublished: Sat Aug 24 2024 19:37:11 GMT+0000 (Coordinated Universal Time)
cuid: cm08jkzgx00000ajwf1b88fst
slug: cartesian-product-of-two-sets
tags: algorithms, array, dsa

---

It involves creating **all possible pairs** of elements where the first element comes from the first set and the second element comes from the second set.

```javascript
const cartesianProduct = (arr1, arr2) => {
  const result = [];
  for (let i = 0; i < arr1.length; i++) {
    for (let j = 0; j < arr2.length; j++) {
      result.push([arr1[i], arr2[j]]);
    }
  }
  return result;
};

const array1 = [1, 2];
const array2 = ["a", "b", "c"];

console.log(cartesianProduct(array1, array2));

// Output: [[1, 'a'], [1, 'b'], [1, 'c'], [2, 'a'], [2, 'b'], [2, 'c']]
```

### Cartesian Product of Multiple Arrays

```javascript
const cartesianProduct = (...arrays) => {
  return arrays.reduce(
    (acc, currArray) => {
      const temp = [];

      acc.forEach((accItem) => {
        currArray.forEach((currItem) => {
          temp.push([...accItem, currItem]);
        });
      });

      return temp;
    },
    [[]]
  );
};

const arrays = [
  [1, 2],
  ["a", "b"],
  [true, false],
];
console.log(cartesianProduct(...arrays));

// [
//   [1, 'a', true], [1, 'a', false],
//   [1, 'b', true], [1, 'b', false],
//   [2, 'a', true], [2, 'a', false],
//   [2, 'b', true], [2, 'b', false]
// ]
```