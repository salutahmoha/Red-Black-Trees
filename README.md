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

## Applications of Red-Black Trees
- **Databases:** Efficient indexing and searching.
- **Compilers:** Syntax trees for efficient language parsing.
- **Operating Systems:** Process scheduling and memory management.
- **Network Routers:** Efficient lookup in routing tables.

## Advantages of Red-Black Trees
- Ensures logarithmic height, making operations efficient.
- Self-balancing without requiring a complete rebalancing for every operation.
- Well-suited for dynamic data structures with frequent insertions and deletions.
