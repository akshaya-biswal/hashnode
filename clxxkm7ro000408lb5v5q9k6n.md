---
title: "Tree Traversal"
datePublished: Thu Jun 27 2024 18:01:15 GMT+0000 (Coordinated Universal Time)
cuid: clxxkm7ro000408lb5v5q9k6n
slug: tree-traversal
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1719511221483/99fb065f-8910-4c5c-84dd-a23304f422af.png
tags: python, tree, dsa, bfs, dfs, treetraversals

---

Traversing a tree means visiting every node in the tree.

### Types

* **Breadth First Search (BFS)** is when you visit all the nodes on one level before moving to the next level. This means you explore the tree sideways.
    
* **Depth First Search (DFS)** is when you go down the tree to the leaf nodes, exploring each branch from top to bottom.
    
    There are three types:
    
    * Preorder
        
    * Inorder
        
    * Postorder
        

### **DFS**

**Inorder traversal**

1. [First,](https://www.w3schools.com/dsa/dsa_algo_binarytrees_preorder.php) [visit](https://www.w3schools.com/dsa/dsa_algo_binarytrees_inorder.php) [all the](https://www.w3schools.com/dsa/dsa_algo_binarytrees_preorder.php) [nod](https://www.w3schools.com/dsa/dsa_algo_binarytrees_inorder.php)[es in th](https://www.w3schools.com/dsa/dsa_algo_binarytrees_preorder.php)[e left s](https://www.w3schools.com/dsa/dsa_algo_binarytrees_inorder.php)ub[tree](https://www.w3schools.com/dsa/dsa_algo_binarytrees_postorder.php)
    
2. [Th](https://www.w3schools.com/dsa/dsa_algo_binarytrees_postorder.php)en the root node
    
3. Visit all the nodes in the right subtree
    

**Preorder traversal**

1. Visit root node
    
2. Visit all the nodes in the left subtree
    
3. Visit all the nodes in the right subtree
    

**Postorder traversal**

1. Visit all the nodes in the left subtree
    
2. Visit all the nodes in the right subtree
    
3. Visit the root node
    

### Code

```python
class Node:
    def __init__(self, item):
        self.left = None
        self.right = None
        self.val = item


def in_order(root):

    if root:
        in_order(root.left)
        print(str(root.val) + "->", end=" ")
        in_order(root.right)


def post_order(root):

    if root:
        post_order(root.left)
        post_order(root.right)
        print(str(root.val) + "->", end=" ")


def pre_order(root):

    if root:
        print(str(root.val) + "->", end=" ")
        pre_order(root.left)
        pre_order(root.right)


root = Node(1)
root.left = Node(2)
root.right = Node(3)
root.left.left = Node(4)
root.left.right = Node(5)

print("In order")
in_order(root)  # 4-> 2-> 5-> 1-> 3->

print("\nPre order")
pre_order(root)  # 1-> 2-> 4-> 5-> 3->

print("\nPost order")
post_order(root)  # 4-> 5-> 2-> 3-> 1->
```