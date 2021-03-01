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
  | 1 | 1 | 1 |
  | 2 | 2 | 3 |
  | 3 | 4 | 7 |
  | 4 | 8 | 15 |
  | 5 | 16 | 31 |
  | 6 | 32 | 63 |

# Binary tree node

- A node which contains a signle data item and pointers for the left and right child

```csharp
class BSTNode<T>
{
    public BSTNode(T value)
    {
        Data = value;
    }
    public T Data;
    public BSTNode<T> Left;
    public BSTNode<T> Right;
}

class Program{
    static void Main(){
        var root = new BSTNode<string>("root");
        root.Left = new BSTNode<string>("left")
        root.Right = new BSTNode<string>("right")
    }
}
```

# Binary search tree

- A binary tree where nodes:
  - With `lessor` values are placed to the `left of the root`
  - With `equal or greater` values are placed `to the right`
- Examples: 12 -> 14 -> 7 -> 7 -> 18 -> 3

```
      12
  7       14
3   7       18

```

# Complexity

- Average: O(logn)
- Worst: O(n)

# Balance tree

```
      12
  7       14
3   7       18

```

# Unbalance tree

```
      12
         14
           18
             20

```
# Data structures for tree traversal
- `Depth-first` search is easily implemented via a `stack`, including recursively (via the call stack)
- `Breadth-first` search is easily implemented via a `queue`, including corecursively
# Depth-first search of binary tree
- These searches are referred to as depth-first search (DFS), since the search tree is `deepened as much as possible on each child` before going to the next sibling. For a binary tree, they are defined as access operations at each node, starting with the current node, whose algorithm is as follows:
- The general recursive pattern for traversing a binary tree is this:

  - Go down one level to the recursive argument N. If N exists (is non-empty) execute the following three operations in a certain order:[5]
    - L: Recursively traverse N's left subtree.
    - R: Recursively traverse N's right subtree.
    - N: Access (visit) the current node N itself.
  - Return by going up one level and arriving at the parent node of N.
- There are three methods (patterns) at which position of the parcours (traversal) relative to the node (in the figure: red, green, or blue) the visit (access) of the node shall take place. The choice of exactly one color determines exactly one visit of a node as described below. Access at all three colors results in a threefold visit of the same node yielding the “all-order” sequentialisation:
- Ref: https://en.wikipedia.org/wiki/Tree_traversal#Pre-order,_NLR
# Tree Traversals

## Pre-order
- The node is visited before its children
  - Process the current value -> Visit the left child -> Visit the right child
## In-order
- The left child is visited before the node, then the right child
## Post-order
- The left and right children are visited before the node