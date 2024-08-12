---
title: "Queue in JS"
datePublished: Mon Aug 12 2024 10:34:51 GMT+0000 (Coordinated Universal Time)
cuid: clzquxbdm000609l9b9ribnif
slug: queue-in-js
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1723458847016/c170e096-44e7-491c-8c00-cc1474dd0b79.png
tags: algorithms, javascript, data-structures, queue, dsa

---

# Introduction

* The queue data structure is a sequential collection of elements that follows the principle of First In First Out (FIFO).
    
* The first element inserted into the queue is first element to be removed.
    
* A queue of people. People enter the queue at one end and leave the queue from the other end.
    

### **Operations**

* `enqueue(element)` : add an element at the end
    
* `dequeue()` : remove an element from the front
    
* `peek()` : get the value of the element at the front of the queue without removing it
    
* `isEmpty()` : check if is empty
    
* `size()` : get the number of elements
    
* `print()` : visualise the elements
    

### Code

```javascript
class Queue {
  constructor() {
    this.items = {};
    this.rear = 0;
    this.front = 0;
  }

  enqueue(item) {
    this.items[this.rear] = item;
    this.rear++;
  }

  dequeue() {
    const item = this.items[this.front];
    delete this.items[this.front];
    this.front++;
    return item;
  }

  peek() {
    if (!this.isEmpty()) {
      return this.items[this.front];
    }
    return null;
  }

  isEmpty() {
    return this.rear - this.front === 0;
  }

  size() {
    return this.rear - this.front;
  }

  print() {
    console.log(this.items);
  }
}
```

```javascript
const queue = new Queue();
console.log(queue.isEmpty()); // true

queue.enqueue(10);
queue.enqueue(20);
queue.enqueue(30);
queue.enqueue(40);
queue.print(); // { '0': 10, '1': 20, '2': 30, '3': 40 }

queue.dequeue();
queue.print(); // { '1': 20, '2': 30, '3': 40 }

console.log(queue.size()); // 3
console.log(queue.peek()); // 20
```

### Usage

* Printers
    
* CPU task scheduling
    
* Callback queue in JavaScript runtime