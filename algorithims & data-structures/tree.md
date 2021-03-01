# Intro

- Tree is a data structure where nodes have a `1 : N parent-child` relationship
- Properties:
  - 0 or 1 parent node
  - 0-N child nodes(binary,trinary,k-ary)
  - leaf nodes have no children
- Examples:
  - reporting structure
  - file system

# Binary Tree
- It has at most 2 childrens
- Every node in the tree can itself be thought of as a root node of a smaller distinct tree
- Properties:
  - Root node: top most node in the tree
  - Parent and children
  - Edges connect nodes
  - Leaf nodes with have no childrens
  - Internal nodes that are neither root or leaf node
  - Degree of a tree: maximum number of childrens each node can have
  - Height of the node: maximum number of edges between that node and leaf. In general, we refering to the maximum height though all of its child paths.
  - Level of the node: is the number 1 + number of edges between that node and the root.
- Examples: A binary tree with 6 nodes and 3 levels
  | Level | Max node on level | Max total nodes |
  |-------|-------------------|-----------------|
  | 1     | 1                 | 1               |
  | 2     | 2                 | 3               |
  | 3     | 4                 | 7               |
  | 4     | 8                 | 15              |
  | 5     | 16                 | 31              |
  | 6     | 32                 | 63              |