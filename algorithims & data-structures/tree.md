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

## Complexity

- `O(h)` (e.g., search, max, min, insert, delete.. etc) time where h is the `height of the BST`

```csharp
class AVLTreeNode<TNode>{
  AVLTreeNode<TNode> Left;
  AVLTreeNode<TNode> Right;
  TNode Value;
  AVLTree<TNode> Tree;
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

  void ReplaceRoot(AVLTreeNode<TNode> newRoot)
  {
    // checking the node that rotate is substree
    if(this.parent != null)
    {
        if(this.parent.Left = this)
        {
          this.parent.Left = this;
        }
        else if(this.parent.Right = this)
        {
          this.parent.Right = this;
        }
    }
    else
    {
      Tree.Head = newRoot;
    }

    // Update the parent for new root;
    newRoot.parent = this.parent;

    // update new parent for old root
    this.parent =  newRoot;
  }

  enum TreeState{
    Balanced,
    RightHeavy,
    LeftHeavy
  }

}

class AVLTree<TNode>
{
  void InOrderTraversal(){
      if(Head != null)
      {
        var stack = new Stack<AVLTreeNode<T>>();
        var current = head;

        bool goLeftNext =false;
        stack.push(current);

        while(stack.Count >0)
        {
          if(goLeftNext)
          {
            while(current.Left != null)
            {
              stack.push(current.Left);
              current = current.Left;
            }
          }
          // in-order is left->yield->right
          yield return current.Value;

          if(current.Right != null)
          {
            current= current.Right;
            goLeftNext = true;
          }
          else
          {
            current = stack.Pop();
            goLeftNext = false;
          }
        }
      }
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

  var newRoot = Right;

 // replace new root, old root as well
  ReplaceRoot(newRoot);

  Right = newRoot.Left;

  newRoot.Left = this;
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
  var newRoot = Left;
  ReplaceRoot(newRoot);

  // update old root left  child
  Left = newRoot.Right;

  // update new root right with new value of old root
  newRoot.Right = this;
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

# B-Tree

- A sorted, balanced, tree structure typically used to access data on slow mediums such as disk or tape drives.
- The B-tree is well suited for storage systems that `read and write relatively large blocks of data`, such as disks `commonly used in databases and file systems`.
- Nodes will always have one more child than values

## why use B tree:

- Reduces the number of reads made on the disk
- B Trees can be easily optimized to adjust its size (that is the number of child nodes) according to the disk size
- It is a specially designed technique for handling a bulky amount of data.
- It is a useful algorithm for databases and file systems.
- A good choice to opt when it comes to reading and writing large blocks of data
- Disk access time is very high compared to the main memory access time. The main idea of using B-Trees is to reduce the number of disk accesses. Most of the tree operations (search, insert, delete, max, min, ..etc ) require O(h) disk accesses where h is the height of the tree. B-tree is a `fat tree`. The h`eight of B-Trees is kept low by putting maximum possible keys in a B-Tree node`.
- Generally, the B-Tree node size is kept equal to the disk block size. Since the height of the B-tree is low so total disk accesses for most of the operations are `reduced significantly` compared to balanced Binary Search Trees like AVL Tree, Red-Black Tree, ..etc.

## Complexity

          Average	      Worst case

Space O(n) O(n)
Search O(log n) O(log n)
Insert O(log n) O(log n)
Delete O(log n) O(log n)

## History of B Tree
- Data is stored on the disk in blocks, this data, when brought into main memory (or RAM) is called data structure.
- In-case of huge data, searching one record in the disk requires reading the entire disk; this increases time and main memory consumption due to high disk access frequency and data size.
- To overcome this, index tables are created that saves the record reference of the records based on the blocks they reside in. This drastically reduces the time and memory consumption.
- Since we have huge data, we can create multi-level index tables.
Multi-level index can be designed by using B Tree for keeping the data sorted in a self-balancing fashion.
## Minimal Degree

- The minimum number of children that every non-root node must have. Represented as the variable `T`:
  - `T` - Each non-root must contain at least T (minimal degree) children
  - `2T` - Each node in the B-tree will contain a maximum of `2*T` children
  - `T-1` - Every non-root node will have at least T-1 values
  - `2T-1` - Every node will have at most `2*T-1` values
  - Every node, except root, must contain minimum nodes of `[T/2]-1`

## Minimal Node

- A non-root node that has T-1 values and T children.

## Full Node

- A node that has 2*T-1 values and 2*T children.

## Examples

- Valid:

  ```
  T = 3

       3        6          10
      1 2   4 5  7 8 9   11 12
  ```

- Invalid

  ```
  T = 3

       3       6          10
      1    4 5  7 8 9   11 12

       3       6          10
      1 2     4 5    7 8 9 10 11 12
  ```

## Height

- The number of edges between the root and the leaf nodes. All B-tree leaf nodes must have the same height.
- Valid:

  ```
  T = 3

       3        6          10
                                  -> 1
      1 2   4 5  7 8 9   11 12
  ```

- Invalid

  ```
  T = 3

          3            6      15
                                    -> 1
      1 2   4 5   7 10 14   16 17
                                    -> 2
                89 11 12 13

    
  ```


## Searching  
```
          3        6          10
          1 2   4 5  7 8 9   11 12
