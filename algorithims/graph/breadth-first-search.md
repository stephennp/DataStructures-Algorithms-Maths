# Intro

- There are many ways to traverse graphs. BFS is the most commonly used approach.

- BFS is a traversing algorithm where you should start traversing from a selected node (source or starting node) and traverse the graph layerwise thus exploring the neighbour nodes (nodes which are directly connected to source node). You must then move towards the next-level neighbour nodes.

- As the name BFS suggests, you are required to traverse the graph breadthwise as follows:
  - First move horizontally and visit all the nodes of the current layer
  - Move to the next layer

```
       0      ->  Layer :0
     1 2 3    ->  Layer :1
    4 5 6 7   ->  Layer :2
```

- The distance between the nodes in layer 1 is comparitively lesser than the distance between the nodes in layer 2. Therefore, in BFS, you must traverse all the nodes in layer 1 before you move to the nodes in layer 2.

# Traversing child nodes

- A graph can contain `cycles`, which may bring you to the same node again while traversing the graph. To avoid processing of same node again, use `a boolean array` which marks the node after it is processed. While visiting the nodes in the layer of a graph, store them in a manner such that you can traverse the corresponding child nodes in a similar order.

- In the earlier diagram, start traversing from 0 and visit its child nodes 1, 2, and 3. Store them in the order in which they are visited. This will allow you to visit the child nodes of 1 first (i.e. 4 and 5), then of 2 (i.e. 6 and 7), and then of 3 (i.e. 7) etc.

- To make this process easy, use a `queue` to store the node and mark it as `visited` until all its neighbours (vertices that are directly connected to it) are marked. The queue follows the `First In First Out (FIFO)` queuing method, and therefore, the neigbors of the node will be visited in the order in which they were inserted in the node i.e. the node that was inserted first will be visited first, and so on.

```C++
BFS (G, s)   //Where G is the graph and s is the source node
      let Q be queue.
      Q.enqueue( s ) //Inserting s in queue until all its neighbour vertices are marked.

      mark s as visited.
      while ( Q is not empty)
           //Removing that vertex from queue,whose neighbour will be visited now
           v  =  Q.dequeue( )

          //processing all the neighbours of v
          for all neighbours w of v in Graph G
               if w is not visited
                        Q.enqueue( w )             //Stores w in Q to further visit its neighbour
                        mark w as visited.

```

# Implementation

```python
from collections import defaultdict
import time

class Graph:

    def __init__(self, size):
        self.graph = defaultdict(list)
        self.vertexSize = size

    def addEdge(self, u, v):
        self.graph[u].append(v)

    def BFS(self, source):
       # length = vertex size
        visited = [False] * self.vertexSize
        level = [0] * self.vertexSize
        queue = []
        queue.append(source)
        visited[source] = True
        level[source] = 0
        while queue:
            q = queue.pop(0)

            print(q)
            # get all neightbours of this vertex
            for v in self.graph[q]:
                if(visited[v] == False):
                    level[v] = level[q] + 1
                    queue.append(v)
                    visited[v] = True

        time.sleep(1)


# 7 vertexes = [0, 1, 2, 3, 4]
#      0
#    3   1
#   4     2
graph = Graph(5)

graph.addEdge(0, 3)
graph.addEdge(0, 1)
graph.addEdge(3, 0)
graph.addEdge(3, 4)
graph.addEdge(1, 2)

graph.BFS(0)

time.sleep(10)

```

# Find shortest path

- This type of BFS is used to find the shortest distance between `two nodes` in a graph provided that the edges in the graph have the weights `0 or 1`. If you apply the BFS explained earlier in this article, you will get an incorrect result for the optimal distance between 2 nodes.

- In this approach, a boolean array is not used to mark the node because the condition of the optimal distance will be checked when you visit each node. `A double-ended queue is used to store the node`. In 0-1 BFS, if the weight of the edge = 0, then the node is pushed to the front of the dequeue. If the weight of the edge = 1, then the node is pushed to the back of the dequeue.

## Implementation

Here, edges[ v ] [ i ] is an adjacency list that exists in the form of pairs i.e. edges[ v ][ i ].first will contain the node to which v is connected and edges[ v ][ i ].second will contain the distance between v and edges[ v ][ i ].first.

Q is a double-ended queue. The distance is an array where, distance[ v ] will contain the distance from the start node to v node. Initially the distance defined from the source node to each node is infinity.

# 0-1 BFS (Shortest Path in a Binary Weight Graph)

- Find the shortest path from source vertex to every other vertex.

  ![Drag Racing](binary-Graph.png)

```
Output : Shortest distances from given source
         0 0 1 1 2 1 2 1 2

Explanation :
Shortest distance from 0 to 0 is 0
Shortest distance from 0 to 1 is 0
Shortest distance from 0 to 2 is 1
```

- In normal BFS of a graph all edges have `equal weight` but in `0-1 BFS some edges may have 0 weight and some may have 1 weight`.
- In this we will not use bool array to mark visited nodes but at each step we will check for the optimal distance condition. We use double ended queue to store the node. While performing BFS if a edge having weight = 0 is found node is pushed at front of double ended queue and if a edge having weight = 1 is found, it is pushed at back of double ended queue.

```python
# shortest path for a Binary Graph
from sys import maxsize as INT_MAX
from collections import deque

# no.of vertices
V = 9

# a structure to represent edges
class node:
    def __init__(self, to, weight):

        # two variable one denote the node
        # and other the weight
        self.to = to
        self.weight = weight

# vector to store edges
edges = [0] * V
for i in range(V):
    edges[i] = []

# Prints shortest distance from
# given source to every other vertex
def zeroOneBFS(src: int):

    # Initialize distances from given source
    dist = [0] * V
    for i in range(V):
        dist[i] = INT_MAX

    # double ende queue to do BFS.
    Q = deque()
    dist[src] = 0
    Q.append(src)

    while Q:
        v = Q[0]
        Q.popleft()

        for i in range(len(edges[v])):

            # checking for the optimal distance
            if (dist[edges[v][i].to] >
                dist[v] + edges[v][i].weight):
                dist[edges[v][i].to] = dist[v] + edges[v][i].weight

                # Put 0 weight edges to front and 1 weight
                # edges to back so that vertices are processed
                # in increasing order of weights.
                if edges[v][i].weight == 0:
                    Q.appendleft(edges[v][i].to)
                else:
                    Q.append(edges[v][i].to)

    # printing the shortest distances
    for i in range(V):
        print(dist[i], end = " ")
    print()

def addEdge(u: int, v: int, wt: int):
    edges[u].append(node(v, wt))
    # edges[u].append(node(v, wt))

# Driver Code
if __name__ == "__main__":

    addEdge(0, 1, 0)
    addEdge(0, 7, 1)
    addEdge(1, 7, 1)
    addEdge(1, 2, 1)
    addEdge(2, 3, 0)
    addEdge(2, 5, 0)
    addEdge(2, 8, 1)
    addEdge(3, 4, 1)
    addEdge(3, 5, 1)
    addEdge(4, 5, 1)
    addEdge(5, 6, 1)
    addEdge(6, 7, 1)
    addEdge(7, 8, 1)

    # source node
    src = 0
    zeroOneBFS(src)
```
