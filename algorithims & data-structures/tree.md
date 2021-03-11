# Intro

- Tree is a data structure where nodes have a `1 : N parent-child` relationship
- Properties:
  - 0 or 1 parent node
  - 0-N child nodes(binary,trinary,k-ary)
  - leaf nodes have no children
- Insert, remove, and search operations are `O(log n)` average case
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

# Unbalance tree

- A tree whose left and right children have uneven heights.
- A fully unbalanced binary tree is just a linked list with `O(n)` algorithmic complexity
- Complexity: `O(n)`

```
      12
         14
           18
             20

```

# Height

- The maximum number of edges between the root and leaf nodes.

```
      12
                  ----> 1
  7       14
                  ----> 2
3   7       18

```

```
      12
                  ----> 1
         14
                  ----> 2
           18
                  ----> 3
             20

```

# Balance tree

- A binary search tree whose maximum height is minimized
- If any two sibling subtrees do not differ in height by more than one level. In other words,any two leaves should not have a difference in depth that is more than one level
- Complexity: `O(logn)`

```
      12
  7       14
3   7       18

```

# Balance factor

- The difference between the height of the left and right sub-trees.

```
      4

Left Height: 0
Right Height: 0
Balance Factor: 0
```

```
      4
  2

Left Height: 1
Right Height: 0
Balance Factor: -1
```

```
      4
          5
              6

Left Height: 0
Right Height: 2
Balance Factor: 2
```

# Heavy

- The state when the balance factor of a node differs by more than one.

```
      4
    2
  1

Left Height: 2
Right Height: 0
Balance Factor: -2
```

```
      4
    2   5
  1       6

Left Height: 2
Right Height: 2
Balance Factor: 0
```

# Diff from balance and unbalance tree

```
Balance tree: The difference between the left and right subtrees is not more than 1 level.
        4
    2      5
  1   3  4   6
                8

Unbalance tree: The difference between the left and right subtrees is more than 1 level in height.
        4
    2      5
         4   6
                8
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

- Average case : O(n)
- Worst case : O(n)

```csharp
class BinaryTreeNode<TNode> {
  public BinaryTreeNode<TNode> Left { get; set; }
  public BinaryTreeNode<TNode> Right { get; set; }
  public TNode Value { get; set; }
}

class BinaryTree<T> {
  public BinaryTreeNode<T> Root { get; set; }

  public void Add(T value)
  {
    if(Root == null)
    {
      Root = new BinaryTreeNode<T>(value);
    }
    else {
      AddTo(Root, value);
    }
  }

  public void AddTo(TNode node, T value)
  {
    if (node.Value.CompareTo(value) < 0)
    {
      if(node.Left == null)
      {
        node.Left = new BinaryTreeNode<T>(value);
      }
      else
      {
        AddTo(node.Left, value);
      }
    }
    else
    {
      if(node.Right == null)
      {
        node.Right = new BinaryTreeNode<TNode>(node);
      }
      else
      {
        AddTo(node.Right, value);
      }
    }
  }
}
```

## Pre-order

- The node is visited before its children
- Process the current value -> Visit the left child -> Visit the right child
- The pre-order traversal is a topologically sorted one, because `a parent node is processed before any of its child nodes is done`.

```
      12
  7       14
3   7       18

1. Access the data part of the current node (in the figure: position red).
2. Traverse the left subtree by recursively calling the pre-order function.
3. Traverse the right subtree by recursively calling the pre-order function.

Steps: 12 -> 7 -> 3 -> 7 -> 14 -> 18
```

```csharp
class BinaryTree<TNode> {

  public void PreOrderTraversal(Action action)
  {
    PreOrderTraversal(action, Root)
  }
  public void PreOrderTraversal(Action action, TNode node)
  {
    if(node != null)
    {
      action(node.Value);
      PreOrderTraversal(node.Left);
      PreOrderTraversal(node.Right);
    }
  }
}
```

- Copy a tree

```csharp
class Program {
  static void Main(){
  //          10
  //      5        20
  //    4   6    15
  //           12
  //             13
  //               14
  BinaryTree<int> expected = new BinaryTree<int>();
  expected.Add(10);
  expected.Add(5);
  expected.Add(4);
  expected.Add(6);

  expected.Add(20);
  expected.Add(15);
  expected.Add(12);
  expected.Add(13);
  expected.Add(14);

  BinaryTree<int> actual = new BinaryTree<int>();
  expected.PreOrderTraversal((value) => actual.Add(value));
  }
}
```

## In-order

- The left child is visited before the node, then the right child
- Visit the left child -> Process the current value -> Visit the right child

```
      12
  7       14
