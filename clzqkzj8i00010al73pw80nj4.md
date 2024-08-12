---
title: "Linked List"
datePublished: Mon Aug 12 2024 05:56:38 GMT+0000 (Coordinated Universal Time)
cuid: clzqkzj8i00010al73pw80nj4
slug: linked-list
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1723442427954/f9d4fa1c-4a6c-4664-ac23-657a18d30c36.png
tags: javascript, data-structures, linkedlists

---

A **Linked List** is a linear data structure where each element, called a node, contains a **data** part and a **reference** to the next node in the sequence. Unlike arrays, linked lists do not require contiguous memory locations, allowing for efficient memory use and dynamic size adjustments.

#### **Types of Linked Lists:**

1. **Singly Linked List:**
    
    * Each node contains data and a reference to the next node.
        
    * It allows traversal in one direction, from the head (first node) to the tail (last node).
        
2. **Doubly Linked List:**
    
    * Each node has two references: one to the next node and one to the previous node.
        
    * This allows traversal in both forward and backward directions.
        
3. **Circular Linked List:**
    
    * The last node in the list points back to the first node, forming a circle.
        
    * Can be singly or doubly linked, allowing for continuous traversal.
        
4. **Circular Doubly Linked List:**
    
    * A combination of circular and doubly linked lists.
        
    * Each node points to both the next and previous nodes, with the last node linking back to the first and vice versa.
        

#### **Key Characteristics:**

* **Dynamic Size:** Linked lists can easily grow or shrink in size by adding or removing nodes.
    
* **Non-Contiguous Storage:** Nodes are stored in non-contiguous memory locations, linked together by pointers.