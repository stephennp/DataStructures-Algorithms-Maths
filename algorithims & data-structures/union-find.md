# Dynamic connectivity

Given a set of N objects.

- Union command: connect two objects.
- Find/connected query: is there a path connecting the two objects?
- Examples

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