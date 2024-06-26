---
title: "Stack Data Structure"
datePublished: Wed Jun 26 2024 12:57:02 GMT+0000 (Coordinated Universal Time)
cuid: clxvub56700000akx3mqj26ug
slug: stack
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719404988071/a46b021c-7058-4665-b207-634e3ca8dead.jpeg
tags: python, data-structures, stack, dsa

---

A stack is a linear data structure that follows the principle of **Last In First Out (LIFO)**. This means the last element inserted inside the stack is removed first.

Think of a stack like a pile of pancakes.

### Operations

* **Push:** Adds a new element
    
* **Pop:** Removes and returns the top element
    
* **Peek:** Returns the top element
    
* **isEmpty:** Checks if it is empty
    
* **Size:** Finds the number of elements
    

### Code : Using Array

```python
class Stack:
    def __init__(self):
        self.stack = []

    def push(self, element):
        self.stack.append(element)

    def pop(self):
        if self.isEmpty():
            return "Stack is empty"
        return self.stack.pop()

    def peek(self):
        if self.isEmpty():
            return "Stack is empty"
        return self.stack[-1]

    def isEmpty(self):
        return len(self.stack) == 0

    def size(self):
        return len(self.stack)


# Create a stack
pancake = Stack()

# Add
pancake.push("A")
pancake.push("B")
pancake.push("C")
print("Stack: ", pancake.stack)

# Remove
print("Pop: ", pancake.pop())

# Peek the top item
print("Peek: ", pancake.peek())

# Is Empty
print("isEmpty: ", pancake.isEmpty())

# Size
print("Size: ", pancake.size())
```