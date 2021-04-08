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
- Initially, all slots of parent array are initialized to `-1` (means there is `only one item` in every subset).
```
index  0   1    2
      -1  -1   -1

```
- Edge `0 -> 1` :  Find the subsets in which vertices `0 and 1` are.
```
index  0   1    2  <----- 1 is made parent of 0 (1 is now representative of subset {0, 1})
       1  -1   -1
```
- Edge `1-2`: 1 is in subset 1 and 2 is in subset 2. So, take union.
```
index  0   1    2  <----- 2 is made parent of 1 (2 is now representative of subset {0, 1,2})
       1   2   -1
```
- Edge `0-2`: : 0 is in subset 2 and 2 is also in subset 2. Hence, including this edge forms a `cycle`.
- How subset of 0 is same as 2?  `0->1->2` // 1 is parent of 0 and 2 is parent of 1  
# Dynamic connectivity
- Given a set of N objects.

- Union command: connect two objects.
- Find/connected query: is there a path connecting the two objects?

# Examples
- You have a set of elements S = `{0, 1, 2, 3, 4, 5, 6, 7, 8, 9}`. Here there are 10 elements (N = 10). Use an array arr to manage the connectivity of the elements. Arr[ ] that is indexed by elements of sets, which are of size N (as N elements in set), can be used to manage the operations of union and find.

# Applications 
  - Pixels in a digital photo.
  - Computers in a network.
  - Friends in a social network.
  - Transistors in a computer chip.
  - Elements in a mathematical set.
  - Variable names in Fortran program.
  - Metallic sites in a composite system.

