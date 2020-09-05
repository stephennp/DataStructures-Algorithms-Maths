# Interview-Docs
 This doc provides the data structures and algorithims are used for what?

## Data structures
### 1. Array
- Complexity:
  - Access: O(1)
  - Insert and the end: O(1)
  - Search: O(n)
  - Remove: O(n)
- What are they used for?
  - **A theater chair row**s
    - Each chair has assigned a position (from left to right), therefore every spectator will have assigned the number from the chair (s)he will be sitting on
    - Expand the problem to the whole theater (rows and columns of chairs) and you will have a 2D array (matrix)!
### 2. Linked List
- Store the current element's value and an address reference to the next element.
- Types:
  - Linked List
  - Double Linked List
  - Circular Linked List
- Complexity:
  - Access: O(n)
  - Insert: O(1)
  - Search: O(n)
  - Remove: O(1)
- What are they used for?
  - Memory management(Using pointer implies dynamic memory usage)
    - Elements can be added to it indefinitely, while an array will eventually get filled or have to be resized 
    - Removing elements from an array leaves empty spaces that are a waste of computer memory.
### 3. Stack
- Follows the rule LIFO (Last In, First Out).
- Complexity:
  - Push: O(1)
  - Top: O(1)
  - Pop: O(1)
  - Access others: O(n)
- What are they used for?
  -  Uses plates placed one over another in the canteen.
  -  Valid Parentheses Problem. Given a string of parantheses, you can check that they are matched using a stack.
- One disadvantage is that once you pop elements from the top in order to access other elements, their values will be **lost** from the stack's memory;
### 4. Queues
- Follows the rule FIFO (First In, First Out).
- Complexity:
  - Push: O(1)
  - Front: O(1)
  - Pop: O(1)
  - Search: O(n)
- What are they used for?
  -  A real life queue
    - In a call center application, a queue is used for saving the clients that are waiting to receive help from the consultant - these clients should get help in the order they called.
  - One special and very important type of queue is the priority queue.
  -  Is essential in many Graph Algorithms (Dijkstra's Algorithm, BFS, Prim's Algorithm, Huffman Coding - more about them below). It is implemented using a heap.
- Searching elements will remove all the accessed elements from the queue's memory;
### 5. Maps & Hash Tables
- Follows the rule FIFO (First In, First Out).
- Complexity:
  - Map
    - Insert: O(log n)
    - Access: O(log n)
    - Delete: O(log n)
    - Search: O(log n)
  - Hash
    - Insert: O(1)
    - Access: O(1)
    - Delete: O(1)
    - Search: O(1)
- What are they used for?
  - A language dictionary application. Each word from a language has assigned its definition to it
  - Contacts  is also a map. Each name has a phone number assigned to it.
  - Normalization of values
    - Let's say we want to assign to each minute of a day (24 hours = 3600 minutes) an index from 0 to 3599.
    - The hash function will be h(x) = x.hour*60+x.minute.
  - Maps are implemented using **self-balancing red-black trees**
### 6. Graphs
- A graph is a non-linear data structure representing a pair of two sets:
  - G={V, E}
    - V is the set of vertices (nodes)
    - E the set of edges (arrows).
- A graph can be traversed and processed using Breadth First Search (BFS) or Depth First Search (DFS)
- Types:
  - Undirected Graph
    - The edge (x, y) is available in both directions: (x, y) and (y, x).
  - Directed Graph
    - The edge (x, y) is called an arrow and the direction is given by the order of the vertices in its name
    - arrow (x, y) is different from arrow (y, x).
- What are they used for?
  - Friendships on Facebook are edges in an **undirected graph** (because it is reciprocal)
  - Instagram or Twitter, the relationship between an account and its followers/following accounts are arrows in a **directed graph** (not reciprocal).

### 7. Trees
- A tree is an undirected graph
- What are they used for?
  - A hierarchy
  - Genealogical tree. Your oldest ancestor is the root of the tree. The youngest generation represents the leaves' set. 
  - Subordinate relationship in the company you work for. That way you can find out who is your manager and who you should manage.
