---
title: "Priority Queue"
datePublished: Sat Aug 17 2024 18:14:34 GMT+0000 (Coordinated Universal Time)
cuid: clzygjsha000d09mn2xsqg3vo
slug: priority-queue
tags: algorithms, javascript, data-structures, dsa, priority-queue

---

A **Priority Queue** is a type of data structure where each element is associated with a priority, and elements are served based on their priority rather than just their position in the queue. Higher priority elements are dequeued before lower priority elements.

### Explanation

* **enqueue(element)**: Adds an element to the queue. The `element` is an array where the first item is the task, and the second item is the priority. The queue is sorted based on the priority.
    
* **dequeue()**: Removes the element with the highest priority (i.e., the one at the front of the queue).
    
* **front()**: Returns the element at the front of the queue without removing it.
    
* **size()**: Returns the number of elements in the queue.
    
* **isEmpty()**: Checks if the queue is empty.
    

```javascript
class PriorityQueue {
  constructor() {
    this.collection = [];
  }

  // Helper function to find the correct insertion index using binary search
  _binarySearchInsertIndex(element) {
    let left = 0;
    let right = this.collection.length - 1;

    while (left <= right) {
      const mid = Math.floor((left + right) / 2);
      if (element[1] === this.collection[mid][1]) {
        return mid;
      } else if (element[1] < this.collection[mid][1]) {
        right = mid - 1;
      } else {
        left = mid + 1;
      }
    }

    return left;
  }

  front() {
    return this.collection[0];
  }

  size() {
    return this.collection.length;
  }

  isEmpty() {
    return this.collection.length === 0;
  }

  dequeue() {
    return this.collection.shift();
  }

  enqueue(element) {
    if (this.isEmpty()) {
      this.collection.push(element);
      return;
    }

    const index = this._binarySearchInsertIndex(element);
    this.collection.splice(index, 0, element); // Insert the element at the correct position
  }
}
```

```javascript
const pq = new PriorityQueue();
pq.enqueue(["Task A", 2]);
pq.enqueue(["Task B", 1]);
pq.enqueue(["Task C", 3]);
console.log(pq.collection); // [['Task B', 1], ['Task A', 2], ['Task C', 3]]

console.log(pq.dequeue()); // ['Task B', 1]
console.log(pq.collection); // ['Task A', 2], ['Task C', 3]]

console.log(pq.front()); // ['Task A', 2]
console.log(pq.size()); // 2
console.log(pq.isEmpty()); // false
```

### Time Complexity

**enqueue()**:

* **Binary Search (\_binarySearchInsertIndex)**: The binary search operation has a time complexity of `O(log⁡n)`, where `n` is the number of elements in the collection.
    
* **Insertion (splice)**: In the worst case, inserting an element in an array (using `splice`) has a time complexity of `O(n)` because it may require shifting other elements.
    
    **Overall Time Complexity**: `O(n)`, dominated by the insertion operation.
    

**dequeue()**:

* **Shift Operation**: The `shift()` method removes the first element of an array, which has a time complexity of `O(n)` because all other elements need to be shifted.
    
* Time Complexity: `O(n)`.
    

### Space Complexity

The space complexity for all operations is O(n)O(n)O(n), where nnn is the number of elements in the priority queue. This is because all elements are stored in the array.