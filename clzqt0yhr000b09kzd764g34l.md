---
title: "Singly Linked List"
datePublished: Mon Aug 12 2024 09:41:41 GMT+0000 (Coordinated Universal Time)
cuid: clzqt0yhr000b09kzd764g34l
slug: singly-linked-list
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1723455614766/173ad87c-099f-46ba-a75d-18cac97bdca8.webp
tags: algorithms, javascript, data-structures, dsa, linkedlists

---

### Introduction

* A **Linked List** is a linear data structure
    

* Each node contains data and a reference to the next node.
    
* It allows traversal in one direction, from the head (first node) to the tail (last node)
    

### Code

```javascript
class Node {
  constructor(data) {
    this.data = data;
    this.next = null;
  }
}
```

```javascript
class LinkedList {
  constructor() {
    this.head = null;
  }

  // Helper: Traverse to the node at a specific index
  _getNodeAtIndex(index) {
    let current = this.head;
    let i = 0;

    while (current && i < index) {
      current = current.next;
      i++;
    }

    return current;
  }

  // Helper: Check if the list is empty
  _isEmpty() {
    return this.head === null;
  }

  // Helper: Add node at the beginning
  _addToStart(newNode) {
    newNode.next = this.head;
    this.head = newNode;
  }

  // Add a node to the end of the list
  append(data) {
    const newNode = new Node(data);
    if (this._isEmpty()) {
      this._addToStart(newNode);
      return;
    }
    let current = this._getNodeAtIndex(this.length() - 1);
    current.next = newNode;
  }

  // Add a node to the beginning of the list
  prepend(data) {
    const newNode = new Node(data);
    this._addToStart(newNode);
  }

  // Add a node at a specific index
  addAtIndex(data, index) {
    if (index === 0) {
      this.prepend(data);
      return;
    }

    const previous = this._getNodeAtIndex(index - 1);

    if (!previous) {
      console.log("Index out of bounds");
      return;
    }

    const newNode = new Node(data);
    newNode.next = previous.next;
    previous.next = newNode;
  }

  // Remove a node at a specific index
  removeAtIndex(index) {
    if (this._isEmpty()) {
      return;
    }

    if (index === 0) {
      this.head = this.head.next;
      return;
    }

    const previous = this._getNodeAtIndex(index - 1);

    if (!previous || !previous.next) {
      console.log("Index out of bounds");
      return;
    }

    previous.next = previous.next.next;
  }

  // Remove the first node
  removeFromStart() {
    if (this._isEmpty()) {
      return;
    }
    this.head = this.head.next;
  }

  // Remove the last node
  removeFromEnd() {
    if (this._isEmpty()) {
      return;
    }

    if (!this.head.next) {
      this.head = null;
      return;
    }

    const previous = this._getNodeAtIndex(this.length() - 2);
    previous.next = null;
  }

  // Search for a node with specific data
  search(data) {
    let current = this.head;
    while (current) {
      if (current.data === data) {
        return current;
      }
      current = current.next;
    }
    return null; // If not found
  }

  display() {
    let current = this.head;
    const elements = [];
    while (current) {
      elements.push(current.data);
      current = current.next;
    }
    console.log(elements.join(" -> "));
  }

  length() {
    let count = 0;
    let current = this.head;
    while (current) {
      count++;
      current = current.next;
    }
    return count;
  }
}
```

```javascript
const list = new LinkedList();
list.append(10);
list.append(20);
list.display(); // 10 -> 20

list.prepend(5);
list.display(); // 5 -> 10 -> 20

list.addAtIndex(15, 2);
list.display(); // 5 -> 10 -> 15 -> 20

list.removeAtIndex(1);
list.display(); // 5 -> 15 -> 20

list.removeFromStart();
list.display(); // 15 -> 20

list.removeFromEnd();
list.display(); // 15
```

### Real-time Use

Linked lists are used in various real-time applications, including:

* Implementing stacks and queues
    
* Managing memory allocation in dynamic environments
    
* Managing music playlists in media players
    

### Complexity Analysis

* Insertion/Deletion at the Beginning: O(1)
    
* Insertion/Deletion at the End: O(n) — Due to traversal to the end
    
* Searching/Accessing an Element: O(n)