Smaller <-                      -> Larger
```

```pseudo
bool search(node, valueToFind)
  foreach value in node
    if valueToFind == value
      return true
    if valueToFind < value
      return search(<left child>, valueToFind)
end
  return search(<last child>, valueToFind)
end
```

## Removing Values
- Values can only be removed from leaf nodes
- Ensure that all nodes visited during the remove process have T values
before entering them
## Balancing Operations
### Node Splitting
- Splitting a child value in half by pulling the middle value up to the parent
- Used when adding a node and the destination node would have too many
values
### Pushing Down
- Merging two child nodes by pushing a parent value between them
- Push Down Minimal Root:
  - When the root has a single value and two minimal children, they can be combined with it to form a full root node.
- Used when removing a value would leave a child node with too few values, the
parent has multiple values, and the sum of the adjacent child and the current
child is less than 2*T-1.
## Rotation
- Rotating a value from a non-minimal child, to a sibling minimal child
- Used when removing a node and pushing down would not work because the
parent has too few values, but a sibling has a value to spare.
## Code
```csharp
// root = 1 2 3 4 5

// root = 3

// children = [1,2] [4,5,6]

// 			[3]
// 		[1,2] [4,5,6]
		
// 		 [3]
//  => [1,2] [4,5,6,7,8]
 
//  root = [3,6]
//  children = [1,2] [4,5] [7,8,9]
 
// 				[3, 6, 9, 12, 15]
// 	=>	[1,2] [4,5] [7,8] [10, 11] [13,14] [16,17,18]
			
// 						    [9]
// 					    [3, 6]              [12, 15]
// 	=>	[1,2] [4,5] [7,8]   [10, 11] [13,14] [16,17,18]

// root = [9]
// children 1 = [3,6] , values = [1,2] [4,5] [7,8]
// children 2 = [9,12,15] , values = [10, 11] [13,14] [16,17,18]

class BTreeNode<T> where T : Comparable<T>{
  List<T> Values;
  BTreeNode<T> Children;
  int MinDegree;
  public BTreeNode(int minDegree, List<T> values, BTreeNode<T> children)
  {
    MinDegree = minDegree;
    Values = values;
    Children = children;
    Validate();
  }
  bool Leaf
  {
    get{
    return Children.Count ==0;
    }
  }
  bool Minimum {
    get{
      return  Values.Count == MinDegree - 1;
    }
  }
  bool Full{
    get {
      return Values.Count >= 2*MinDegree - 1;
    }
  }

  bool Count{
    get{
      return Values.Count;
    }
  }

  void Validation(){
    if(Count === 0)
    {
      throw new Exception("Every node must have at least one value.");

    }
    if(Children > 0)
    {
      if(Values.Count > Children.Count -1)
      {
        throw new Exception("Values must be be one less than children");
      }
    }
    if(Values.Count >= MinDegree * 2 +1)
    {
      throw new Exception("the number of values exceeds the degree limit.");
    }
  }
}
class BTree<T>{
  BTreeNode<T> Root {get;set;}
  int MinDegree = 7;
  // The number of items in the tree
 public int Count
  {
   get;
  private set;
  }

  // The current height of the tree
  // Grows in SplitRootNode, shrinks in PushDownMinimalRoot
 public int Height
  {
     get;
    private set;
   }


  public BTree(int minDegree)
  {
    MinDegree = minDegree;
  }

