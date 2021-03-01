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