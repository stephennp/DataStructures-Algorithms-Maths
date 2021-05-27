# Intro
- Spanning tree algorithms seek to find the shortest way to cover all nodes
- Such algorithms are used when start and end nodes do not matter Prim’s algorithm works for connected graphs
- Kruskal’s algorithm works even for ldisconnected graphs
# What is a Spanning Tree?
- Given an `undirected and connected graph` , a spanning tree of the graph G = (V,E) is a tree that spans G (that is, it includes every vertex of G) and is a subgraph of  G (every edge in the tree belongs to )


# What is a Minimum Spanning Tree?
- Spanning tree with the lowest weight
- The cost of the spanning tree is the sum of the weights of all the edges in the tree. There can be many spanning trees. Minimum spanning tree is the spanning tree where the cost is minimum among all the spanning trees. There also can be many minimum spanning trees.

- Minimum spanning tree has direct application in the design of networks. It is used in algorithms approximating `the travelling salesman problem`, `multi-terminal minimum cut problem` and `minimum-cost weighted perfect matching`. Other practical applications are:
  - Cluster Analysis
  - Handwriting recognition
  - Image segmentation

# Prim's Algorithm
- Works with connected graphs
- Prim’s algorithm is a `greedy` algorithm to find a minimal spanning tree for a weighted undirected graph
- Implementation heavily drawn from Dijkstra’s algorithm
- Distance table, but with edge weight as the distance
- Requires `priority queue` to find edge with least cost
- Steps:
  - Start anywhere, pick a node at random
  - Find the lowest weight edge out of that node
  - Lowest weighted edge connecting an unvisited node
  - Add that edge to the result
  - Now find the lowest weight edge out of either node
  - Lowest weighted edge connecting an unvisited node
  - Add that edge to result as well
  - Once again, find lowest weight edge out of result set
  - All vertices in spanning  tree, stop  Minimum spanning tree found

- `Benefit`: Intermediate result is a tree as well
- `Drawback`: Does not work for disconnected graphs

## Complexity
- Binary Heap : O(E ln(V) )
- Array : O(E+V^2)


# Kruskal's Algorithm
- Works even with disconnected graphs