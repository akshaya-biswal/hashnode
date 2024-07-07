---
title: "Circular Linked List"
datePublished: Sun Jul 07 2024 19:20:43 GMT+0000 (Coordinated Universal Time)
cuid: clybxuwwz000008jyfj2o231k
slug: cll
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720379853091/19274ab9-319d-481d-ab92-0684c7400c84.jpeg
tags: python, data-structures, python3, codenewbies, circular-linked-list

---

* A **circular linked list** is a variation of a linked list in which the last node points back to the first node, forming a circle.
    
* This can be implemented using either singly or doubly linked lists.
    

### Operations

| Operation | Description | Time Complexity | Space Complexity |
| --- | --- | --- | --- |
| **Insertion** |  |  |  |
| At the beginning | Insert a node at the start | `O(1)` | `O(1)` |
| At the end | Insert a node at the end | `O(n)` | `O(1)` |
| At a specific position | Insert a node at a given position | `O(n)` | `O(1)` |
| **Deletion** |  |  |  |
| From the beginning | Remove a node from the start | `O(1)` | `O(1)` |
| From the end | Remove a node from the end | `O(n)` | `O(1)` |
| From a specific position | Remove a node at a given position | `O(n)` | `O(1)` |
| **Traversal** | Visit all nodes in the list | `O(n)` | `O(1)` |
| **Search** | Find a node with a given value | `O(n)` | `O(1)` |
| **Length Calculation** | Count the number of nodes | `O(n)` | `O(1)` |

### Code

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None


class CircularLinkedList:
    def __init__(self):
        self.head = None

    # Helper function to find the last node
    def get_last_node(self):
        if not self.head:
            return None
        last_node = self.head
        while last_node.next != self.head:
            last_node = last_node.next
        return last_node

    # Helper function to check if the list is empty or has only one node
    def check_empty_or_single_node_for_delete(self):
        if not self.head:
            return True
        if self.head.next == self.head:  # If only one node is present
            self.head = None
            return True
        return False

    def insert_node(self, new_node):
        if not self.head:  # If list is empty
            self.head = new_node
            new_node.next = new_node
        else:
            last_node = self.get_last_node()
            new_node.next = self.head
            last_node.next = new_node

    def insert_at_beginning(self, data):
        new_node = Node(data)
        self.insert_node(new_node)
        self.head = new_node

    def insert_at_end(self, data):
        new_node = Node(data)
        self.insert_node(new_node)

    def insert_at_position(self, data, position):
        if position < 0 or position > self.length():
            raise IndexError("Position out of bounds")
        if position == 0:
            self.insert_at_beginning(data)
            return
        new_node = Node(data)
        # Traverse to the node before the desired position
        current = self.head
        for _ in range(position - 1):
            current = current.next
        new_node.next = current.next
        current.next = new_node

    def delete_from_beginning(self):
        if self.check_empty_or_single_node_for_delete():
            return
        last_node = self.get_last_node()
        self.head = self.head.next
        last_node.next = self.head

    def delete_from_end(self):
        if self.check_empty_or_single_node_for_delete():
            return
        # Traverse to the second last node
        second_last = self.head
        while second_last.next.next != self.head:
            second_last = second_last.next
        second_last.next = self.head

    def delete_at_position(self, position):
        if position < 0 or position >= self.length():
            raise IndexError("Position out of bounds")
        if position == 0:
            self.delete_from_beginning()
            return
        current = self.head
        # Traverse to the node before the desired position
        for _ in range(position - 1):
            current = current.next
        current.next = current.next.next

    def traverse(self):
        elements = []
        if not self.head:
            return elements
        current = self.head
        while True:
            elements.append(current.data)
            current = current.next
            if current == self.head:
                break
        return elements

    def search(self, key):
        if not self.head:
            return False
        current = self.head
        while True:
            if current.data == key:
                return True
            current = current.next
            if current == self.head:
                break
        return False

    def length(self):
        if not self.head:
            return 0
        count = 1
        current = self.head
        while current.next != self.head:
            count += 1
            current = current.next
        return count


# Example usage:
cll = CircularLinkedList()
cll.insert_at_beginning(1)
cll.insert_at_beginning(2)

cll.insert_at_end(3)
cll.insert_at_end(4)

cll.insert_at_position("A", 2)
print(cll.traverse())  # [2, 1, 'A', 3, 4]

print(cll.length())  # 5
print(cll.search(4))  # True

cll.delete_from_beginning()
cll.delete_from_end()
print(cll.traverse())  # [1, 'A', 3]

cll.delete_at_position(1)
print("List after deletion at position 1:", cll.traverse())  # [1, 3]
```

### Advantages

* Bidirectional Traversal, nodes can be traversed in both forward and backward directions due to the two pointers (`next` and `prev`).
    
* Ease of Deletion, as we have direct access to the previous node, unlike singly linked lists where we have to traverse from the head to find the previous node.
    
* Flexibility in Insertion, more straightforward as you can easily update both `next` and `prev` pointers.
    

### Disadvantages

* Increased Memory Usage
    
* More Complex Implementation
    
* Additional Pointer Updates
    

### Real-Life Examples

* Navigation Systems
    
* Undo/Redo Functionality
    
* LRU (Least Recently Used) Cache
    
* File Systems