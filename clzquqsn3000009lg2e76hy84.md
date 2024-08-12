---
title: "Stack in JS"
datePublished: Mon Aug 12 2024 10:29:47 GMT+0000 (Coordinated Universal Time)
cuid: clzquqsn3000009lg2e76hy84
slug: stack-in-js
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/1_Aojfv58_s/upload/d006feb4296e83513ac90903d72a6ed6.jpeg
tags: algorithms, data-structures, stack, dsa

---

### Introduction

* The stack data structure is a sequential collection of elements that follows the principle of Last In First Out (LIFO).
    
* The last element inserted into the stack is first element to be removed.
    
* A stack of plates. The last plate placed on top of the stack is also the first plate removed from the stack.
    

### O**perations**

* `push(element)` : add an element to the top
    
* `pop()` : remove the top most element
    
* `peek()` : get the value of the top element without removing it
    
* `isEmpty()` : check if is empty
    
* `size()` : get the number of elements
    
* `print()` : visualise the elements
    

### Code

```javascript
class Stack {
  constructor() {
    this.items = [];
  }

  push(item) {
    this.items.push(item);
  }

  pop() {
    return this.items.pop();
  }

  peek() {
    return this.items[this.items.length - 1];
  }

  isEmpty() {
    return this.items.length === 0;
  }

  size() {
    return this.items.length;
  }

  print() {
    console.log(this.items.toString());
  }
}
```

```javascript
const stack = new Stack();

console.log(stack.isEmpty()); // true

stack.push(10);
stack.push(20);
stack.push(30);
stack.push(40);
console.log(stack); // { items: [ 10, 20, 30, 40 ] }

console.log(stack.isEmpty()); // false

stack.pop();
console.log(stack); // { items: [ 10, 20, 30 ] }

console.log(stack.peek()); // 30
```

### Usage

* Browser history tracking
    
* Undo operation when typing
    
* Expression conversions
    
* Call stack in JavaScript runtime