# Intro
- A graph is a data structure that is defined by two components :
  - A `node` or a vertex.
  - An `edge` E or ordered pair is a connection between two nodes u,v that is identified by unique pair(u,v). The pair (u,v) is ordered because (u,v) is not same as (v,u) in case of directed graph.The edge may have a weight or is set to one in case of unweighted graph.
- Applications:
  - Graph is a data structure which is used extensively in our real-life.
  - Social Network: Each user is represented as a node and all their activities,suggestion and friend list are represented as an edge between the nodes.
  - Google Maps: Various locations are represented as vertices or nodes and the roads are represented as edges and graph theory is used to find shortest path between two nodes.
  - Recommendations on e-commerce websites: The “Recommendations for you” section on various e-commerce websites uses graph theory to recommend items of similar type to user’s choice.
  - Graph theory is also used to study molecules in chemistry and physics.
- Characteristics of graphs:
  - `1. Adjacent node`: A node ‘v’ is said to be adjacent node of node ‘u’ if and only if there exists an edge between ‘u’ and ‘v’.
  - `2. Degree of a node`: In an undirected graph the number of nodes incident on a node is the degree of the node.
    - In case of directed graph ,Indegree of the node is the number of arriving edges to a node.
Outdegree of the node is the number of departing edges to a node.
  - `3. Path`: A path of length ‘n’ from node ‘u’ to node ‘v’ is defined as sequence of n+1 nodes.
P(u,v)=(v0,v1,v2,v3…….vn)
    - A path is simple if all the nodes are dist  inct,exception is source and destination are same.
- Types of graphs:
  - `1. Directed graph`:
    - A graph in which the direction of the edge is defined to a particular node is a directed graph.
    - `Directed Acyclic graph`: It is a directed graph with no cycle.For a vertex ‘v’ in DAG there is no directed edge starting and ending with vertex ‘v’.
     - **Real World Application** :Critical game analysis,expression tree evaluation,game evaluation.
    - `Tree`: A tree is just a restricted form of graph.That is, it is a DAG with a restriction that a child can have only one parent.
  - `2. Undirected graph`:
    - A graph in which the direction of the edge is not defined.So if an edge exists between node ‘u’ and ‘v’,then there is a path from node ‘u’ to ‘v’ and vice versa.
    - `Connected graph`: A graph is connected when there is a path between every pair of vertices.In a connected graph there is no unreachable node.
    - `Complete graph`: A graph in which each pair of graph vertices is connected by an edge.In other words,every node ‘u’ is adjacent to every other node ‘v’ in graph ‘G’.A complete graph would have n(n-1)/2 edges.See below for proof.
    - `Biconnected graph`: A connected graph which cannot be broken down into any further pieces by deletion of any vertex.It is a graph with no articulation point.
# Intro 2
- A graph is a structure amounting to a set of objects in which some pairs of the objects are in some sense “related”.
- The objects of the graph correspond to `vertices` and the relations between them correspond to `edges`. 
- A graph is depicted diagrammatically as a set of dots depicting vertices connected by lines or curves depicting edges.
Formally,

“A graph $G = (V, E)$ consists of $V$, a non-empty set of vertices (or nodes) and $E$, a set of edges. Each edge has either one or two vertices associated with it, called its `endpoints`.”
- Types of graph :There are several types of graphs distinguished on the basis of edges, their direction, their weight etc.

  - `1. Simple graph` – A graph in which each edge connects two different vertices and where no two edges connect the same pair of vertices is called a simple graph
    - The above graph is a simple graph, since no vertex has a self-loop and no two vertices have more than one edge connecting them.
    - The edges are denoted by the vertices that they connect- $\{A,B\}$ is the edge connecting vertices A and B.
  - `2. Multigraph` – A graph in which multiple edges may connect the same pair of vertices is called a multigraph.
    - Since there can be multiple edges between the same pair of vertices, the multiplicity of edge tells the number of edges between two vertices.
    - The above graph is a multigraph since there are multiple edges between B and C. The multiplicity of the edge $\{B, C\}$ is 2.
- In some graphs, unlike the one’s shown above, the edges are directed. This means that the relation between the objects is one-way only and not two-way. The direction of the edges may be important in some applications.

- Based on whether the edges are directed or not we can have directed graphs and undirected graphs. This property can be extended to simple graphs and multigraphs to get simple directed or undirected simple graphs and directed or undirected multigraphs.