  int FindChildIndex(BTreeNode<T> node, T value)
  {
    var index = node.Values.BinarySearch(value);
    if(index < 0)
    {
      index = ~index;
    }
    return index;
  } 

  void Add(){
    if(Root != null)
    {
      Root = new BTreeNode<T>(MinDegree);
    }
    else
    {
      if(Root.Full)
      {
        SplitRootNode(Root);
      }
      InsertNonRoot(Root);
    }
    Count ++;
  }
  void InsertNonRoot(BTreeNode<T> node, T value){
    if(node.Leaf)
    {
      node.Values.Insert(FindChildIndex(node, value), value);
    }
    else
    {
      var childIndex = FindChildIndex(node, value);
      BTreeNode<T> child = node.Children[childIndex];

      if(node.Full)
      {
        SplitChildNode(node, childIndex);

        // re-find the child node where the value would be added
        child = node.Children(FindChildIndex(node,value));
      }

      InsertNonRoot(child,value);
    }
  }
  // [1,2,3,4,5]
  void SplitRootNode(BTreeNode<T> node){
    var midIndex = node/2;
    // [1,2]
    var left = new BTreeNode<T>(MinDegree, node.Values.Take(midIndex), node.Children.Take(midIndex+1));
    // [4,5]
    var right = new BTreeNode<T>(MinDegree, node.Values.TakeLast(midIndex), node.Children.TakeLast(midIndex+1));

    // remove [1,2] and [4,5]
    node.Values.RemoveRange(0, midIndex);
    node.Values.RemoveRange(1, midIndex);

    // clear all the root node children
    // (the left and right nodes have those children)
    node.Chidlren.Clear();

    node.Children.Insert(left);
    node.Children.Insert(right);

    node.Validate();
    Height ++;
  }
          /*
         * Splits a child node by pulling the middle node up from it
         * into the current (parent) node.
         * 
         *       [3          9]
         *  [1 2] [4 5 6 7 8] [10 11] 
         *  
         *  splitting [4 5 6 7 8] would pull 6 up to its parent
         *  
         *      [3     6     9]
         *  [1 2] [4 5] [7 8] [10 11] 
         */
  void SplitChildNode(BTreeNode<T> parent, int childIndex)
  {
      // [4, 5, 6, 7, 8]
      var child = parent.Children[childIndex];

      // 6
      var midIndex = child.Value.Count / 2

      // [4, 5]
      var left = new BTreeNode<T>(MinDegree, child.Value.Take(midIndex), child.Children.Take(midIndex+1));
      // [7, 8]
      var right = new BTreeNode<T>(MinDegree, child.Value.TakeLast(midIndex), child.Children.TakeLast(midIndex+1));

      // [3, 6, 9]
      parent.Value.Insert(childIndex, child.Value[midIndex]);

      // remove [4 5 6 7 8]
      parent.Children.RemoveAt(childIndex);

      // add the child point to [4, 5] and [7, 8]
      // add right first to maintain ordering
      parent.Children.Insert(midIndex,right);
      parent.Children.Insert(midIndex,left);

      parent.Validate();
      left.Validate();
      right.Validate();
  }

  void Remove(T value)
  {    
    var removed = RemoveNode(Root, value);
    if(removed)
    {
      Count --;

      if(Count ==0 )
      {
        Root = null;
      }
    }
    return removed;

  }

bool RemoveNode(BTreeNode<T> node, T value) {

    if(node.Leaf)
    {
      return RemoveLeaf(node, value);
    }
    
    if(node.Values.Contains(value))
    {
      return RemoveNode(PushDown(node,value), value);
    }
  }

   bool RemoveLeaf(BTreeNode<T> node, T value)
   {
     return node.Values.Remove(value);
   }


  //    [3 , 6]
  // [1,2] [4,5] [7,8]
  void PushDown(BTreeNode<T> node, T value){
    var childIndex = FindChildIndex(node,value);
    var left= node.Children[childIndex];
    var right = node.Children[childIndex + 1]

    left.Value.Add(value);
    left.Value.AddRange(Right.Values);
    left.Children.AddRange(Right.Children);

    // remove the value from the parent: 6
    node.Values.RemoveAt(childIndex);
    // remove right childrens
    node.Children.RemoveAt(childIndex + 1);

    node.Validate();
    left.Validate();
    return left;
  }
}
```