3   7       18

1. Traverse the left subtree by recursively calling the in-order function.
2. Access the data part of the current node (in the figure: position green).
3. Traverse the right subtree by recursively calling the in-order function.

Steps: 3 -> 7 -> 7 -> 12 -> 14 -> 18
```

```csharp
class BinaryTree<TNode> {

  public void InOrderTraversal(Action action)
  {
    InOrderTraversal(action, Root)
  }
  public void InOrderTraversal(Action action, TNode node)
  {
    if(node != null)
    {
      PreOrderTraversal(node.Left);
      action(node.Value);
      PreOrderTraversal(node.Right);
    }
  }
}
```

## Post-order

- The left and right children are visited before the node
- Visit the left child -> Visit the right child -> Process the current value

```
      12
  7       14
3   7       18

1. Traverse the left subtree by recursively calling the post-order function.
2. Traverse the right subtree by recursively calling the post-order function.
3. Access the data part of the current node (in the figure: position blue).

Steps: 3 -> 7 -> 7 -> 18 -> 14 -> 12
```

```csharp
class BinaryTree<TNode> {

  public void PostOrderTraversal(Action action)
  {
    PostOrderTraversal(action, Root)
  }
  public void PostOrderTraversal(Action action, TNode node)
  {
    PostOrderTraversal(node.Left);
    PostOrderTraversal(node.Right);
    action(node.Value);
  }
}
```

# Search

- Average : O(n)
- Worst : O(n)

```csharp
public T FindWithParent(T value, out BinaryTree<T> Parent)
{
  var current = Root;
  var parent = null;
  while(current != null)
  {
    if(current.CompareTo(value) > 0)
    {
      // if the value is less than current, go left.
      parent = current;
      current = current.Left;
    }
    else if(current.CompareTo(value) < 0)
    {
      // if the value is more than current, go right.
      parent = current;
      current = current.Right;
    }
    else
    {
      break;
    }
  }
  return current;
}
```

# Remove

- There are 3 cases:
  - No children (Leaf)
  - 1 children
  - 2 childrens:
    - Find the node
    - Go to the right child
    - Go to the left-most child
    - Replace deleted node with successor
    - Move the successor's child up
- Complexity:
  - Average: O(log n)
  - Worst: O(n)
- Steps
  - Case 1: If current has no right child, then current's left replaces current
  - Case 2: If current's right child has no left child, then current's right child replaces current
  - Case 3: If current's right child has a left child, replace current with current's right child's left-most child

```csharp
// cases:
// 1. Remove leaf
// 2. Remove root one child on left
// 3. Remove root one child on right
// 4. Remove root two childs
// 5. Remove one child left
// 6. Remove one child right
// 7. Remove two childs
// 8. Remove root only
void Remove(T value)
{
  var current = FindWithParent(value,Root);
  if(current == null)
  {
    return;
  }

  // Remove leaf or one-child node

  // Case 1: If current has no right child
  // then current's left replaces current
  // There are only left side sub-tree
  if(current.Right == null)
  {
    // remove root still having left child
    if(parent == null)
    {
      Root = current.Left;
    }
    // either leaf or one child node
    else
    {
      var result = parent.CompareTo(current.Value);
      // parent value greater than current value
      if(result > 0)
      {
        parent.Left = current.Left;
      }
      // parent value less than current value
      else
      {
        parent.Right = current.Left;
      }
    }
  }
  else if(current.Left == null)
  {
    // ...
    // executing like above only except:
    else
    {
       var result = parent.CompareTo(current.Value);
      // parent value greater than current value
      if(result > 0)
      {
        parent.Left = current.Right;
      }
      // parent value less than current value
      else
      {
        parent.Right = current.Right;
      }
    }
  }
  else if(current.Right.Left == null)
  {

  }
  // Remove two-childrens node
  else{
    var leftMost = current.Right.Left;
    var parentLeftMost = current.Right

    while(leftMost.Left != null)
    {
      parentLeftMost = leftMost;
      leftMost = leftMost.Left;
    }
    parentLeftMost.Left = leftMost.Right;
    leftMost.Left = current.Left;
    leftMost.Right = current.Right;

    if(parent == null)
    {
      Root = leftMost
    }
    else
    {
       var result = parent.CompareTo(current.Value);
      // parent value greater than current value
      if(result > 0)
      {
        parent.Left = leftMost;
      }
      // parent value less than current value
      else
      {
        parent.Right = leftMost;
      }
    }
  }
}
```

# Compare SortedLinkedList to BinaryTree

- Insert 25.000 items
  - SortedLinkedList : took 32 seconds to complete
  - BinaryTree : tool o seconds to complete

# AVL Tree (Self Balancing Tree)

- A self-balancing binary search tree. Named after it’s inventors Georgy Adelson-Velsky and Evgenii Landis
- The tree is balanced as nodes are added or removed from the tree.

```csharp
class AVLTreeNode<TNode>{
  AVLTreeNode<TNode> Left;
  AVLTreeNode<TNode> Right;
  TNode Value;

