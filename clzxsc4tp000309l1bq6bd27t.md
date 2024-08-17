---
title: "Heap DS"
datePublished: Sat Aug 17 2024 06:56:46 GMT+0000 (Coordinated Universal Time)
cuid: clzxsc4tp000309l1bq6bd27t
slug: heap-ds
tags: algorithms, javascript, dsa, heap, max-heap, min-heap

---

* **Max-Heap**: In a max-heap, for any given node `I`, the value of `I` is greater than or equal to the values of its children. The largest value is at the root.
    

* **Min-Heap**: In a min-heap, for any given node `I`, the value of `I` is less than or equal to the values of its children. The smallest value is at the root.
    

Heaps are commonly implemented using arrays, where:

* The root element is at index `0`.
    
* For any element at index `i`:
    
    * Its left child is at index `2 * i + 1`.
        
    * Its right child is at index `2 * i + 2`.
        
    * Its parent is at index `(i - 1) / 2`.
        

### Basic Operations of a Heap

1. **Insert**: Adding an element to the heap while maintaining the heap property.
    
2. **Extract**: Removing the root element and maintaining the heap property.