## Basic graph Terminology
- In the above discussion some terms regarding graphs have already been explained such as vertices, edges, directed and undirected edges etc. There are more terms which describe properties of vertices and edges.

- `Adjacency`:
  - In a graph G two vertices u and v are said to be adjacent if they are the endpoints of an edge. - The edge $\{u, v\}$ -  e is said to be incident with the vertices.
  - In case the edge is directed, u is said to be `adjacent` to v and v is said to be `adjacent` from u. Here, u is said to be the intitial vertex and v is said to the terminal vertex. 
- `Degree`:
  - The degree of a vertex is the number of edges incident with it, except the self-loop which contributes twice to the degree of the vertex.
  - Degree of a vertex u is denoted as $deg(u)$.
  - In case of directed graphs, the degree is further classified as `in-degree` and `out-degree`.
    - The in-degree of a vertex is the number of edges with the given vertex as the terminal vertex. 
    - The out-degree of a vertex is the number of edges with the given vertex as the initial vertex. - In-degree is denoted as $deg^-(u)$ and out-degree is denoted as $deg^+(u)$ .
  - For example in the directed graph shown above depicting flights between cities, the in-degree of the vertex “Delhi” is 3 and its out-degree is also 3.
- Note: If a vertex has zero degree, it is called `isolated`. If the degree is one then it’s called pendant.

## Handshaking Theorem :
- What would one get if the degrees of all the vertices of a graph are added. In case of an undirected graph, each edge contributes twice, once for its initial vertex and second for its terminal vertex.
- So the sum of degrees is equal to twice the number of edges. This fact is stated in the `Handshaking Theorem`.
- Let G = $(V, E)$ be an undirected graph with e edges. Then
$2e = \sum_{u\in V} deg(u)$

In case G is a directed graph,
$\sum_{u\in V} deg^-(u) = \sum_{u\in V} deg^+(u) = |E|$
- The handshaking theorem, for undirected graphs, has an interesting result –
  - `An undirected graph has an even number of vertices of odd degree.`
- Proof :
  - Let $V_{1}$ and $V_{2}$ be the sets of vertices of even and odd degrees respectively.
  - We know by the handshaking theorem that, $2e = \sum_{u\in V} deg(u)$ So,
$2e = \sum_{u\in V} deg(u) = \sum_{u\in V_{1}} deg(u) + \sum_{u\in V_{2}} deg(u)$
  - The sum of degrees of vertices with even degrees is even. The LHS is also even, which means that the sum of degrees of vertices with odd degrees must be even.
  - Thus, the number of vertices with odd degree is even.

## Some special Simple Graphs :

1. Complete Graphs – A simple graph of n vertices having exactly one edge between each pair of vertices is called a complete graph. A complete graph of n vertices is denoted by $K_{n}$. Total number of edges are $n*(n-1)/2$ with n vertices in complete graph.
2. Cycles – Cycles are simple graphs with vertices $n \geq 3 and edges \{1, 2\},\: \{2, 3\}...\: \{n-1, n\}\: and\: \{n, 1\}$. Cycle with n vertices is denoted as $C_{n}$. Total number of edges are n with n vertices in cycle graph.
3. Wheels – A wheel is just like a cycle, with one additional vertex which is connected to every other vertex. Wheels of n vertices with 1 addition vertex are denoted by $W_{n}$. Total number of edges are $2*(n-1)$ with n vertices in wheel graph.
4. Hypercube – The Hypercube or n-cube is a graph with $2^n$ vertices each represented by a n-bit string. The vertices which differ by at most 1-bit are connected by edges. A hypercube of $2^n$ vertices is denoted by $Q_{n}$. Total number of edges are $n*2^{n-1}$ with $2^n$ vertices in cube graph.
5. Bipartite Graphs – A simple graph G is said to be bipartite if its vertex set V can be divided into two disjoint sets such that every edge in G has its initial vertex in the first set and the terminal vertex in the second set. Total number of edges are (n*m) with (n+m) vertices in bipartite graph.

## References:
- Connected Graph: https://www.youtube.com/watch?v=z9cTXaLG1kk&ab_channel=WrathofMath
- Complete Graph: https://www.youtube.com/watch?v=egz_cP6vbIc&ab_channel=WrathofMath