### 8. Binary Trees & Binary Search Trees
- A Binary Tree is a special type of tree: each vertice can have maximum two children
- A complete binary tree with n levels has all **2ⁿ-1** possible nodes.
- Types:
  - Preorder (Root, Left, Right)  
    - Copy tree
    - get the prefix expression of an expression tree
  - Inorder (Left, Root, Right)
    - all the nodes in the tree in ascending order
  - Postorder (Left, Right, Root); all done in O(n) time;
    - is used to delete the tree
    - get the postfix expression of an expression tree
- Complexity:
  - Search: O(log n)
  - Insert: O(log n)
  - Delete: O(log n)
- What are they used for?
  - Evaluation of logical expressions. Each expression can be decomposed into variables/constants and operators
    - Using inorder traversal of the AST (Abstract Syntax Tree)
  - AVL Trees, Red-Black Trees, ordered sets and maps are implemented using BSTs.
### 9. Self-balancing tree
- Complexity: O(log n)
- **AVL Trees** are self-balancing after every **insertion/deletion** because the difference in module between the heights of the left subtree and the right subtree of a node is **maximum 1**
- **Red-Black** Trees, each node stores an extra bit representing **color**, used to ensure the balance after every insert/delete operation.
- **Splay** trees, recently accessed nodes can be quickly accesed again, thus the amortized time complexity of any operation is still O(log n)
- What are they used for?
  - AVL
    - Best for data structure in Database Theory
    - Fastest in practice for searching elements, but the rotation of subtrees for self-balancing is costly;
  - Red-Black
    - Organize pieces of comparable data such as text fragments or numbers
    - HashMaps are implemented using RBTs in Java
    - Faster insertions and deletions because there are no rotations
  - Splay
    - Caches
    - Memory allocators
    - Garabage collectors
    - Data compression
    - Ropes (replacement of string used for long text strings)
    - Virtual memory, networking, file system in window NT
    - Searched item to be accessible in **O(1)** time if accessed again
### 10. Heaps
- A min-heap is a binary tree where each node has the property that its value is bigger or equal to its parent’s value
  - val[par[x]] <= val[x], with x a node of the heap
  - where val[x] is its value and par[x] its parent.
- A binary heap is a complete binary tree (all its levels are filled, except maybe for the last level).
- Complexity:
    - Insert: O(log n)
    - Delete: O(log n)
    - Max: O(1)
    - Min: O(1)
    - Heapsort: O(n*log n)
- What are they used for?
  - **Priority queues** can be efficiently implemented using a binary heap because it supports insert(), delete(), extractMax() and decreaseKey() operations in O(log n) time
  - Heaps are also essential in **graph algorithms** (because of the priority queue)
  - Quick **access** to the maximum/minimum item, a heap is the best option.
### 11. Tries
- A trie is an efficient **information retrival data** structure. Also known as a prefix tree
- If we store keys in a well balanced BST, it will need time proportional to L * log n
  - where n is the number of keys in the tree. That way, a trie is a way faster data structure (with O(L)) compared to a BST
  - But the penalty is on the trie storage requirements.
- Time Complexity : O(L)
- Space Complexity : O(Alphabet_Size * L * n)
  -  L is the length of the key.
- What are they used for?
  - Mostly used for storing **strings and their values**.
  - **Typing autocomplete & autosuggestions** Application in the Google search bar
    - A trie is the best choice because it is the fastest option
    - A faster search is more valuable than the storage saved if we didn’t use a trie.
  - Ortographical autocorrection of typed words
    - looking for the word in the dictionary or maybe for other instances of it in the same text.
  - The time complexity of insert/search operations is O(L), where L is the length of the key, which is way faster than a BST’s O(log n), but comparable to a hashtable;
  - Space complexity is actually a disadvantage: O(ALPHABET_SIZE*L*n).
### 12. Segment Tree
- A segment tree is a full binary tree that allows answering to queries efficiently, while still easily modifying its elements.
  - Each element on index **i** in the given array represents a leaf labeled with the **[i, i] interval**
  - A node having its children labeled **[x, y]**, respectively **[y, z]**, will have the **[x, z] interval** as a label
  - Therefore, given n elements **(0-indexed)**, the root of the segment tree will be labeled with **[0, n-1]**
