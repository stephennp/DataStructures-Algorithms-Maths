# Intro
## Algorithms
### 1. Divide and Conquer (DAC)
- An important category of algorithms that needs to be understood before diving into other topics
- It is used to solve problems that can be divided into subproblems that are similar to the original problem, but smaller in size
- DAC then recursively solves them and finally merges the results to find the solution of the problem
- Complexity: T(n)=D(n)+C(n)+M(n)
  - Meaning that every stage has a different complexity depending on the problem.
- It has three stages:
  - Divide — the problems into subproblems;
  - Conquer — the subproblems by using recursion;
  - Merge — the subproblems’ results into the final solution.
- What are they used for?
  - **Parallel programming** using multiple processors, so the subproblems are executed on different machines
  - DAC is the base of many algorithms such as Quick Sort, Merge Sort, Binary Search or fast multiplication algorithms.
  - **Binary Search**
    - is a searching algorithm.
    - In each step, the algorithm compares the input element x with the value of the middle element in array
    - If the values match, return the index of the middle
    - Otherwise, if x is less than the middle element, then the algorithm recurs for left side of middle element, else recurs for the right side of the middle element
    - Time Complexity: O(log2n)
  - **Quick Sort**
    - The algorithm picks a pivot element
    - Rearranges the array elements in such a way that all elements smaller than the picked pivot element move to left side of pivot
    - And all greater elements move to right side
    - Finally, the algorithm recursively sorts the subarrays on left and right of pivot element.
    - Time Complexity: O(n^2)
  - **Merge Sort** is also a sorting algorithm
    - The algorithm divides the array in two halves
    - Recursively sorts them and finally merges the two sorted halves.
    - Time Complexity: 	O(n log(n))
  - **Closest Pair of Points**
    - The problem is to find the closest pair of points in a set of points in x-y plane.
    - The problem can be solved in **O(n^2)** time by calculating distances of every pair of points and comparing the distances to find the minimum. - The Divide and Conquer algorithm solves the problem in **O(nLogn)** time.
    - Time Complexity: O(nLogn)
  - **Strassen’s Algorithm**
    - is an efficient algorithm to multiply two matrices
    - A simple method to multiply two matrices need 3 nested loops and is O(n^3)
    - Strassen’s algorithm multiplies two matrices in O(n^2.8974) time.
    - Time Complexity: O(n^2.8974)
  - **Cooley–Tukey Fast Fourier Transform (FFT)** algorithm
    - is the most common algorithm for FFT. It is a divide and conquer algorithm which works in O(nlogn) time.
    - Time Complexity: O(nlogn)
  - **Karatsuba algorithm for fast multiplication**
    - it does multiplication of two n-digit numbers in at most 3 n^{\log_23}\approx 3 n^{1.585}single-digit multiplications in general (and exactly n^{\log_23} when n is a power of 2).
    - It is therefore faster than the classical algorithm, which requires n2 single-digit products. If n = 210 = 1024, in particular, the exact counts are 310 = 59, 049 and (210)2 = 1, 048, 576, respectively.
    - A Naive Approach : O(n^2)
    - Time Complexity: O(N^(log 3) that is O(N^1.585)
  - **Fibonacci numbers**
  - **Matrix Multiplication**
- SUM OF N ELEMENTS USING DAC - C++
  ```C++
  int DAC(int arr[], int start, int finish)
  {
      if(start==finish)
          return arr[start];
      else
      {
          int mid = (start+finish)/2;
          int sum1 = DAC(arr, start, mid);
          int sum2 = DAC(arr, mid+1, finish);
          return sum1+sum2;
      }
  }
  ```
### 2. Sorting Algorithms
#### 2.1 Bubble Sort
- Is one of the simplest sorting algorithms
  - It is based on a repeated swap between adjacent elements if they are in wrong order. It is stable
- Time complexity: O(n²)
-  Auxiliary space: O(1).
#### 2.1 Counting Sort
- It is basically using the frequency of each element (a kind of hashing)
- Determining the minimum and maximum value and then iterating between them to place each element based on its frequency.
- It is efficient if the range of input is not significantly greater than the number of elements.
- Time complexity: O(n+k) where n is the number of elements in input array and k is the range of input.
- Space complexity:O(n+k)
#### 2.2 Quick Sort
- An application of Divide and Conquer
- It is based on choosing an element as a pivot (first, last or median) and then swapping elements in order to place the pivot between all the elements smaller than it and all the elements bigger than it
- Time complexity: O(n*log n)
- Space complexity: no additional space
#### 2.3 Merge Sort
- is also a Divide & Conquer application
- It divides the array in two halves, sorts each half and then merges them.
- It is also super fast like Quick Sort
- Time complexity: O(n*log n)
- Space complexity: O(n) to store two subarrays at the same time and, finally, merge them.
#### 2.4 Radix Sort
- Uses Counting Sort as a subroutine, so it is not a comparison based algorithm
- What if the elements are in range from 1 to n2?
  - We can’t use counting sort because counting sort will take O(n2) which is worse than comparison based sorting algorithms. Can we sort such an array in linear time?
  - Radix Sort is the answer. The idea of Radix Sort is to do digit by digit sort starting from least significant digit to most significant digit. Radix sort uses counting sort as a subroutine to sort.
- Time complexity: O(n+k) where elements are in range [1, k]. It sorts the elements digit by digit starting with the least significant one (units), to the most (tens, hundreds etc.)
- Space complexity: O(n)
### 3. Searching Algorithms
#### 3.1 Linear Search
- This algorithm’s approach is very simple: you start searching for your value from the first index of the data structure
- You compare them one by one until your value and your current element are equal.
- If that specific value is not in the DS, return -1.
- Time Complexity: O(n)
#### 3.2 Binary Search
- BS is one efficient search algorithm based on Divide and Conquer
- **Unfortunately, it only works only on sorted data structures**
- Being a DAC method, you continuously divide the DS in two halves and compare your in-search value with the middle element’s value.
  - If they are equal, the search is finished.
  - Either way, if your value is bigger/smaller than it, the search should continue on the right/left half.
Time Complexity: O(log n)
### 4. Sieve of Eratosthenes
- The method uses a frequency list/map that marks the primality of every number in the range
  - [0, n]: ok[x]=0 if x is prime
  - ok[x]=1 otherwise
- We begin choosing every prime number from our list and marking its multiples from the list with 1 — that way, we choose the unmarked (0) numbers. - Finally, we can easily answer in O(1) to as many queries as we want.
- What are they used for?
  - Given an integer number n, print all the prime numbers smaller or equal to n.
  - Sieve of Eratosthenes is one of the most efficient algorithms that solves this problem and it perfectly works for n smaller than **10.000.000**
- Time complexity: O(n*log(log n)) for the classical algorithm, O(n) for the optimized one.
- Space complexity: O(n)
### 5. Knuth-Morris-Pratt Algorithm
- Given a text of length n and a pattern of length m, find all the occurrences of the pattern in the text.
- Its working the best when the pattern has many repeating subpatterns.
- Knuth-Morris-Pratt Algorithm (KMP) is an efficient way to solve the pattern matching problem.
- For instance: find a pattern pat[] ( abxab) in a string txt[] (abxababxab)
- The naive solution is based on using a “sliding window”, where we compare character to character every time we set a new beginning index, starting from index 0 of the text to index n-m. That way, time complexity is O(m*(n-m+1))~O(n*m).
- Its using a **sliding window**, but instead of comparing all the characters to the substring’s, it is constantly looking for the longest suffix of the current subpattern which is also its prefix.
- In other words, anytime we detect a mismatch after some matches, we already know some of the characters in the text of the next window. 
- Therefore, it is useless to match them again, so we restart the matching with the same character in the text with a character after that prefix. - - How do we know how many characters we should skip? Well, we should build a pre-process array that tells us how many characters should be skipped.
- What are they used for?
  - Given a text of length n and a pattern of length m, find all the occurrences of the pattern in the text.
  - Its working the best when the pattern has many repeating subpatterns.
- Time complexity: O(n)

### 6. Greedy
- At every step, we can make a choice that looks best at the moment, and we get the optimal solution of the complete problem.
- The Greedy method is mostly used for problems that require optimization and the local optimal solution leads to the global optimal solution
- when using Greedy, the optimal solution at each step leads to the overall optimal solution
- However, in most cases, the decision we make at one step affects the list of decisions for the next step
  - In this case, the algorithm must be mathematically demonstrated
- Greedy also produces great solutions on some mathematical problems, but not on all (it is possible that the most optimal solution is not guaranteed)!
- A Greedy algorithm generally has five components:
  - a candidate set — from which a solution is created;
  - a selection function — chooses the best candidate;
  - a feasibility function — can determine if a candidate is able to contribute to the solution;
  - an objective function — assigns the candidate to the (partial) solution;
  - a solution function — builts the solution from the partial solutions
- What are they used for?
  - **Activity Selection Problem**
    - You are given n activities with their start and finish times. Select the maximum number of activities that can be performed by a single person, assuming that a person can only work on a single activity at a time.
    - 1. Sort the activities according to their finishing time
    - 2. Select the first activity from the sorted array and print it.
    - 3. Do following for remaining activities in the sorted array.
        - If the start time of this activity is greater than or equal to the finish time of previously selected activity then select this activity and print it.
    - Time Complexity: O(nlogn)
  - **Job Sequencing Problem**
    - Given an array of jobs where every job has a deadline and associated profit if the job is finished before the deadline. It is also given that every job takes single unit of time, so the minimum possible deadline for any job is 1. How to maximize total profit if only one job can be scheduled at a time.
    - Sort all jobs in descending order of profit
    - Init the result sequence as the first job in sorted order
    - Do the following n-1 jobs
      - If the current job can fit the result sequence without missing deadline, add current job to result, else ignore the current job
    - Time Complexity: O(n^2)
  - **Huffman Coding**
    - It assigns variable-length bit codes to different characters.
    - The Greedy Choice is to assign least bit length code to the most frequent character. 
    - The variable-length codes assigned to input characters as Prefix Codes
    - Use Heap Tree
    - What are they used for?
      - Lossless data compression algorithm
    - Time Complexity: O(nlogn)
  - **Kruskal’s Minimum Spanning Tree (MST)**
    - In Kruskal’s algorithm, we create a MST by picking edges one by one. The Greedy Choice is to pick the smallest weight edge that doesn’t cause a cycle in the MST constructed so far.
    - Kruskal’s algorithm runs faster in **sparse** graphs.
    - It traverses one node only once.
    - What are they used for?
      - To find the **minimum cost spanning tree** uses the greedy approach for a connected weighted graphs
    - Time Complexity: O(logV), V being the number of vertices.
  - **Prim’s Minimum Spanning Tree**
    - In Prim’s algorithm also, we create a MST by picking edges one by one.
    - We maintain two sets: a set of the vertices already included in MST and the set of the vertices not yet included. 
    - The Greedy Choice is to pick the smallest weight edge that connects the two sets.
    - It traverses one node more than one time to get the minimum distance.
    - Prim’s algorithm runs faster in **dense** graphs.
    - What are they used for?
      - To find the **minimum cost spanning tree** uses the greedy approach for a connected weighted graph
    - Time complexity: O(V^2), V being the number of vertices.
  - **Dijkstra’s Shortest Path**
    - The Dijkstra’s algorithm is very similar to Prim’s algorithm.
    - The shortest path tree is built up, edge by edge
    - We maintain two sets: 
      - a set of the vertices already included in the tree
      - the set of the vertices not yet included
    - The Greedy Choice is to pick the edge that connects the two sets and is on the smallest weight path from source to the set that contains not yet included vertices.
    - What are they used for?
      - Find the Shortest Path
      - It just talks about the shortest route and cost between 2 nodes. So in your case, if there's a need to include all nodes in between then the suggestion for TSP (Travelling sale person) is valid.
      - If you want to have the shortest routes and cost between all pairs of nodes, then you should go for Floyd's algorithm which is basically an extension of Dijkstra.
    - Time complexity:  O(V^2) but with min-priority queue it drops down to O ( V + E l o g V )
    - Time complexity: O(LogV) for operations like extract-min and decrease-key value of Min Heap
      - Min Heap is used as a priority queue to get the minimum distance vertex from set of not yet included vertices
  - **Fractional Knapsack Problem**
    - Given weights and values of n items, we need to put these items in a knapsack of capacity W to get the maximum total value in the knapsack.
    - In the 0-1 Knapsack problem, we are not allowed to break items. We either take the whole item or don’t take it.
    - An efficient solution is to use **Greedy** approach. 
      - The basic idea of the greedy approach is to calculate the ratio value/weight for each item and sort the item on basis of this ratio.
      - Then take the item with the highest ratio and add them until we can’t add the next item as a whole and at the end add the next item as much as we can. Which will always be the optimal solution to this problem.
    - Time complexity: O(NlogN) where N is the number of items in S.

### 7. Dynamic Programming
- Dynamic Programming (DP) is a similar approach to Divide & Conquer. It also breaks the problem into similar subproblems, but they are actually overlapping and codependent — they’re not solved independently.
- Each subproblem’s result can be used anytime later and it is built using memoization (precalculation). DP is mostly used for (time & space) optimization and it is based on finding a recurrence.
- DP applications include Fibonacci number series, Tower of Hanoi, Roy-Floyd-Warshall, Dijkstra etc. Below we are going to discuss about a DP solution of the 0–1 Knapsack Problem.
#### 7.1 0–1 Knapsack Problem
- Given weights and values of n items,we need to put these items in a knapsack of capacity W to get the maximum total value in the knapsack
- Fractioning items just as in the Greedy solution is **not allowed**
- The 0–1 property is given by the fact that we should either pick the whole item or not choose it at all.
- We build a DP structure as a matrix dp[i][cw] storing the maximum profit that we can obtain by choosing i objects whose total weight is cw. It is easy to notice that we should firstly initialize dp[1][w[i]] with v[i], where w[i] is the weight of the ith object and v[i] its value.
- The recurrence is the following: dp[i][cw] = max(dp[i-1][cw], dp[i-1][cw-w[i]]+v[i])
- Time complexity: O(nW) where, n is the number of items and W is the capacity of knapsack.
### 8. Longest Common Subsequence
- Given two sequences, find the length of the longest subsequence present in both of them. A subsequence is a sequence that appears in the same relative order, but not necessarily contiguous.
- For example, “bcd”, “abdg”, “c” are subsequences of “abcdefg”.
### 9. Longest Increasing Subsequence
### 10. Convex Hull
### 11. Graph Traversals
### 12. Floyd-Warshall Algorithm
### 13. Dijkstra’s Algorithm & Bellman-Ford Algorithm
### 14. Kruskal’s Algorithm
### 15. Topological Sorting
### 12. Shannon-Fano Algorithm for Data Compression
### 13. LZW (Lempel–Ziv–Welch) for Data Compression
### 14. Map Reduce
- https://en.wikipedia.org/wiki/MapReduce

### 15. Memorization and Recursion
- https://dev.to/ionabrabender/memoization-and-recursion-228f

## References:
1. https://dev.to/iuliagroza/complete-introduction-to-the-30-most-essential-data-structures-algorithms-43kd?fbclid=IwAR1WYHQ7loHbuEWo4KefnVHV2AvGurQftrTFdtJx5MobXhSECv-8Ws3bt08
2. GeeksforGeeks Youtube: https://www.youtube.com/channel/UC0RhatS1pyxInC00YKjjBqQ, thanks so much for much comprehensive videos :)