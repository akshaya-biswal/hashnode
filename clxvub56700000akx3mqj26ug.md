---
title: "Stacks"
datePublished: Wed Jun 26 2024 12:57:02 GMT+0000 (Coordinated Universal Time)
cuid: clxvub56700000akx3mqj26ug
slug: stack
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720292474853/718c4293-3a2d-46c8-a39e-6118954f90f4.jpeg
tags: python, data-structures, stack, dsa

---

A stack is a linear data structure that follows the principle of **Last In First Out (LIFO)**. This means the last element inserted inside the stack is removed first.

Think of a stack like a pile of pancakes.

### Operations

* **Push**: Add an element to the top.
    
* **Pop**: Remove the element from the top.
    
* **Peek/Top**: Get the value of the top element without removing it.
    
* **isEmpty**: Check if the stack is empty.
    
* **Size:** Finds the number of elements
    

### Code : Using Array

```python
class Stack:
    def __init__(self):
        self.stack = []

    def push(self, item):
        self.stack.append(item)

    def pop(self):
        if not self.is_empty():
            return self.stack.pop()
        else:
            raise IndexError("pop from empty stack")

    def peek(self):
        if not self.is_empty():
            return self.stack[-1]
        else:
            raise IndexError("peek from empty stack")

    def is_empty(self):
        return len(self.stack) == 0

    def size(self):
        return len(self.stack)

    def __str__(self):
        return str(self.stack)


# Example usage
s = Stack()
s.push(1)
s.push(2)
s.push(3)
print(s)  # Output: [1, 2, 3]
print(s.pop())  # Output: 3
print(s.peek())  # Output: 2
print(s.is_empty())  # Output: False
print(s.size())  # Output: 2
```