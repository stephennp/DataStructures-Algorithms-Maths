# Intro

- Spanning tree algorithms seek to find the `shortest way to cover all nodes`
- Such algorithms are used when start and end nodes do not matter Prim’s algorithm works for connected graphs
- Kruskal’s algorithm works even for disconnected graphs

# What is a Spanning Tree?

- Given an `undirected and connected graph` , a spanning tree of the graph G = (V,E) is a tree that spans G (that is, it includes every vertex of G) and is a subgraph of G (every edge in the tree belongs to )

# What is a Minimum Spanning Tree?

- Spanning tree with the lowest weight
- The cost of the spanning tree is the sum of the weights of all the edges in the tree. There can be many spanning trees. Minimum spanning tree is the spanning tree where the cost is minimum among all the spanning trees. There also can be many minimum spanning trees.

- Minimum spanning tree has direct application in the design of networks. It is used in algorithms approximating `the travelling salesman problem`, `multi-terminal minimum cut problem` and `minimum-cost weighted perfect matching`. Other practical applications are:
  - Cluster Analysis
  - Handwriting recognition
  - Image segmentation

# Prim's Algorithm

- using BFS algorithmz
- Works with connected graphs
- Prim’s algorithm is a `greedy` algorithm to find a minimal spanning tree for a weighted undirected graph
- Implementation heavily drawn from Dijkstra’s algorithm
- Distance table, but with edge weight as the distance
- Requires `priority queue` to find edge with least cost
- Steps:
  - Create matrix graph
  - Start random a node
  - Remember use a distance table to compare last vertex
  - Use queue to contain nodes
  - Create a spanning tree table
  - Remember create a visited nodes
- Details:

  - Start anywhere, pick a node at random
  - Find the lowest weight edge out of that node
  - Lowest weighted edge connecting an unvisited node
  - Add that edge to the result
  - Now find the lowest weight edge out of either node
  - Lowest weighted edge connecting an unvisited node
  - Add that edge to result as well
  - Once again, find lowest weight edge out of result set
  - All vertices in spanning tree, stop Minimum spanning tree found

- `Benefit`: Intermediate result is a tree as well
- `Drawback`: Does not work for disconnected graphs

## Complexity
- O((V+E)logV)
- Binary Heap : O(E ln(V) )
- Array : O(E+V^2)

## Implementation

```python
import priority_dict

from graph import *

def spanning_tree(graph, source):
	# A dictionary mapping from the vertex number to a tuple of
	# (distance from source, last vertex on path from source)
	distance_table = {}

	for i in range(graph.numVertices):
		distance_table[i] = (None, None)

	# The distance to the source from itself is 0
	distance_table[source] = (0, source)

	# Holds mapping of vertex id to distance from source
	# Access the highest priority (lowest distance) item
	# first 
	priority_queue = priority_dict.priority_dict()
	priority_queue[source] = 0

	visited_vertices = set()

	# Set of edges where each edge is represented as a string
	# "1->2": is an edge between vertices 1 and 2 
	spanning_tree = set()

	while len(priority_queue.keys()) > 0:
		current_vertex = priority_queue.pop_smallest()

		# If we've visited a vertex earlier then we have all
		# outbound edges from it, we do not process it again
		if current_vertex in visited_vertices:
			continue

		visited_vertices.add(current_vertex)

		# If the current vertex is the source, we haven't traversed an
		# edge yet, no edge to add to our spanning tree
		if current_vertex != source:	
			# The current vertex is connected by the lowest weighted edge
			last_vertex = distance_table[current_vertex][1]	

			edge = str(last_vertex) + "-->" + str(current_vertex)
			if edge not in spanning_tree:
				spanning_tree.add(edge)		

		for neighbor in graph.get_adjacent_vertices(current_vertex):
			# The distance to the neighbor is only the weight of the edge
			# connecting the neighbor
			distance = g.get_edge_weight(current_vertex, neighbor)

			# The last recorded distance of this neighbor
			neighbor_distance = distance_table[neighbor][0]

			# If this neigbor has been seen for the first time or the new edge
			# connecting this neighbor is of a lower weight than the last
			if  neighbor_distance is None or neighbor_distance > distance:
				distance_table[neighbor] = (distance, current_vertex)

				priority_queue[neighbor] = distance


	for edge in spanning_tree:
		print(edge)			



"""
      2
  3 ----- 2 
  |       | \ -> 2 
3 |     5 |   4
  |       | / -> 6
  1 ----- 0  
      6
       
"""
g = AdjacencyMatrixGraph(5, directed=False)
g.add_edge(0, 4, 6)
g.add_edge(0, 2, 5)
g.add_edge(4, 2, 2)
g.add_edge(2, 3, 2)
g.add_edge(3, 1, 3)
g.add_edge(1, 0, 6)

# spanning_tree(g, 1)

spanning_tree(g, 4)

```

