---
title: "Binary Search Tree"
datePublished: Mon Aug 19 2024 18:43:42 GMT+0000 (Coordinated Universal Time)
cuid: cm01cgy1a00050ams4nf18btz
slug: binary-search-tree
tags: algorithms, javascript, dsa, binary-search-tree, datastructure

---

A Binary Search Tree (BST) is a data structure that maintains sorted data in a way that allows for efficient insertion, deletion, and lookup operations. Each node in a BST has the following properties:

1. **Node**: Contains a value (data).
    
2. **Left Child**: A subtree where all the nodes have values less than the parent node's value.
    
3. **Right Child**: A subtree where all the nodes have values greater than the parent node's value.
    

### Basic Operations

1. **Insertion**: Add a node to the BST while maintaining the property that the left child is less than the parent, and the right child is greater.
    
2. **Search**: Find if a value exists in the BST.
    
3. **Deletion**: Remove a node from the BST and ensure the tree remains a valid BST.
    
4. **Traversal**: Visit all the nodes in a specific order (In-order, Pre-order, Post-order).
    

### Code

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

class BinarySearchTree {
  constructor() {
    this.root = null;
  }

  findMin(node = this.root) {
    while (node.left !== null) {
      node = node.left;
    }
    return node.value;
  }

  findMax(node = this.root) {
    while (node.right !== null) {
      node = node.right;
    }
    return node.value;
  }

  insert(value) {
    const newNode = new Node(value);

    if (this.root === null) {
      this.root = newNode;
      return this;
    }

    let current = this.root;
    while (true) {
      if (value === current.value) return undefined; // No duplicate values allowed
      if (value < current.value) {
        if (current.left === null) {
          current.left = newNode;
          return this;
        }
        current = current.left;
      } else {
        if (current.right === null) {
          current.right = newNode;
          return this;
        }
        current = current.right;
      }
    }
  }

  // left-root-right
  inOrderTraversal(node = this.root, result = []) {
    if (node !== null) {
      this.inOrderTraversal(node.left, result);
      result.push(node.value);
      this.inOrderTraversal(node.right, result);
    }
    return result;
  }

  search(value) {
    if (this.root === null) return false;

    let current = this.root;
    while (current) {
      if (value === current.value) return true;
      if (value < current.value) {
        current = current.left;
      } else {
        current = current.right;
      }
    }
    return false;
  }

  delete(value, node = this.root) {
    if (node === null) return node;

    if (value < node.value) {
      node.left = this.delete(value, node.left);
    } else if (value > node.value) {
      node.right = this.delete(value, node.right);
    } else {
      // Node with only one child or no child
      if (node.left === null) return node.right;
      else if (node.right === null) return node.left;

      // Node with two children: Get the in-order successor
      node.value = this.findMin(node.right);

      // Delete the in-order successor
      node.right = this.delete(node.value, node.right);
    }

    return node;
  }
}
```

```javascript
const bst = new BinarySearchTree();
bst.insert(10);
bst.insert(5);
bst.insert(15);
bst.insert(3);
bst.insert(7);
console.log("In-order traversal:", bst.inOrderTraversal()); // [3, 5, 7, 10, 15]

console.log("Search 7:", bst.search(7)); // true
console.log("Search 20:", bst.search(20)); // false

bst.delete(5);
console.log("In-order traversal after deletion:", bst.inOrderTraversal()); // [3, 7, 10, 15]
```

### Explanation

1. **Insertion**: Start at the root and compare the value with the current node. Move left if the value is smaller or right if it's larger. Insert the node in the correct position.
    
2. **Search**: Start at the root and traverse the tree based on comparisons until you either find the value or reach a null node.
    
3. **In-order Traversal**: Recursively visit the left subtree, the root, and then the right subtree. This gives the nodes in sorted order.
    
4. **Deletion**: To delete a node, there are three cases:
    
    * Node has no children (leaf node).
        
    * Node has one child.
        
    * Node has two children (replace with the in-order successor and delete the successor).