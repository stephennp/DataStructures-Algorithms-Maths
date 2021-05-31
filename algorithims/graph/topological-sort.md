# Intro

- Complexity: O(V+E)
- A Topological Sort is any ordering of all the DAG’s vertices that satisfies all precedence relationships
- Each edge visited exactly once
- Each vertex visited exactly once
- Multiple solutions possible

# Complexity

- O(V+E)

# Directed Acyclic Graph

- A directed graph with no cycle
- Common applications
  - Scheduling tasks
  - Evaluating expressions
  - Building neural network models
- A graph with cycles will never finish computation

# “Deep Learning” Binary Classifier

- The vertices in the computation graph are neurons (simple building blocks)
- The edges in the computation graph are data items called tensors

# TensorFlow

- TensorFlow is a language for machine learning which is optimized for building neural networks
- Everything is a Graph in TensorFlow

# Come before

```
A → B
      ↘
↓   ↑   D
      ↗
C → E

A -> B,C
E -> B,D
B -> D

```

# Come after

- The `in-degree` of a node is the number of directed edges that directly flow into that node

```
A → B
      ↘
↓   ↑   D
      ↗
C → E
                Degreee ( number of imconing arrows)
A ->                0
B -> A,E            2
C -> A              1
E -> C              1
D -> E ,B           2
```

# Steps
- Start with in-degree `0` then reduce the other incoming edges
- Repeat the step
- Should check cycle graph

- Details
  - Start the topological sort procedure by visiting any node that has `in-degree = 0`
  - If `no` node has in-degree = 0, the graph has a cycle (i.e. it is not a DAG, topological sort not defined)
  - Add A to the result of our topological sort
  - Decrement the in-degree of all nodes that `come after` A
  - Next, visit any node that has in-degree = 0
  - Add C to the result of our topological sort
  - Remove C from our original graph
  - Decrement the in-degree of all nodes that `come after` C
  - ... Rinse-and-Repeat
  - Result: A -> C -> E -> B -> D

# Implementation

- BFS
  - Get indegree of edges
  - Get edge with indegree = 0 and add to `queue` and add to visisted array as well
  - traversing to queue, get the upcoming edges of the current vertex, decrease by one value
  - Then checking any `indegree = 0` . If yes, then add to queue and visisted
  - Rinse and repeat
  - Checking the cycle

```python
# set up matrix graph
for i in verticles:
  for j in verticles:
    graph[i,j] = 0

def addEdge(i,j):
  graph[i,j] = 1
  indgree[j] += 1

def sortBFS():
  for item in indgree:
    if(item == 0):
      queue.add(item)
      visited.add(item)
      break

  sortedList = []
  while(queue):
    v = queue.pop()
    sortedList.add(v)
    for item in verticle:
      if(graph[v,item] == 1 and visisted[v] == False):
          indegree[item] -= 1
        if(indegree[item] == 0):
          queue.add(item)
          visisted.add(item)

  if(len(sortedList) != len(verticles)):
    print 'Graph has cycle'
    
def sortDFS(source, visited):

  visited[source] = True

  for item in verticles:
    if(graph[source,item]) == 1 and visited[item] == False:
      sortDFS(item)

  queue.append_front(source)

addEdge(0,1)
addEdge(0,2)
addEdge(1,3)
```

```python
from queue import Queue

from graph import *

def topological_sort(graph):

	queue = Queue()
	indegreeMap = {}

	for i in range(graph.numVertices):
		indegreeMap[i] = graph.get_indegree(i)

		# Queue all nodes which have no dependencies i.e.
		# no edges coming in
		if indegreeMap[i] == 0:
			queue.put(i)

	sortedList = []
	while not queue.empty():
		vertex = queue.get()

		sortedList.append(vertex)

		for v in graph.get_adjacent_vertices(vertex):
			indegreeMap[v] = indegreeMap[v] - 1

			if indegreeMap[v] == 0:
				queue.put(v)


	if len(sortedList) != graph.numVertices:
		raise ValueError("This graph has a cycle!")

	print(sortedList)



g = AdjacencyMatrixGraph(9, directed=True)
g.add_edge(0, 1)
g.add_edge(1, 2)
g.add_edge(2, 7)
g.add_edge(2, 4)
g.add_edge(2, 3)
g.add_edge(1, 5)
g.add_edge(5, 6)
g.add_edge(3, 6)
g.add_edge(3, 4)
g.add_edge(6, 8)

topological_sort(g)


```
