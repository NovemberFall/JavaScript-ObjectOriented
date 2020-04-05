# 12. Binary Search Tree

# What is a tree?

`A data structure that consists of nodes in a parent/child relationship`

- Lists - linear

- Trees - nonlinear

- A Singly Linked List sort of a special case of a tree

---

`Tree Terminology`

- Root - The top node in a tree

- Child - A node directly connected to another node when moving away from the Root

- Parent - The converse notion of a child.

- Siblings - A group of nodes with the same parent.

- Leaf - A node with no child

- Edge - The connection between one node and another

---
`Trees Lots of different applications`

- Html DOM

- Network routing 

- Abstract Syntax Tree

- Artficial Intelligence

- Folders in Operating Systems

- Computer File Systems

---

`Kinds of Trees`

- Trees

- Binary Tress

- Binary Search Trees

---
`How BSTS work?`

- Every parent node has at most **two** children

- Every node to the left of a parent node is **always less** than the parent

- Every node to the right of a parent node is **always greater** than the parent

`The BinarySearchTree class`

```js
class BinarySearchTree{
    constructor(){
        this.root = null;
    }
}

class Node{
    constructor(value){
        this.value = value;
        this.left = null;
        this.right = null;
    }
}
```