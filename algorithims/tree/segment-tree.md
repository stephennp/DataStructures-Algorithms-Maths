# Intro

- Segment Tree is a basically a binary tree used for storing the intervals or segments. Each node in the Segment Tree represents an interval. Consider an array `A` of size `N` and a corresponding Segment Tree `T`:
    - The root of `T` will represent the whole array `A[0: N - 1]`
    - Each leaf in the Segment Tree `T`  will represent a single element `A[i]` such that `0 <= i <N`.
    - The internal nodes in the Segment Tree  `T` represents the union of elementary intervals `A[i:j` where `0 <= i < j < N`.

- The root of the Segment Tree represents the whole array `A[0: N - 1]`. Then it is broken down into two half intervals or segments and the two children of the root in turn represent the `A[0: (N - 1)/2]`  and `A[(N - 1)/2] +1 : N-1` . So in each step, the segment is divided into half and the two children represent those two halves. So the height of the segment tree will be `log2N`. There are  `N` leaves representing the `N`  elements of the array. The number of internal nodes is `N-1`. So, a total number of nodes are `2xN -1`.

- Once the Segment Tree is built, its structure cannot be changed. We can update the values of nodes but we cannot change its structure. Segment tree provides two operations:

  - `Update`: To update the element of the array  `A` and reflect the corresponding change in the Segment tree.
  - `Query`: In this operation we can query on an interval or segment and return the answer to the problem (say minimum/maximum/summation in the particular segment).
- Segment tree represented as linear array
```
Arr= [1,3,5,7,9,11]
=> 

                                        A[0:5](36) node = 0
                 A[0:2](9) node =1                                 A[3:5](27) node=2
        A[0:1](4) node=3         A[2:2](5) node=4           A[3:4](16) node=5         A[(5:5](11) node =6
A[0:0](1) node=7 A[1:1](3) node=8               A[3:3](7) node =11 A[4:4](9) node =12

tree[0] = A[0:5]
tree[1] = A[0:2]
tree[2] = A[3:5]
tree[3] = A[0:1]
tree[4] = A[2:2]
tree[5] = A[3:4]
tree[6] = A[5:5]
tree[7] = A[0:0]
tree[8] = A[1:1]
tree[9] = A[3:3]
tree[10] = A[4:4]
tree[11] = A[5:5]
```

# Psude code

```csharp

// Complexity: O(n)
void build(int currentIndex, int start, int end)
{
   if(start == end)
   {
       tree[currentIndex] = A[start];
   }
}

// Complexity: O(logN)
void update(int node, int start, int end, int idx, int val)
{
   
}
```
# Query
- Range represented by a node is completely inside the given range
- Range represented by a node is completely outside the given range
- Range represented by a node is partially inside and partially outside the given range

```csharp
// Complexity: O(logN)
// L <----> R                     L <----> R
//              Start <-------->  End
//              L     <-------->  R
// left, right: we want to sum with the range
// query(0, 1,3, 0, N-1)
int query(int node, int left,int right, int start, int end)
{
  // If segment of this node is
  // outside the given range
  if(r < start or end < l)
  {
    return 0
  }

  // If segment of this node is a part
  // of given range, then return
  // the sum of the segment
  if(l <= start and end <= r)
  {
    return tree[node];
  }

  // range represented by a node is completely inside the given range
  var mid = (start+end) / 2;
  int p1 = query(node * 2 + 1, left, right, start,mid);
  int p2= query(node * 2 + 2, left, right, mid, end);
  return p1+p2;
}
```


# Applications
- Sum of all elements in array from indices L to R
- Finding the minimum of all the elements in array from indices L to R


