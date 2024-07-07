---
title: "Single Linked List"
datePublished: Sun Jul 07 2024 12:10:39 GMT+0000 (Coordinated Universal Time)
cuid: clybihul4000208mi69pk03sc
slug: sll
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720354112790/15f534ed-f727-426a-b401-80f8f3f28168.jpeg
tags: python, data-structures, python3, dsa, codenewbies, linked-list-singly-linked-list

---

* A **singly linked list** is a linear data structure in which elements, called nodes, are connected by pointers.
    
* Each node contains two parts: data and a pointer to the next node in the sequence.
    
* The list terminates with a node pointing to `null`.
    
* Example: Trains
    

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


class SingleLinkedList:
    def __init__(self):
        self.head = None

    def insert_at_beginning(self, data):
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node

    def insert_at_end(self, data):
        if not self.head:
            self.insert_at_beginning(data)
            return
        new_node = Node(data)
        last_node = self.head
        while last_node.next:
            last_node = last_node.next
        last_node.next = new_node

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
        current.next = new_node

    def delete_from_beginning(self):
        if not self.head:
            return
        self.head = self.head.next

    def delete_from_end(self):
        if not self.head:
            return
        if not self.head.next:
            self.head = None
            return
        second_last = self.head
        while second_last.next.next:
            second_last = second_last.next
        second_last.next = None

    def delete_at_position(self, position):
        if position < 0 or position >= self.length():
            raise IndexError("Position out of bounds")
        if position == 0:
            self.delete_from_beginning()
            return
        current = self.head
        for _ in range(position - 1):
            current = current.next
        current.next = current.next.next

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

    def traverse(self):
        elements = []
        current = self.head
        while current:
            elements.append(current.data)
            current = current.next
        return elements


sll = SingleLinkedList()

sll.insert_at_beginning(1)
sll.insert_at_beginning(2)
print(sll.traverse())  # [2,1]

sll.insert_at_end(3)
sll.insert_at_end(4)
print(sll.traverse())  # [2, 1, 3, 4]

sll.insert_at_position("A", 1)
sll.insert_at_position("B", 2)
print(sll.traverse())  # [2, 'A', 'B', 1, 3, 4]

sll.delete_from_beginning()
print(sll.traverse())  # ['A', 'B', 1, 3, 4]

sll.delete_from_end()
print(sll.traverse())  # ['A', 'B', 1, 3]

sll.delete_at_position(1)
print(sll.traverse())  # ['A', 1, 3]

print(sll.length())  # 3

print(sll.search(3))  # True
print(sll.search("B"))  # False
```

### Advantages

* **Dynamic size**: Linked lists can grow or shrink in size dynamically.
    
* **Ease of insertion/deletion**: Adding or removing nodes is straightforward and efficient, especially at the beginning of the list.
    

### Disadvantages

* **Memory overhead**: Extra memory is required for storing pointers.
    
* **Sequential access**: Linked lists do not allow random access. Elements must be accessed sequentially from the head.
    
* **Cache locality**: Nodes in a linked list are not stored contiguously in memory, which can lead to poor cache performance.