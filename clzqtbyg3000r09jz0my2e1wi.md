---
title: "Doubly Linked List"
datePublished: Mon Aug 12 2024 09:50:15 GMT+0000 (Coordinated Universal Time)
cuid: clzqtbyg3000r09jz0my2e1wi
slug: doubly-linked-list
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1723458682788/91707d46-7ecb-49f4-9c08-eaee7b069aad.png
tags: algorithms, javascript, dsa, linkedlists

---

### Introduction

* A **Linked List** is a linear data structure
    
* Each node has two references: one to the next node and one to the previous node.
    
* This allows traversal in both forward and backward directions.
    

### Code

```javascript
class Node {
  constructor(data) {
    this.data = data;
    this.next = null;
    this.prev = null;
  }
}
```

```javascript
class DoublyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
  }

  // Helper: Check if the list is empty
  _isEmpty() {
    return this.head === null;
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

  // Helper: Insert a new node between two nodes
  _insertBetween(newNode, previous, next) {
    newNode.prev = previous;
    newNode.next = next;

    if (previous) {
      previous.next = newNode;
    }

    if (next) {
      next.prev = newNode;
    }
  }

  // Helper: Remove a node
  _removeNode(node) {
    if (node.prev) {
      node.prev.next = node.next;
    } else {
      this.head = node.next;
    }

    if (node.next) {
      node.next.prev = node.prev;
    } else {
      this.tail = node.prev;
    }
  }

  // Add a node to the end of the list
  append(data) {
    const newNode = new Node(data);
    if (this._isEmpty()) {
      this.head = this.tail = newNode;
      return;
    }
    this._insertBetween(newNode, this.tail, null);
    this.tail = newNode;
  }

  // Add a node to the beginning of the list
  prepend(data) {
    const newNode = new Node(data);
    if (this._isEmpty()) {
      this.head = this.tail = newNode;
      return;
    }
    this._insertBetween(newNode, null, this.head);
    this.head = newNode;
  }

  // Add a node at a specific index
  addAtIndex(data, index) {
    if (index === 0) {
      this.prepend(data);
      return;
    }

    const current = this._getNodeAtIndex(index);
    if (!current) {
      this.append(data);
      return;
    }

    const newNode = new Node(data);
    this._insertBetween(newNode, current.prev, current);
  }

  // Remove a node at a specific index
  removeAtIndex(index) {
    if (this._isEmpty()) {
      return;
    }

    const current = this._getNodeAtIndex(index);
    if (!current) {
      console.log("Index out of bounds");
      return;
    }

    this._removeNode(current);
  }

  // Remove the first node
  removeFromStart() {
    if (this._isEmpty()) {
      return;
    }

    this._removeNode(this.head);
  }

  // Remove the last node
  removeFromEnd() {
    if (this._isEmpty()) {
      return;
    }

    this._removeNode(this.tail);
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

  // Display the list
  display() {
    let current = this.head;
    const elements = [];
    while (current) {
      elements.push(current.data);
      current = current.next;
    }
    console.log(elements.join(" <-> "));
  }

  // Display the list in reverse order
  displayReverse() {
    if (this._isEmpty()) {
      console.log("List is empty");
      return;
    }
    let current = this.tail;
    while (current) {
      console.log(current.data);
      current = current.prev;
    }
  }
}
```

```javascript
const list = new DoublyLinkedList();
list.append(10);
list.append(20);
list.prepend(5);
list.addAtIndex(15, 2);

list.display(); // 5 <-> 10 <-> 15 <-> 20

list.removeAtIndex(1);
list.display(); // 5 <-> 15 <-> 20

list.removeFromStart();
list.display(); // 15 <-> 20

list.removeFromEnd();
list.display(); // 15

list.displayReverse(); // 15
```