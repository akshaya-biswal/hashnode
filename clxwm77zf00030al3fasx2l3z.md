---
title: "Queues"
datePublished: Thu Jun 27 2024 01:57:49 GMT+0000 (Coordinated Universal Time)
cuid: clxwm77zf00030al3fasx2l3z
slug: queue
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720292938150/7081fda1-3ca5-476a-947b-58fe2e31d042.jpeg
tags: 2articles1week

---

A **queue** is a data structure that follows the First In, First Out (FIFO) principle. The first element added is the first one to be removed.

Think of a queue as people standing in line in a supermarket.

### Operations

* **Enqueue**: Add an element to the end of the queue.
    
* **Dequeue**: Remove the element from the front of the queue.
    
* **Front**: Get the value of the front element without removing it.
    
* **isEmpty**: Check if the queue is empty.
    
* **Size:** Finds the number of elements
    

### Code : Using Array

```python
class Queue:
    def __init__(self):
        self.queue = []

    def enqueue(self, item):
        self.queue.append(item)

    def dequeue(self):
        if not self.is_empty():
            return self.queue.pop(0)
        else:
            raise IndexError("dequeue from empty queue")

    def front(self):
        if not self.is_empty():
            return self.queue[0]
        else:
            raise IndexError("front from empty queue")

    def is_empty(self):
        return len(self.queue) == 0

    def size(self):
        return len(self.queue)

    def __str__(self):
        return str(self.queue)


# Example usage
q = Queue()
q.enqueue(1)
q.enqueue(2)
q.enqueue(3)
print(q)  # Output: [1, 2, 3]
print(q.dequeue())  # Output: 1
print(q.front())  # Output: 2
print(q.is_empty())  # Output: False
print(q.size())  # Output: 2
```