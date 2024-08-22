---
title: "AVL Trees"
datePublished: Thu Aug 22 2024 18:36:31 GMT+0000 (Coordinated Universal Time)
cuid: cm05mj9mo000d09mgb8gi1rrj
slug: avl-trees
tags: algorithms, javascript, data-structures, dsa, avl-trees

---

### Introduction

An AVL tree is a self-balancing binary search tree (BST) where the difference in heights between the left and right subtrees of any node (also called the balance factor) is at most 1.

* **Balance Factor**: The balance factor of a node is the difference between the heights of its left and right subtrees.
    
* **Rotations**: To maintain balance, AVL trees use rotations:
    
    * **Right Rotation (RR Rotation)**: Used when the left subtree is taller.
        
    * **Left Rotation (LL Rotation)**: Used when the right subtree is taller.
        
    * **Left-Right Rotation (LR Rotation)**: A combination of left and right rotations.
        
    * **Right-Left Rotation (RL Rotation)**: A combination of right and left rotations.
        

### Code

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
    this.height = 1;
  }
}
```

```javascript
class AVL {
  constructor() {
    this.root = null;
  }

  getHeight(node) {
    return node ? node.height : 0;
  }

  getBalanceFactor(node) {
    return node ? this.getHeight(node.left) - this.getHeight(node.right) : 0;
  }

  rotateRight(y) {
    const x = y.left;
    const T2 = x.right;

    x.right = y;
    y.left = T2;

    y.height = Math.max(this.getHeight(y.left), this.getHeight(y.right)) + 1;
    x.height = Math.max(this.getHeight(x.left), this.getHeight(x.right)) + 1;

    return x;
  }

  rotateLeft(x) {
    const y = x.right;
    const T2 = y.left;

    y.left = x;
    x.right = T2;

    x.height = Math.max(this.getHeight(x.left), this.getHeight(x.right)) + 1;
    y.height = Math.max(this.getHeight(y.left), this.getHeight(y.right)) + 1;

    return y;
  }

  insert(node, value) {
    if (!node) {
      return new Node(value);
    }

    if (value < node.value) {
      node.left = this.insert(node.left, value);
    } else if (value > node.value) {
      node.right = this.insert(node.right, value);
    } else {
      return node;
    }

    node.height =
      1 + Math.max(this.getHeight(node.left), this.getHeight(node.right));

    const balance = this.getBalanceFactor(node);

    if (balance > 1 && value < node.left.value) {
      return this.rotateRight(node);
    }

    if (balance < -1 && value > node.right.value) {
      return this.rotateLeft(node);
    }

    if (balance > 1 && value > node.left.value) {
      node.left = this.rotateLeft(node.left);
      return this.rotateRight(node);
    }

    if (balance < -1 && value < node.right.value) {
      node.right = this.rotateRight(node.right);
      return this.rotateLeft(node);
    }

    return node;
  }

  insertValue(value) {
    this.root = this.insert(this.root, value);
  }

  minValueNode(node) {
    let current = node;
    while (current.left !== null) {
      current = current.left;
    }
    return current;
  }

  delete(node, value) {
    if (!node) {
      return node;
    }

    if (value < node.value) {
      node.left = this.delete(node.left, value);
    } else if (value > node.value) {
      node.right = this.delete(node.right, value);
    } else {
      if (!node.left || !node.right) {
        let temp = node.left ? node.left : node.right;
        if (!temp) {
          temp = node;
          node = null;
        } else {
          node = temp;
        }
      } else {
        let temp = this.minValueNode(node.right);
        node.value = temp.value;
        node.right = this.delete(node.right, temp.value);
      }
    }

    if (!node) {
      return node;
    }

    node.height =
      Math.max(this.getHeight(node.left), this.getHeight(node.right)) + 1;

    const balance = this.getBalanceFactor(node);

    if (balance > 1 && this.getBalanceFactor(node.left) >= 0) {
      return this.rotateRight(node);
    }

    if (balance > 1 && this.getBalanceFactor(node.left) < 0) {
      node.left = this.rotateLeft(node.left);
      return this.rotateRight(node);
    }

    if (balance < -1 && this.getBalanceFactor(node.right) <= 0) {
      return this.rotateLeft(node);
    }

    if (balance < -1 && this.getBalanceFactor(node.right) > 0) {
      node.right = this.rotateRight(node.right);
      return this.rotateLeft(node);
    }

    return node;
  }

  deleteValue(value) {
    this.root = this.delete(this.root, value);
  }

  search(node, value) {
    if (node === null || node.value === value) {
      return node;
    }

    if (value < node.value) {
      return this.search(node.left, value);
    }

    return this.search(node.right, value);
  }

  searchValue(value) {
    return this.search(this.root, value);
  }

  preOrder(node) {
    if (node !== null) {
      console.log(node.value);
      this.preOrder(node.left);
      this.preOrder(node.right);
    }
  }
}
```

```javascript
const avl = new AVL();
avl.insertValue(10);
avl.insertValue(20);
avl.insertValue(30);
avl.insertValue(40);
avl.insertValue(50);
avl.insertValue(25);

console.log("Pre-order traversal after insertions:");
avl.preOrder(avl.root);

avl.deleteValue(30);

console.log("Pre-order traversal after deletion of 30:");
avl.preOrder(avl.root);

const foundNode = avl.searchValue(50);
console.log(
  `Node with value 50 ${foundNode ? "found" : "not found"} in the tree.`
);
```

### Time and Space Complexity

**Insert**:

* **Time Complexity**: O(log n) Inserting a node in an AVL tree involves first performing a standard Binary Search Tree (BST) insertion, which takes O(log n) time due to the tree's balanced nature. After the insertion, the tree may need to be rebalanced by performing rotations, which also takes O(log n) time in the worst case.
    
* **Space Complexity**: O(log n) auxiliary space due to the recursion stack.
    

**Deletion**

* **Time Complexity**: O(log n) The deletion process includes finding the node to be deleted, which takes O(log n) time, and rebalancing the tree, which also takes O(log n) time.
    
* **Space Complexity**: O(log n) auxiliary space due to the recursion stack.
    

**Search**

* **Time Complexity**: O(log n) Since the tree is balanced, searching for a value involves traversing from the root to a leaf, which takes O(log n) time.
    
* **Space Complexity**: O(log n) auxiliary space due to the recursion stack.