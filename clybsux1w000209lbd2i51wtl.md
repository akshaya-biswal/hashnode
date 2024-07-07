---
title: "Doubly Linked List"
datePublished: Sun Jul 07 2024 17:00:45 GMT+0000 (Coordinated Universal Time)
cuid: clybsux1w000209lbd2i51wtl
slug: dll
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720371568366/3c80a9c0-7737-44cd-8da9-44c9a399dbde.jpeg
tags: python, data-structures, python3, coding, codenewbies, data-structure-and-algorithms, doublylinkedlist

---

* A **doubly linked list** is a linear data structure where each node contains three parts: data, a pointer to the next node, and a pointer to the previous node.
    
* This allows traversal in both directions (forward and backward).
    

### Operations

| Operation | Description | Time Complexity | Space Complexity |
| --- | --- | --- | --- |
| **Insertion** |  |  |  |
| At the beginning | Insert a node at the start | `O(1)` | `O(1)` |
| At the end | Insert a node at the end | `O(1)` | `O(1)` |
| At a specific position | Insert a node at a given position | `O(n)` | `O(1)` |
| **Deletion** |  |  |  |
| From the beginning | Remove a node from the start | `O(1)` | `O(1)` |
| From the end | Remove a node from the end | `O(1)` | `O(1)` |
| From a specific position | Remove a node at a given position | `O(n)` | `O(1)` |
| **Traversal** |  |  |  |
| Forward | Visit all nodes from head to tail | `O(n)` | `O(1)` |
| Backward | Visit all nodes from tail to head | `O(n)` | `O(1)` |
| **Search** | Find a node with a given value | `O(n)` | `O(1)` |
| **Length Calculation** | Count the number of nodes | `O(n)` | `O(1)` |

### Code

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
        self.prev = None


class DoublyLinkedList:
    def __init__(self):
        self.head = None

    def insert_at_beginning(self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
            return
        new_node.next = self.head
        self.head.prev = new_node
        self.head = new_node

    def insert_at_end(self, data):
        if self.head is None:
            self.insert_at_beginning(data)
            return
        new_node = Node(data)
        last_node = self.head
        while last_node.next:
            last_node = last_node.next
        last_node.next = new_node
        new_node.prev = last_node

    def insert_at_position(self, data, position):
        if position < 0 or position > self.length():
            raise IndexError("Position out of bounds")
        if position == 0:
            self.insert_at_beginning(data)
            return
        new_node = Node(data)
        current = self.head
        for _ in range(position - 1):
            current = current.next
        new_node.next = current.next
        if current.next:
            current.next.prev = new_node
        current.next = new_node
        new_node.prev = current

    def delete_if_empty_or_single_node(self):
        if self.head is None:
            return True
        if self.head.next is None:
            self.head = None
            return True
        return False

    def delete_from_beginning(self):
        if self.delete_if_empty_or_single_node():
            return
        self.head = self.head.next
        self.head.prev = None

    def delete_from_end(self):
        if self.delete_if_empty_or_single_node():
            return
        last_node = self.head
        while last_node.next:
            last_node = last_node.next
        last_node.prev.next = None

    def delete_at_position(self, position):
        if position < 0 or position >= self.length():
            raise IndexError("Position out of bounds")
        if position == 0:
            self.delete_from_beginning()
            return
        current = self.head
        for _ in range(position):
            current = current.next
        if current.next:
            current.next.prev = current.prev
        current.prev.next = current.next

    def traverse_forward(self):
        elements = []
        current = self.head
        while current:
            elements.append(current.data)
            current = current.next
        return elements

    def traverse_backward(self):
        elements = []
        current = self.head

        # when it's empty
        if current is None:
            return elements

        # Move current to the last node of the list using a while loop
        while current.next:
            current = current.next

        # Loop until the beginning of the list is reached
        while current:
            elements.append(current.data)
            current = current.prev
        return elements

    def search(self, key):
        current = self.head
        while current:
            if current.data == key:
                return True
            current = current.next
        return False

    def length(self):
        count = 0
        current = self.head
        while current:
            count += 1
            current = current.next
        return count


# Example usage:
dll = DoublyLinkedList()
dll.insert_at_beginning(1)
dll.insert_at_beginning(2)

dll.insert_at_end(3)
dll.insert_at_end(4)

dll.insert_at_position("A", 2)

print(dll.traverse_forward())  # [2, 1, 'A', 3, 4]
print(dll.traverse_backward())  # [4, 3, 'A', 1, 2]

print(dll.length())  # 5
print(dll.search(4))  # True

dll.delete_from_beginning()
print(dll.traverse_forward())  # [1, 'A', 3, 4]

dll.delete_from_end()
print(dll.traverse_forward())  # [1, 'A', 3]

dll.delete_at_position(1)
print(dll.traverse_forward())  # [1, 3]
```

### Advantages

* Bidirectional Traversal
    
* Ease of Deletion
    
* Flexibility in Insertion
    

### Disadvantages

* Increased Memory Usage
    
* More Complex Implementation
    
* Additional Pointer Updates
    

### Real-Life Examples

* Navigation Systems, where we need to move forward and backward between items
    
* Undo/Redo Functionality, where each action is a node, and you can move back and forth between actions.
    
* LRU (Least Recently Used) Cache, where you need to quickly remove and add elements from both ends of the list.