---
title: "Red Black Tree"
datePublished: Sat Aug 24 2024 18:08:23 GMT+0000 (Coordinated Universal Time)
cuid: cm08gesty000a09jw46ng2u4n
slug: red-black-tree
tags: algorithms, javascript, data-structures, dsa, red-black-tree

---

### Introduction

A **Red-Black Tree** is a balanced binary search tree with an additional color property for each node (either red or black). This ensures that the tree remains balanced, leading to efficient search, insertion, and deletion operations. Here are the properties of a Red-Black Tree:

1. Each node is either red or black.
    
2. The root is always black.
    
3. All leaves (NIL nodes) are black.
    
4. If a red node has children, then the children are always black (no two red nodes can be adjacent).
    
5. Every path from a node to its descendant leaves has the same number of black nodes.
    

### Code

```javascript
class Node {
    constructor(data, color = 'red', left = null, right = null, parent = null) {
        this.data = data;
        this.color = color;
        this.left = left;
        this.right = right;
        this.parent = parent;
    }
}
```

```javascript
class RedBlackTree {
    constructor() {
        this.root = null;
    }

    // Helper function to perform a left rotation
    rotateLeft(x) {
        let y = x.right;
        x.right = y.left;

        if (y.left !== null) {
            y.left.parent = x;
        }

        y.parent = x.parent;

        if (x.parent === null) {
            this.root = y;
        } else if (x === x.parent.left) {
            x.parent.left = y;
        } else {
            x.parent.right = y;
        }

        y.left = x;
        x.parent = y;
    }

    // Helper function to perform a right rotation
    rotateRight(y) {
        let x = y.left;
        y.left = x.right;

        if (x.right !== null) {
            x.right.parent = y;
        }

        x.parent = y.parent;

        if (y.parent === null) {
            this.root = x;
        } else if (y === y.parent.left) {
            y.parent.left = x;
        } else {
            y.parent.right = x;
        }

        x.right = y;
        y.parent = x;
    }

    // Function to fix violations after insertion
    fixViolation(node) {
        while (node !== this.root && node.parent.color === 'red') {
            let parent = node.parent;
            let grandparent = parent.parent;

            if (parent === grandparent.left) {
                let uncle = grandparent.right;

                if (uncle && uncle.color === 'red') {
                    grandparent.color = 'red';
                    parent.color = 'black';
                    uncle.color = 'black';
                    node = grandparent;
                } else {
                    if (node === parent.right) {
                        this.rotateLeft(parent);
                        node = parent;
                        parent = node.parent;
                    }

                    this.rotateRight(grandparent);
                    [parent.color, grandparent.color] = [grandparent.color, parent.color];
                    node = parent;
                }
            } else {
                let uncle = grandparent.left;

                if (uncle && uncle.color === 'red') {
                    grandparent.color = 'red';
                    parent.color = 'black';
                    uncle.color = 'black';
                    node = grandparent;
                } else {
                    if (node === parent.left) {
                        this.rotateRight(parent);
                        node = parent;
                        parent = node.parent;
                    }

                    this.rotateLeft(grandparent);
                    [parent.color, grandparent.color] = [grandparent.color, parent.color];
                    node = parent;
                }
            }
        }

        this.root.color = 'black';
    }

    // Insert function
    insert(data) {
        let node = new Node(data);
        if (this.root === null) {
            node.color = 'black';
            this.root = node;
        } else {
            let current = this.root;
            let parent = null;

            while (current !== null) {
                parent = current;
                if (node.data < current.data) {
                    current = current.left;
                } else {
                    current = current.right;
                }
            }

            node.parent = parent;

            if (node.data < parent.data) {
                parent.left = node;
            } else {
                parent.right = node;
            }

            this.fixViolation(node);
        }
    }

    // In-order traversal to display the tree
    inOrderTraversal(node) {
        if (node !== null) {
            this.inOrderTraversal(node.left);
            console.log(`${node.data} (${node.color})`);
            this.inOrderTraversal(node.right);
        }
    }

    // Function to start in-order traversal
    displayTree() {
        this.inOrderTraversal(this.root);
    }
}
```

```javascript
const tree = new RedBlackTree();
tree.insert(10);
tree.insert(20);
tree.insert(30);
tree.insert(15);
tree.insert(25);
tree.insert(5);

tree.displayTree();
```