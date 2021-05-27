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

- I think it using BFS algorithmz
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
  - All vertices in spanning tree, stop Minimum spanning tree found

- `Benefit`: Intermediate result is a tree as well
- `Drawback`: Does not work for disconnected graphs

## Complexity

- Binary Heap : O(E ln(V) )
- Array : O(E+V^2)

## Implementation

```c++
#include <iostream>
#include <vector>
#include <queue>
#include <functional>
#include <utility>

using namespace std;
const int MAX = 1e4 + 5;
typedef pair<long long, int> PII;
bool marked[MAX];
vector <PII> adj[MAX];

long long prim(int x)
{
    priority_queue<PII, vector<PII>, greater<PII> > Q;
    int y;
    long long minimumCost = 0;
    PII p;
    Q.push(make_pair(0, x));
    while(!Q.empty())
    {
        // Select the edge with minimum weight
        p = Q.top();
        Q.pop();
        x = p.second;
        // Checking for cycle
        if(marked[x] == true)
            continue;
        minimumCost += p.first;
        marked[x] = true;
        for(int i = 0;i < adj[x].size();++i)
        {
            y = adj[x][i].second;
            if(marked[y] == false)
                Q.push(adj[x][i]);
        }
    }
    return minimumCost;
}

int main()
{
    int nodes, edges, x, y;
    long long weight, minimumCost;
    cin >> nodes >> edges;
    for(int i = 0;i < edges;++i)
    {
        cin >> x >> y >> weight;
        adj[x].push_back(make_pair(weight, y));
        adj[y].push_back(make_pair(weight, x));
    }
    // Selecting 1 as the starting node
    minimumCost = prim(1);
    cout << minimumCost << endl;
    return 0;
}
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