- Time Complexity : O(Log n)
- Space Complexity : O(4 * n)
- What are they used for?
  -  Updates and queries
  - extremely useful in tasks that can be solved using **Divide & Conquer** Algorithms
  - require updates on their elements
  - the **sum/maximum/minimum** of n given elements are the most common applications of segment trees
  - Binary search can also use a segment tree if element updates are ocurring.
  - one efficient method of updating a whole range in a segment tree is called “Lazy Propagation” and it is also done in O(log n)
  - updating elements/ranges require O(log n) time; answering to a query is constant (O(1));
  - custom/user-defined aggregator, and not just simple aggregator like MAX, SUM, MIN, PRODUCT etc, for pre-processing of the nodes
### 13. Fenwick Tree (BIT)
- A fenwick tree, also known as a binary indexed tree **(BIT)**
  - is a data structure that is also used for efficient updates and queries
  - Compared to Segment Trees, BITs require less space and are easier to implement.
- Time Complexity : O(Log n)
- Space Complexity : O(n)
- What are they used for?
  - For instance:
    - We have an array arr[0 . . . n-1]. We would like to
      - Compute the sum of the first i elements.
      - Modify the value of a specified element of the array arr[i] = x where 0 <= i <= n-1.
    - A **simple solution** is to run a loop from 0 to i-1 and calculate the sum of the elements. To update a value, simply do arr[i] = x. The first operation takes O(n) time and the second operation takes O(1) time. Another simple solution is to create an extra array and store the sum of the first i-th elements at the i-th index in this new array. The sum of a given range can now be calculated in O(1) time, but the update operation takes O(n) time now. This works well if there are a large number of query operations but a very few number of update operations
  - Updates and queries
  - Used to calculate prefix sums — the prefix sum of the element on the ith position is the sum of the elements from the first position to the ith
  - They are represented using an array, where every index is represented in the binary system.
  - For instance, an index 10 is equivalent to an index 2 in the decimal system.
### 14. Disjoint Set Union
- We are given n elements, each of them representing a separate set. Disjoint Set Union (DSU) permits us to do two operations:
  - UNION — combine any two sets (or unify the sets of two different elements if they’re not from the same set);
  - FIND — find the set an element comes from.
  - they are represented using trees; once two sets are combined, one of the two roots becomes the main root and the parent of the other root is one of the other tree’s leaves;
- Time Complexity : O(1)
- Space Complexity : O(n)
- What are they used for?
  - DSUs are very important in graph theory
  - An example of cities and towns
    - Since neighbour cities with demographical and economical growth are expanding, they can easily create a metropolis
    - Therefore, two cities are combined and their residents live in the same metropolis
    - We can also check what city a person lives in, by calling the **FIND** function.
  - Union-Find Algorithm can be used to check whether an undirected graph contains cycle or not
### 15. Minimum Spanning Trees
- Given a connected and undirected graph, a spanning tree of that graph is a subgraph that is a tree and connects all the nodes together.
- A single graph can have many different spanning trees
- Time Complexity : O(m * Log n)
- What are they used for?
  - The MST problem is an optimization problem, a minimum cost problem.
  - Shortest Tour between cities
  - Sum of minimum spanning trees is as low as possible
- For instance: 
  - Vertices: {A,B,C}
    - Edges: (undirected) {A,B,4} {A,C,3} {B,C,2}
    - So basically it's a triangle with the given weights. Starting from A, Dijkstra's algorithm will give you (A,B) and (A,C) but the minimum spanning Tree will give you (A,C) and (C,B).

## Algorithms
## References:
1. https://dev.to/iuliagroza/complete-introduction-to-the-30-most-essential-data-structures-algorithms-43kd?fbclid=IwAR1WYHQ7loHbuEWo4KefnVHV2AvGurQftrTFdtJx5MobXhSECv-8Ws3bt08
2. 