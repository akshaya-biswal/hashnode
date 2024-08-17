---
title: "Heap DS"
datePublished: Sat Aug 17 2024 06:56:46 GMT+0000 (Coordinated Universal Time)
cuid: clzxsc4tp000309l1bq6bd27t
slug: heap-ds
tags: algorithms, javascript, dsa, heap, max-heap, min-heap

---

A heap is a specialized binary tree-based data structure that satisfies the heap property.

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
    

### Code

```javascript
class MinHeap {
  constructor() {
    this.heap = [];
  }

  getParentIndex(index) {
    return Math.floor((index - 1) / 2);
  }

  getLeftChildIndex(index) {
    return 2 * index + 1;
  }

  getRightChildIndex(index) {
    return 2 * index + 2;
  }

  swap(index1, index2) {
    [this.heap[index1], this.heap[index2]] = [
      this.heap[index2],
      this.heap[index1],
    ];
  }

  insert(value) {
    this.heap.push(value);
    this.heapifyUp();
  }

  heapifyUp() {
    let index = this.heap.length - 1;
    while (
      this.getParentIndex(index) >= 0 &&
      this.heap[this.getParentIndex(index)] > this.heap[index]
    ) {
      this.swap(this.getParentIndex(index), index);
      index = this.getParentIndex(index);
    }
  }

  extractMin() {
    if (this.heap.length === 0) return null;
    if (this.heap.length === 1) return this.heap.pop();

    const root = this.heap[0];
    this.heap[0] = this.heap.pop();
    this.heapifyDown();
    return root;
  }

  heapifyDown() {
    let index = 0;
    while (this.getLeftChildIndex(index) < this.heap.length) {
      let smallerChildIndex = this.getLeftChildIndex(index);
      if (
        this.getRightChildIndex(index) < this.heap.length &&
        this.heap[this.getRightChildIndex(index)] < this.heap[smallerChildIndex]
      ) {
        smallerChildIndex = this.getRightChildIndex(index);
      }

      if (this.heap[index] < this.heap[smallerChildIndex]) {
        break;
      }

      this.swap(index, smallerChildIndex);
      index = smallerChildIndex;
    }
  }

  peek() {
    return this.heap[0];
  }
}
```

```javascript
const minHeap = new MinHeap();

minHeap.insert(10);
minHeap.insert(20);
minHeap.insert(5);
minHeap.insert(7);

console.log(minHeap.peek());
console.log(minHeap.extractMin());
console.log(minHeap.extractMin());
```

### Explanation

`heapifyUp()`

* **Start at the Last Element**: The process begins at the last index of the heap array, where the new element was inserted.
    
* **Compare with Parent**: The function compares the newly added element with its parent. In a min-heap, if the newly added element is smaller than its parent, it violates the heap property (since the parent should be smaller).
    
* **Swap if Necessary**: If the new element is smaller than its parent, it swaps places with the parent to maintain the heap property.
    
* **Move Up the Tree**: After the swap, the process moves up to the parent's position (now occupied by the new element) and repeats the comparison with the next parent.
    
* **Stop Condition**: The loop continues until:
    
    * The element reaches the root (where it has no parent).
        
    * The element is no longer smaller than its parent, meaning the heap property is restored.
        

`heapifyDown()`

* **Start at the Root**: The process begins at the root of the heap (index `0`), which is now occupied by the last element in the heap after removing the root.
    
* **Find the Smaller Child**: For the current node, the function checks its children. It finds the index of the smaller child (in a min-heap) since this is the one that might need to be swapped with the current node.
    
* **Compare and Swap**: If the current node is greater than the smaller child, a swap occurs to maintain the heap property. This ensures that the smallest value remains closer to the root.
    
* **Move Down**: After the swap, the process moves down to the child's position (now the position of the element that was swapped) and repeats the comparison with its new children.
    
* **Stop Condition**: The loop continues until:
    
    * The node has no children (i.e., it's a leaf node).
        
    * The node is smaller than its children (in a min-heap), meaning the heap property is restored.
        

### Time and Space Complexity

**Time Complexity**

* **Insertion** `O(log⁡n)` : When a new element is added to the heap, it may need to be moved up the tree to restore the heap property.
    

* **Deletion** `O(log⁡n)` : Removing the root element involves replacing it with the last element and then moving this element down the tree to restore the heap property.
    
* **Peek** `O(1)` : The root is always the first element of the array
    

**Space Complexity**

* `O(n)` : A heap is usually implemented using an array, and the space required is proportional to the number of elements in the heap. Therefore, if there are `n` elements in the heap, the space complexity is `O(n)`.