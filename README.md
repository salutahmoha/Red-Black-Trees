# Red-Black-Trees
It is a type of self-balancing binary search tree used to efficiently maintain sorted data. It ensures that the tree remains balanced, making operations such as insertion, deletion, and search operate in O(log n) time.

## Properties of Red-Black Trees
Red-Black Trees follow these key properties:
- **Node Colors**: Each node is either red or black.
- **Root is Black**: The root node is always black.
- **Red Node Rule**: A red node cannot have a red child (no two consecutive red nodes).
- **Black-Height Property**: Every path from a node to its descendant null pointers (leaves) contains the same number of black nodes.
- **Leaf Nodes**: Null pointers (leaves) are considered black.

These properties ensure that the longest path from the root to a leaf is at most twice the shortest path, maintaining a balanced tree.

## How Red-Black Trees Work
### Insertion
- Insert a new node as in a Binary Search Tree.
- Color the new node red.
- Fix violations of the Red-Black Tree properties by:
   - **Recoloring:** Adjust the colors of nodes.
   - **Rotations:** Perform left or right rotations to restructure the tree.

### Deletion
- Delete the node as in a Binary Search Tree.
- If the deleted node is black, fix violations using:
   - **Recoloring:** Adjust the colors to maintain the black-height property.
   - **Rotations:** Restructure the tree if necessary.

### Balancing
Red-Black Trees balance themselves through recoloring and rotations, ensuring that the tree height is always O(log n).

## Implementation  of a **Red-Black Tree** in JavaScript
```
class Node {
    constructor(data) {
        this.data = data;
        this.color = 'red';
        this.left = null;
        this.right = null;
        this.parent = null;
    }
}

class RedBlackTree {
    constructor() {
        this.TNULL = new Node(0); 
        this.TNULL.color = 'black';
        this.root = this.TNULL;
    }

    // Left rotation
    rotateLeft(x) {
        let y = x.right;
        x.right = y.left;
        if (y.left !== this.TNULL) {
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

    // Right rotation
    rotateRight(x) {
        let y = x.left;
        x.left = y.right;
        if (y.right !== this.TNULL) {
            y.right.parent = x;
        }
        y.parent = x.parent;
        if (x.parent === null) {
            this.root = y;
        } else if (x === x.parent.right) {
            x.parent.right = y;
        } else {
            x.parent.left = y;
        }
        y.right = x;
        x.parent = y;
    }

    // Fix violations of Red-Black Tree properties after insertion
    fixInsert(k) {
        while (k.parent.color === 'red') {
            if (k.parent === k.parent.parent.right) {
                let u = k.parent.parent.left;
                if (u.color === 'red') {
                    u.color = 'black';
                    k.parent.color = 'black';
                    k.parent.parent.color = 'red';
                    k = k.parent.parent;
                } else {
                    if (k === k.parent.left) {
                        k = k.parent;
                        this.rotateRight(k);
                    }
                    k.parent.color = 'black';
                    k.parent.parent.color = 'red';
                    this.rotateLeft(k.parent.parent);
                }
            } else {
                let u = k.parent.parent.right;
                if (u.color === 'red') {
                    u.color = 'black';
                    k.parent.color = 'black';
                    k.parent.parent.color = 'red';
                    k = k.parent.parent;
                } else {
                    if (k === k.parent.right) {
                        k = k.parent;
                        this.rotateLeft(k);
                    }
                    k.parent.color = 'black';
                    k.parent.parent.color = 'red';
                    this.rotateRight(k.parent.parent);
                }
            }
            if (k === this.root) {
                break;
            }
        }
        this.root.color = 'black';
    }

    // Insert a new node with the given key
    insert(key) {
        let node = new Node(key);
        node.parent = null;
        node.data = key;
        node.left = this.TNULL;
        node.right = this.TNULL;
        node.color = 'red'; 

        let y = null;
        let x = this.root;

        // Find the appropriate position to insert the new node
        while (x !== this.TNULL) {
            y = x;
            if (node.data < x.data) {
                x = x.left;
            } else {
                x = x.right;
            }
        }

        node.parent = y;
        if (y === null) {
            this.root = node;
        } else if (node.data < y.data) {
            y.left = node;
        } else {
            y.right = node;
        }

        // Fix Red-Black Tree violations
        this.fixInsert(node);
    }

    // In-order traversal of the tree
    inorderHelper(node) {
        if (node !== this.TNULL) {
            this.inorderHelper(node.left);
            console.log(node.data);
            this.inorderHelper(node.right);
        }
    }

    // Start in-order traversal from the root
    inorder() {
        this.inorderHelper(this.root);
    }

    // Print the tree (for debugging purposes)
    printTree() {
        this.inorder();
    }
}

// Example usage:

let rbt = new RedBlackTree();
rbt.insert(20);
rbt.insert(15);
rbt.insert(25);
rbt.insert(10);
rbt.insert(5);
rbt.insert(1);

console.log("In-order traversal:");
rbt.printTree();

```

## Applications of Red-Black Trees
- **Databases:** Efficient indexing and searching.
- **Compilers:** Syntax trees for efficient language parsing.
- **Operating Systems:** Process scheduling and memory management.
- **Network Routers:** Efficient lookup in routing tables.

## Advantages of Red-Black Trees
- Ensures logarithmic height, making operations efficient.
- Self-balancing without requiring a complete rebalancing for every operation.
- Well-suited for dynamic data structures with frequent insertions and deletions.
