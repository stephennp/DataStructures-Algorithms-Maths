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
