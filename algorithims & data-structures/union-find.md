# Union find (Disjoint data structure)
- The efficiency of an algorithm sometimes depends on the data structure that is used. An efficient data structure, like the disjoint-set-union, can reduce the execution time of an algorithm.

- Assume that you have a set of N elements that are into further subsets and you have to track the connectivity of each element in a specific subset or connectivity of subsets with each other. You can use the `union-find algorithm (disjoint set union)` to achieve this.

- Let’s say there are 5 people `A, B, C, D, and E`. `A is B's` friend, `B is C's` friend, and `D is E's` friend, therefore, the following is true:
  - `A, B, and C` are connected to each other
  - `D and E` are connected to each other

- You can use the union-find data structure to check each friend is connected to the other directly or indirectly. You can also determine the two different disconnected subsets. Here, 2 different subsets are `{A, B, C}` and `{D, E}`.

- You have to perform two operations:
  - Union(A, B): Connect two elements A and B
  - Find(A, B): Find whether the two elements A and B are connected

# Example
- You have a set of elements S = `{0, 1, 2, 3, 4, 5, 6, 7, 8, 9}`. Here there are 10 elements (N = 10). Use an array arr to manage the connectivity of the elements. Arr[ ] that is indexed by elements of sets, which are of size N (as N elements in set), can be used to manage the operations of union and find.
# Dynamic connectivity

Given a set of N objects.

- Union command: connect two objects.
- Find/connected query: is there a path connecting the two objects?
# Examples
- You have a set of elements S = `{0, 1, 2, 3, 4, 5, 6, 7, 8, 9}`. Here there are 10 elements (N = 10). Use an array arr to manage the connectivity of the elements. Arr[ ] that is indexed by elements of sets, which are of size N (as N elements in set), can be used to manage the operations of union and find.
## Assumption 
- A and B objects are connected only if arr[ A ] = arr[ B ].

```
  union(4, 3)
  union(3, 8)
  union(6, 5)
  union(9, 4)
  union(2, 1)
  connected(0, 7) -> wrong
  connected(8, 9) -> true
  union(5, 0)
  union(7, 2)
  connected(0, 7) -> true
```

- Applications involve manipulating objects of all types.
  - Pixels in a digital photo.
  - Computers in a network.
  - Friends in a social network.
  - Transistors in a computer chip.
  - Elements in a mathematical set.
  - Variable names in Fortran program.
  - Metallic sites in a composite system.

- We assume "is connected to" is an equivalence relation:
  - Reflexive: p is connected to p.
  - Symmetric: if p is connected to q, then q is connected to p.
  - Transitive: if p is connected to q and q is connected to r, then p is connected to r.