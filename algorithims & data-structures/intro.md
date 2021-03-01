# What is Resource?

- Operations: THe number of times we need to perform some operations
- Memory: How much memory is consumed by the algorithims
- Others: Network transfer, compression ratios, disk usage

# BigO notation

- O(1) : A constant-time function/method, is unchanged by the input size
  - Input size: 1 -> Cost: 1
  - Input size: 100 -> Cost: 1
  - Input size: 1000 -> Cost: 1
  - Input size: 1000000 -> Cost: 1
- O(logn) : A function whose cost scales logarithmically with the input size
  - Input size: 1 -> Cost: 1
  - Input size: 100 -> Cost: 1
  - Input size: 1000 -> Cost: 3
  - Input size: 1000000 -> Cost: 6
  - Examples: Find the word `giraffe` from `aardvark` to `zebra`
    - We can split by cutting problem space in half -> `aardvark` -> `ocelot` -> `zebra`
    - Then continuely cutting problem space in half until get the result.
- O(n): A linear-time function/method, scale linearly by the input size
  - Input size: 1 -> Cost: 1
  - Input size: 100 -> Cost: 100
  - Input size: 1000 -> Cost: 1000
  - Input size: 1000000 -> Cost: 1000000
  ```csharp
    char[] a = 'abcdefgh'
    for(int i = 0 ; i<a.length;i++>)
    {
      Console.WriteLine(a[i])
    }
  ```
- O(n^2) : : A quadratic-time function/method, scale quadratic growth relative to the input size
  - Input size: 1 -> Cost: 1
  - Input size: 10 -> Cost: 100
  - Input size: 1000 -> Cost: 1000000
  - Input size: 1000000 -> Cost: 1e+12
  - Examples: Double nested loop is an indication that you have O(n^2) algorithim
  ```csharp
    for(int i = 0 ; i<arr.length;i++>)
    {
      for(int j = 0; j<arr.length ; j++)
      {
        process(i,j)
      }
    }
  ```
- O(nm) : A function which has two- inputs that contribute to the growth
  - Example: A nested loop that iterates over distinct collections of data
  ```csharp
    for(int i = 0 ; i<arrA.length;i++>)
    {
      for(int j = 0; j<arrB.length ; j++)
      {
        process(arrA[i],arrB[j])
      }
    }
  ```

# Topic

- data types
  - stack, queue, bag, union-find, priority queue
- sorting
  - quicksort, mergesort, heapsort
- searching
  - BST, red-black BST, hash table
- graphs
  - BFS, DFS, Prim, Kruskal, Dijkstra
- strings
  - radix sorts, tries, KMP, regexps, data compression
- advanced
  - B-tree, suffix array, maxflow

# Why study algorithms?

Their impact is broad and far-reaching.

- Internet. Web search, packet routing, distributed file sharing, ...
- Biology. Human genome project, protein folding, ...
- Computers. Circuit layout, file system, compilers, ...
- Computer graphics. Movies, video games, virtual reality, ...
- Security. Cell phones, e-commerce, voting machines, ...
- Multimedia. MP3, JPG, DivX, HDTV, face recognition, ...
- Social networks. Recommendations, news feeds, advertisements, ...
- Physics. N-body simulation, particle collision simulation, ...
