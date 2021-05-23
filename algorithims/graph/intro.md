# Intro

- Graphs are mathematical structures that represent pairwise relationships between objects. A graph is a flow structure that represents the relationship between various objects. It can be visualized by using the following two basic components:

- **Nodes**: These are the most important components in any graph. Nodes are entities whose relationships are expressed using edges. If a graph comprises 2 nodes and and an undirected edge between them, then it expresses a bi-directional relationship between the nodes and edge.

- **Edges**: Edges are the components that are used to represent the relationships between various nodes in a graph. An edge between two nodes expresses a one-way or two-way relationship between the nodes.

# Types of nodes

- **Root node**: The root node is the ancestor of all other nodes in a graph. It does not have any ancestor. Each graph consists of exactly one root node. Generally, you must start traversing a graph from the root node.

- **Leaf nodes**: In a graph, leaf nodes represent the nodes that do not have any successors. These nodes only have ancestor nodes. They can have any number of incoming edges but they will not have any outgoing edges.

# Types of graphs

- Undirected: An undirected graph is a graph in which all the edges are bi-directional i.e. the edges do not point in any specific direction

```
1 --- 2
|     |
|     |
3 --- 4
```

- Directed: A directed graph is a graph in which all the edges are uni-directional i.e. the edges point in a single direction.

```
1 ---> 2
^      ^
|      |
|      |
3 ---> 4

```

# Weighted:

- In a weighted graph, each edge is assigned a weight or cost. Consider a graph of 4 nodes as in the diagram below. As you can see each edge has a weight/cost assigned to it. If you want to go from vertex 1 to vertex 3, you can take one of the following 3 paths:

```
1 -> 2 -> 3
1 -> 3
1 -> 4 -> 3
```

- Therefore the total cost of each path will be as follows: - The total cost of 1 -> 2 -> 3 will be (1 + 2) i.e. 3 units - The total cost of 1 -> 3 will be 1 unit - The total cost of 1 -> 4 -> 3 will be (3 + 2) i.e. 5 units

```
      1
   1 ---- 2
   | \    |
 3 |  \ 1 | 2
   |   \  |
   3 ---- 4
      2

    Weighted graph
```

# Cyclic:

- A graph is `cyclic` if the graph comprises a path that starts from a vertex and ends at the same vertex. That path is called a `cycle`. An `acyclic graph` is a graph that has `no cycle`.

- A tree is an `undirected graph` in which any two vertices are connected by only one path. `A tree is an acyclic graph` and has `N - 1` edges where N is the number of vertices. Each node in a `graph` may have `one or multiple parent nodes`. However, in a `tree`, each node (except the root node) comprises `exactly one parent node`.

- Note: A root node has no parent.

- A tree cannot contain any cycles or self loops, however, the same does not apply to graphs.

# Graph representation

- You can represent a graph in many ways. The two most common ways of representing a graph is as follows:

# Adjacency matrix

- An adjacency matrix is a `VxV` binary matrix `A`. Element A(i,j) is `1` if there is an edge from vertex i to vertex j else A(i,j) is `0`.

- Note: A binary matrix is a matrix in which the cells can have only one of two possible values - either a `0 or 1`.

- The adjacency matrix can also be modified for the weighted graph in which instead of storing 0 or 1 in , the weight or cost of the edge will be stored.

- In an `undirected graph`, if `A(i,j) = 1, then A(j,i)= 1`.
- In a `directed graph`, if `A(i,j) = 1`, then `A(j,i) may or may not be 1`.

- Adjacency matrix provides constant time access `(O(1) )` to determine if there is an edge between two nodes. Space complexity of the adjacency matrix is `O(V^2)`.

- The adjacency matrix of the following graph is:

```
i/j : 1 2 3 4

1 :   0 1 0 1
2 :   1 0 1 0
3 :   0 1 0 1
4 :   1 0 1 0

1 --- 2
|     |
|     |
3 --- 4
```

- The adjacency matrix of the following graph is:

```
i/j:  1 2 3 4
1 :   0 1 0 0
2 :   0 0 0 1
3 :   1 0 0 1
4 :   0 1 0 0

1 ---> 2
↑     ↑ ↓
3 ---> 4
```

# Adjacency list

- Space complexity of adjacency list is `O(V + E)`
- An array of lists is used. The size of the array is equal to the number of vertices. Let the array be an array[]. An entry array[i] represents the list of vertices adjacent to the ith vertex.
- This representation can also be used to represent a weighted graph. The weights of edges can be represented as lists of pairs. Following is the adjacency list representation of the above graph.

```python
"""
A Python program to demonstrate the adjacency
list representation of the graph
"""

# A class to represent the adjacency list of the node
class AdjNode:
    def __init__(self, data):
        self.vertex = data
        self.next = None


# A class to represent a graph. A graph
# is the list of the adjacency lists.
# Size of the array will be the no. of the
# vertices "V"
class Graph:
    def __init__(self, vertices):
        self.V = vertices
        self.graph = [None] * self.V

    # Function to add an edge in an undirected graph
    def add_edge(self, src, dest):
        # Adding the node to the source node
        node = AdjNode(dest)
        node.next = self.graph[src]
        self.graph[src] = node

        # Adding the source node to the destination as
        # it is the undirected graph
        node = AdjNode(src)
        node.next = self.graph[dest]
        self.graph[dest] = node

    # Function to print the graph
    def print_graph(self):
        for i in range(self.V):
            print("Adjacency list of vertex {}\n head".format(i), end="")
            temp = self.graph[i]
            while temp:
                print(" -> {}".format(temp.vertex), end="")
                temp = temp.next
            print(" \n")


# Driver program to the above graph class
if __name__ == "__main__":
    V = 5
    graph = Graph(V)
    graph.add_edge(0, 1)
    graph.add_edge(0, 4)
    graph.add_edge(1, 2)
    graph.add_edge(1, 3)
    graph.add_edge(1, 4)
    graph.add_edge(2, 3)
    graph.add_edge(3, 4)

    graph.print_graph()
```

# Comparing Adjacency matrix, linked-list and set
- Adjacency matrix:
  - Space: O(v^2)
  - Checking if edge is present: O(1)
  - Iterating over edges: O(v)
- Adjacency Linked-list:
  - Space: O(e+v)
  - Checking if edge is present: O(degree v)
  - Iterating over edges: O(degree v)
- Adjacency set:
  - Space: O(e+v)
  - Checking if edge is present: O(Indegree v)
  - Iterating over edges: O(degree v)

# Traversing tree
- One node is designated root
- Only one specific path from root to any node
- No cycles
- Any node will be visited exactly once
- No need to track which nodes already visited
- No unconnected nodes possible
# Traversing graph
- No designated root
- Multiple paths possible between any pair of nodes
- Cycles possible
- Nodes could be visited multiple times (could lead to infinite loop)
- Essential to track which nodes already visited
- Unconnected nodes possible
- `Algorithm can not terminate until all nodes have been visited`

# Summary
- Directed Acyclic Graphs (DAGs) are extremely versatile constructs
- Applications of DAGs include building neural network models
- DAGs specify precedence relationship between nodes
- Any ordering of all nodes that satisfies all relationships is a topological sort
- Topological sort can be implemented via a simple iterative algorithm
# Reference:
- Love this course, very comprehensive :)) https://app.pluralsight.com/library/courses/graph-algorithms-python/table-of-contents