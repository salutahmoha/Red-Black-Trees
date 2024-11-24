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