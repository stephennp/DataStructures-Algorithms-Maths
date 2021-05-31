# Intro
- Shortest path algorithms are widely used in transportation and scheduling
- Such algorithms focus on the most efficient route between a pair of nodes
- Edge weights determine the cost of a path in such algorithms
- If all edge weights are `equal`, use the unweighted `shortest path algorithm`
- If edge weights are `unequal`, use `Dijkstra’s algorith`

# Applications
- Getting from Point A to Point B
  - Route through less congested roads
  - Multiple deliveries to multiple locations
  - Costly to ford rivers, pass mountains

# Unweighted Graphs
- All edges have equal weights
- Shortest path has smallest number of hops
- Unweighted shortest path algorithm
# Weighted graphs
- Edges have differing weights
- Shortest path has lowest sum of weights along path
- Djisktra’s algorithm

# Shortest path algorithm
- Using this when all edge weights are `equal`
- The shortest path is the path with the least hops
- Steps:
  - Use BFS traversal
  - Create a distance table incluiding( Node, distance and preceding node)
  - Should only add neighbors of edge when they have other adjacent verticles
- Details:
  - Create distance table(Node, Distance, Preceding Node)
    - At outset, all we know is that source node is at distance `0` from itself
    ```
      Node      Distance      Preceding Node
      A            0              A
      B           -1              - 
      C           -1              -
      D           -1              -
      E           -1              -
    ```
  - Create a `queue` hold values from incoming edges of a vertex
  - To trace out the shortest path, using `backtrack` from destination D to source A
    - Use `stack` for last-in, first-out
## So why shortest path shouldn't have a cycle ?
- There is no need to pass a vertex again, because the shortest path to all other vertices could be found without the need for a second visit for any vertices.
## Compexity
- Adjacency matrix: O(V2)
- Adjacency list or set :O(V+E)
## Implementation
```python
from queue import Queue

from graph import *


def build_distance_table(graph, source):
	# A dictionary mapping from the vertex number to a tuple of
	# (distance from source, last vertex on path from source)
	distance_table = {}

	for i in range(graph.numVertices):
		distance_table[i] = (None, None)

	# The distance to the source from itself is 0
	distance_table[source] = (0, source)

	queue = Queue()
	queue.put(source)

	while not queue.empty():
		current_vertex = queue.get()

		# The distance of the current vertex from the source
		current_distance = distance_table[current_vertex][0]
			
		for neighbor in graph.get_adjacent_vertices(current_vertex):
			# Only update the distance table if no current distance from
			# the source is set
			if distance_table[neighbor][0] is None:
				distance_table[neighbor] = (1 + current_distance, current_vertex)

				# Enqueue the neighbor only if it has other adjacent vertices
				# to explore
				if len(graph.get_adjacent_vertices(neighbor)) > 0:
					queue.put(neighbor)

	return distance_table			


def shortest_path(graph, source, destination):
	distance_table = build_distance_table(graph, source)

	path = [destination]

	previous_vertex = distance_table[destination][1]
	while previous_vertex is not None and previous_vertex is not source:
		path = [previous_vertex] + path

		previous_vertex = distance_table[previous_vertex][1]

	if previous_vertex is None:
		print("There is no path from %d to %d" % (source, destination))
	else:
		path = [source] + path
		print("Shortest path is: ", path)


g = AdjacencySetGraph(8, directed=True)
g.add_edge(0, 1)
g.add_edge(1, 2)
g.add_edge(1, 3)
g.add_edge(2, 3)
g.add_edge(1, 4)
g.add_edge(3, 5)
g.add_edge(5, 4)
g.add_edge(3, 6)
g.add_edge(6, 7)
g.add_edge(0, 7)

shortest_path(g, 0, 5)
shortest_path(g, 0, 6)
shortest_path(g, 7, 4)
```

# Djikstra's algorithm
- unweighted Shortest path
  - Enque neighbors: Any order
  - Calculating distance: Number of hops
  - Visited nodes: Don’t update distance to visited nodes
  - Enqueuing visited nodes: Never re-enqueue visited nodes
- Djikstra
  - Enque neighbors: Decreasing order of weight
  - Calculating distance: Sum of weights
  - Visited nodes: Re-calculate distance to visited nodes, update if needed
  - Enqueuing visited nodes: Re-enqueue if distance was updated
# Complexity
- Binary Heap: O(E ln(V) )
- Array: O(E + V2)
## Implementation
- Steps:
  - Create distance tbl 
  - Use `priority queue` to enqueue based on distance -> update value to distance tbl and queue as well