  public int LeftHeight{
    get {
      return GetMaxHeight(Left);
    }
  }

  public int RightHeight{
    get {
      return GetMaxHeight(Right);
    }
  }

  public int BalanceFactor {
    get {
      return RightHeight - LeftHeight;
    }
  }

  //       5
  //    4     6
  //  3   5      7
  // 2             8
  //1
  public int GetMaxHeight(AVLTreeNode<TNode> node) {
    if(node == null)
    {
      return 0;
    }
    return 1 + Math.Max(GetMaxHeight(node.Left), GetMaxHeight(node.Right));
  }

  public TreeState State {
    get {

      if (RightHeight - LeftHeight > 1)
      {
        return TreeState.RightHeavy;
      }
      if (LeftHeight - RightHeight > 1)
      {
        return TreeState.LeftHeavy;
      }
      return TreeState.Balanced;
    }
  }

  void Balance(){

    if(State.RightHeavy)
    {
        if(Right!= null && Right.BalanceFactor <0 )
        {
          LeftRightRotation();
        }
        else{
          LeftRotation();
        }
    }

    if(State.LeftHeavy)
    {
      if(Left != null && Left.BalanceFactor > 0)
      {
        RightLeftRotation();
      }
      else
      {
        RightRotation();
      }
    }    
  }

  enum TreeState{
    Balanced,
    RightHeavy,
    LeftHeavy
  }

}

```

## Left rotation

- Algorithm to balance a right-heavy tree by rotating nodes to the left.
- Steps:
  - Right child becomes the new root
  - Left child of the new root is assigned to right child of the old root
  - Previous root becomes the new root’s left child

```
      1
        3
      2   4
1. Right child becomes the new root:
  1      3
       2   4
2. Left child of the new root is assigned to right child of the old root:
    1        3
      2        4
3. Previous root becomes the new root’s left child:
    3
  1    4
    2
```

```csharp
//			5
//		3		   7
//  2   4   6  8
//					    9
//					     10

void LeftRotation() {

  var newRoot = root.Right;
  root.right = newRoot.left;

  newRoot.left = root;
}
```

## Right rotation
- Algorithm to balance a left-heavy tree by rotating nodes to the right
- Steps:
  - 1 Left child becomes the new root
  - 2 Right child of the new root is assigned to left child of the old root
  - 3 Previous root becomes the new root’s right child
```
      4
    2
  1   3

  ->

      2
    1    4
       3
    
```
```csharp
void RightRotation(){
  var oldRoot = Left;
  var newRoot = ReplaceRoot(Left);
  oldRoot.Left = newRoot.Right;
  newRoot.Right = oldRoot;
}
```
## Left-right rotation
- Right rotation the right child
- Left rotation the root
```csharp
void LeftRightRotation(){
  RightRotation(Right)

}
```
## Right-left rotation
- Left rotate the left child
- Right rotate the root
```csharp
void RightLeftRotation(){

}
```
