# Intro

- Dynamic Programming is mainly an optimization over plain recursion. Wherever we see a recursive solution that has repeated calls for same inputs, we can optimize it using Dynamic Programming.
- The idea is to simply store the results of subproblems, so that we do not have to re-compute them when needed later. This simple optimization reduces time complexities from exponential to polynomial.
- For example, if we write simple recursive solution for Fibonacci Numbers, we get exponential time complexity and if we optimize it by storing solutions of subproblems, time complexity reduces to linear.

- The core idea of Dynamic Programming is to avoid repeated work by `remembering partial results` and this concept finds it application in a lot of real life situations.

- In programming, Dynamic Programming is a powerful technique that allows one to solve different types of problems in time `O(n2) or O(n3)` for which a naive approach would take `exponential time`.

- Jonathan Paulson explains Dynamic Programming in his amazing Quora answer here.

```
Writes down "1+1+1+1+1+1+1+1 =" on a sheet of paper.
"What's that equal to?"
Counting "Eight!"
Writes down another "1+" on the left.
"What about that?"
"Nine!" " How'd you know it was nine so fast?"
"You just added one more!"
"So you didn't need to recount because you remembered there were eight! Dynamic Programming is just a fancy way to say remembering stuff to save time later!"
```

# Dynamic Programming algorithms

- [Unix diff](https://en.wikipedia.org/wiki/Diff_utility) for comparing two files
- [Bellman-Ford](https://en.wikipedia.org/wiki/Bellman%E2%80%93Ford_algorithm) for shortest path routing in networks
- [TeX](http://en.wikipedia.org/wiki/TeX) the ancestor of LaTeX
- [WASP](https://en.wikipedia.org/wiki/WASP_%28cricket_calculation_tool%29) - Winning and Score Predictor

# Dynamic Programming and Recursion:

- Dynamic programming is basically, recursion plus using common sense. What it means is that recursion allows you to express the value of a function in terms of other values of that function.
- Where the common sense tells you that if you implement your function in a way that the recursive calls are done in advance, and stored for easy access, it will make your program faster.
- This is what we call `Memoization` - it is memorizing the results of some specific states, which can then be later accessed to solve other sub-problems.
  The intuition behind dynamic programming is that we trade space for time, i.e. to say that instead of calculating all the states taking a lot of time but no space, we take up space to store the results of all the sub-problems to save time later.

- Let's try to understand this by taking an example of Fibonacci numbers.

```c++
Fibonacci (n) = 1; if n = 0
Fibonacci (n) = 1; if n = 1
Fibonacci (n) = Fibonacci(n-1) + Fibonacci(n-2)
```

- So, the first few numbers in this series will be: 1, 1, 2, 3, 5, 8, 13, 21... and so on!

- A code for it using pure recursion:

```c++
  int fib (int n) {
        if (n < 2)
            return 1;
        return fib(n-1) + fib(n-2);
    }
```

- Using Dynamic Programming approach with memoization:

```c++
 void fib () {
        fibresult[0] = 1;
        fibresult[1] = 1;
        for (int i = 2; i<n; i++)
           fibresult[i] = fibresult[i-1] + fibresult[i-2];
    }
```

- Are we using a different recurrence relation in the two codes? No. Are we doing anything different in the two codes? Yes.

- In the recursive code, a lot of values are being recalculated multiple times. We could do good with calculating each unique quantity only once. Take a look at the image to understand that how certain values were being recalculated in the recursive way:

  ![Drag Racing](fib_tree.png)

- Majority of the Dynamic Programming problems can be categorized into two types:
  - Optimization problems.
  - Combinatorial problems.

- The optimization problems expect you to select a feasible solution, so that the value of the required function is minimized or maximized. Combinatorial problems expect you to figure out the number of ways to do something, or the probability of some event happening.

- Every Dynamic Programming problem has a schema to be followed:
  - Show that the problem can be broken down into optimal sub-problems.
  - Recursively define the value of the solution by expressing it in terms of optimal solutions for smaller sub-problems.
  - Compute the value of the optimal solution in bottom-up fashion.
  - Construct an optimal solution from the computed information.

# Memoization (BottomUp)
-  I'm going to learn programming. Then, I will start practicing. Then, I will start taking part in contests. Then, I'll practice even more and try to improve. After working hard like crazy, I'll be an amazing coder.

- This is a laissez-faire approach: You assume that you have already computed all subproblems and that you have no idea what the optimal evaluation order is. Typically, you would perform a recursive call (or some iterative equivalent) from the root, and either hope you will get close to the optimal evaluation order, or obtain a proof that you will help you arrive at the optimal evaluation order. You would ensure that the recursive call never recomputes a subproblem because you cache the results, and thus duplicate sub-trees are not recomputed.
```
example: If you are calculating the Fibonacci sequence fib(100), you would just call this, and it would call fib(100)=fib(99)+fib(98), which would call fib(99)=fib(98)+fib(97), ...etc..., which would call fib(2)=fib(1)+fib(0)=1+0=1. Then it would finally resolve fib(3)=fib(2)+fib(1), but it doesn't need to recalculate fib(2), because we cached it.
```
- This starts at the top of the tree and evaluates the subproblems from the leaves/subtrees back up towards the root.

# Tabulation (Top Down)
-I will be an amazing coder. How? I will work hard like crazy. How? I'll practice more and try to improve. How? I'll start taking part in contests. Then? I'll practicing. How? I'm going to learn programming.

- In Top Down, you start building the big solution right away by explaining how you build it from smaller solutions. In Bottom Up, you start with the small solutions and then build up.

- Memoization is very easy to code and might be your first line of approach for a while. Though, with dynamic programming, you don't risk blowing stack space, you end up with lots of liberty of when you can throw calculations away. The downside is that you have to come up with an ordering of a solution which works.

- You can also think of dynamic programming as a "table-filling" algorithm (though usually multidimensional, this 'table' may have non-Euclidean geometry in very rare cases*). This is like memoization but more active, and involves one additional step: You must pick, ahead of time, the exact order in which you will do your computations. This should not imply that the order must be static, but that you have much more flexibility than memoization.
```
example: If you are performing fibonacci, you might choose to calculate the numbers in this order: fib(2),fib(3),fib(4)... caching every value so you can compute the next ones more easily. You can also think of it as filling up a table (another form of caching).
```
- I personally do not hear the word 'tabulation' a lot, but it's a very decent term. Some people consider this "dynamic programming".
- Before running the algorithm, the programmer considers the whole tree, then writes an algorithm to evaluate the subproblems in a particular order towards the root, generally filling in a table.
*footnote: Sometimes the 'table' is not a rectangular table with grid-like connectivity, per se. Rather, it may have a more complicated structure, such as a tree, or a structure specific to the problem domain (e.g. cities within flying distance on a map), or even a trellis diagram, which, while grid-like, does not have a up-down-left-right connectivity structure, etc. For example, user3290797 linked a dynamic programming example of finding the maximum independent set in a tree, which corresponds to filling in the blanks in a tree.