# Kruskal's Algorithm

- Kruskal’s algorithm is a greedy algorithm to find a minimal spanning tree for a weighted undirected graph
- Works even with disconnected graphs
- Steps:
  - Sort edges
    - Increasing order of weights
    - Can use priority queue
  - Find shortest edge
    - Not currently in result
    - Dequeue from priority queue
  - Stop
    - When N-1 edges in result
    - N = number of vertices in graphe
  - Initialize empty result
    - Empty set of edges
    - At end will hold minimum spanning tree
  - Reject if cycle introduced
    - Else add to result set
    - This is a greedy step
- `Benefit`: Works for disconnected graphs too
- `Drawback`: Intermediate result is not necessarily a tree
## Complexity
- O(ELogV)
- Sort edge : O(E ln(E))

## Implemntation

```python
import priority_dict

from graph import *

def spanning_tree(graph):

	# Holds a mapping from a pair of edges to the edge weight
	# The edge weight is the priority of the edge
	priority_queue = priority_dict.priority_dict()

	for v in range(graph.numVertices):
		for neighbor in graph.get_adjacent_vertices(v):
			priority_queue[(v, neighbor)] = graph.get_edge_weight(v, neighbor)

	visited_vertices = set()

	# Maps a node to all its adjacent nodes which are in the
	# minimum spanning tree
	spanning_tree = {}
	for v in range(graph.numVertices):
		spanning_tree[v] = set()

	# Number of edges we have got so far
	num_edges = 0

	while len(priority_queue.keys()) > 0 and num_edges < graph.numVertices - 1:
		v1, v2 = priority_queue.pop_smallest()

		if v1 in spanning_tree[v2]:
			continue


		# Arrange the spanning tree so the node with the smaller
		# vertex id is always first. This greatly simplifies the
		# code to find cycles in this tree
		vertex_pair = sorted([v1, v2])
		spanning_tree[vertex_pair[0]].add(vertex_pair[1])

		# Check if adding the current edge causes a cycle
		if has_cycle(spanning_tree):
			spanning_tree[vertex_pair[0]].remove(vertex_pair[1])
			continue

		num_edges = num_edges + 1

		visited_vertices.add(v1)
		visited_vertices.add(v2)

	print("Visited vertices: ", visited_vertices)

	if len(visited_vertices) != graph.numVertices:
		print("Minimum spanning tree not found")
	else:
		print("Minimum spanning tree:")
		for key in spanning_tree:
			for value in spanning_tree[key]:
				print(key, "-->", value)


def has_cycle(spanning_tree):
	for source in spanning_tree:
		q = []
		q.append(source)

		visited_vertices = set()
		while len(q) > 0:
			vertex = q.pop(0)

			# print("Visit: ", vertex)
			# If we've see the vertex before in this spanning tree
			# there is a cycle
			if vertex in visited_vertices:
				return True
			visited_vertices.add(vertex)

			# Add all vertices connected by edges in this spanning tree
			q.extend(spanning_tree[vertex])

	return False


"""
      5
  3 ----- 2
  |       | \ -> 1
6 |     4 |   4
  |       | / -> 3
  1 ----- 0
      7

"""
g = AdjacencyMatrixGraph(5, directed=False)
g.add_edge(0, 4, 3)
g.add_edge(0, 2, 4)
g.add_edge(4, 2, 1)
g.add_edge(2, 3, 5)
g.add_edge(3, 1, 6)
g.add_edge(1, 0, 7)

spanning_tree(g)
```
