---
title: "Queues"
datePublished: Thu Jun 27 2024 01:57:49 GMT+0000 (Coordinated Universal Time)
cuid: clxwm77zf00030al3fasx2l3z
slug: queues
tags: 2articles1week

---

Queue follows the **First In First Out (FIFO)** rule - the item that goes in first is the item that comes out first.

Think of a queue as people standing in line in a supermarket.

### Operations

* **Enqueue:** Adds a new element
    
* **Dequeue:** Removes and returns the first (front) element
    
* **Peek:** Returns the first element
    
* **isEmpty:** Checks if it is empty
    
* **Size:** Finds the number of elements
    

### Code : Using Array

```python
class Queue:
    def __init__(self):
        self.queue = []

    def enqueue(self, element):
        self.queue.append(element)

    def dequeue(self):
        if self.isEmpty():
            return "Queue is empty"
        return self.queue.pop(0)

    def peek(self):
        if self.isEmpty():
            return "Queue is empty"
        return self.queue[0]

    def isEmpty(self):
        return len(self.queue) == 0

    def size(self):
        return len(self.queue)


# Create a queue
movie_line = Queue()

# Add
movie_line.enqueue("A")
movie_line.enqueue("B")
movie_line.enqueue("C")
print("Queue: ", movie_line.queue)

# Remove
print("Dequeue: ", movie_line.dequeue())

# Peek the left most item
print("Peek: ", movie_line.peek())

# Check isEmpty
print("isEmpty: ", movie_line.isEmpty())

# Size
print("Size: ", movie_line.size())
```