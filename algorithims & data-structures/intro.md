# What is Resource?

- Operations: THe number of times we need to perform some operations
- Memory: How much memory is consumed by the algorithims
- Others: Network transfer, compression ratios, disk usage

# Order of growth

- Is how the time of execution depends on the length of the input.

```python
for i : 1 to length of A
    if A[i] is equal to x
        return TRUE
return FALSE
```

- N: `length` of array A
- c: for `if` condition and `return` statement

# O-notation

- To denote asymptotic upper bound, we use O-notation. For a given function `g(n)` , we denote by O(g(n)) (pronounced “big-oh of g of n”) the set of functions:

```
O(g(n)) = {f(n): there exist positive constants c and n(0) such that 0<= f(n) <= c*g(n) for all n >= n(0)}
```

# Ω-notation

- To denote asymptotic lower bound Ω-notation, we use Ω-notation. For a given function , we denote by Ω(g(n)) (pronounced “big-omega of g of n”) the set of functions:

```
Ω(g(n)) = { f(n): there exist positive constants c and n(0) such that 0<= c* g(n) <= f(n) for all n>= n(0)}
```

# ⊖-notation

- To denote asymptotic tight bound, we use ⊖-notation. For a given function g(n), we denote by ⊖(g(n)) (pronounced “big-theta of g of n”) the set of functions:

```
⊖(g(n)) = { f(n): there exist positive constants c(1), c(2) and n(0) such that 0<= c(1)* g(n) <= f(n) <= c(2) * g(n) for all n>= n(0)}
```

# O(1)
- A constant-time function/method, is unchanged by the input size
  - Input size: 1 -> Cost: 1
  - Input size: 100 -> Cost: 1
  - Input size: 1000 -> Cost: 1
  - Input size: 1000000 -> Cost: 1

```csharp
// Odds or Even
// It doesn’t matter if n is 10 or 10,001. It will execute line 2 one time.
function isEvenOrOdd(n) {
  return n % 2 ? 'Odd' : 'Even';
}

console.log(isEvenOrOdd(10)); // => Even
console.log(isEvenOrOdd(10001)); // => Odd
// you could also replace n % 2 with the bit AND operator: n & 1. If the first bit (LSB) is 1 then is odd otherwise is even.
```
```csharp
// Look-up table
const dictionary = {the: 22038615, be: 12545825, and: 10741073, of: 10343885, a: 10144200, in: 6996437, to: 6332195 /* ... */};

function getWordFrequency(dictionary, word) {
  return dictionary[word];
}

console.log(getWordFrequency(dictionary, 'the'));
console.log(getWordFrequency(dictionary, 'in'));
```

# O(n)
- A linear-time function/method, scale linearly by the input size
  - Input size: 1 -> Cost: 1
  - Input size: 100 -> Cost: 100
  - Input size: 1000 -> Cost: 1000
  - Input size: 1000000 -> Cost: 1000000
- Examples:
  - Get the max/min value in an array.
  - Find a given element in a collection.
  - Print all the values in a list.
```csharp
// Time complexity of a simple loop when the loop variable is incremented or decremented by a constant amount
int i = 1;
do
  {
      i++;
  }while(i<=n);

// n: Number of times the loop is to be executed.

// find the maximum value from an unsorted array.
function findMax(n) {
  let max;
  let counter = 0;

  for (let i = 0; i < n.length; i++) {
    counter++;
    if(max === undefined || max < n[i]) {
      max = n[i];
    }
  }

  console.log(`n: ${n.length}, counter: ${counter}`);
  return max;
}

// 
int count = 0;
for (int i = N; i > 0; i /= 2) 
    for (int j = 0; j < i; j++) 
        count++;
// When i = N, it will run N times.
// When i = N/2, it will run N/2  times.
// When i = N/4, it will run N/4 times and so on.
```

# O(n^2)
- A quadratic-time function/method, scale quadratic growth relative to the input size
  - Input size: 1 -> Cost: 1
  - Input size: 10 -> Cost: 100
  - Input size: 1000 -> Cost: 1000000
  - Input size: 1000000 -> Cost: 1e+12
- Examples
  - Check if a collection has duplicated values.
  - Sorting items in a collection using bubble sort, insertion sort, or selection sort.
  - Find all possible ordered pairs in an array.


```csharp
//  find duplicate words in an array.
function hasDuplicates(n) {
  const duplicates = [];
  let counter = 0; // debug

  for (let outter = 0; outter < n.length; outter++) {
    for (let inner = 0; inner < n.length; inner++) {
      counter++; // debug

      if(outter === inner) continue;

      if(n[outter] === n[inner]) {
        return true;
      }
    }
  }

  console.log(`n: ${n.length}, counter: ${counter}`); // debug
  return false;
}

// buble sort
function sort(n) {
  for (let outer = 0; outer < n.length; outer++) {
    let outerElement = n[outer];

    for (let inner = outer + 1; inner < n.length; inner++) {
      let innerElement = n[inner];

      if(outerElement > innerElement) {
        // swap
        n[outer] = innerElement;
        n[inner] = outerElement;
        // update references
        outerElement = n[outer];
        innerElement = n[inner];
      }
    }
  }
  return n;
}

// Double nested loop is an indication that you have O(n^2) algorithim
for(int i = 0 ; i<arr.length;i++>)
{
  for(int j = 0; j<arr.length ; j++)
    {
      process(i,j)
    }
}
```
```csharp
// Time complexity of a nested loop.
int i=0;
do{
    do{
        int j =0;
        j++;
      }while(j<=i);
  i++;
  }while(i<=n-1);
// n: Number of times the loop is to be executed.
```

```csharp
int count = 0;
for (int i = 0; i < N; i++)
    for (int j = 0; j < i; j++)
        count++;
```

- Lets see how many times `count++` will run.
  - When i = 0, it will run `0` times.
  - When i = 1, it will run `1` times.
  - When i = 2, it will run `2` times and so on.
  - Total number of times count++ will run is `0+1+2+..+(N-1) = N*(N-1)/2`. So the time complexity will be O(N^2).
- If N = `4`, summ all operations
  - outer loop : 4 times
  - inner loop : 6 times
  - count variable: 6 times
  - Total: `12 times = O(4^2) = O(N^2)`

# O(logN)
- Logarithmic time complexities usually apply to algorithms that `divide problems in half` every time
- A function whose cost scales logarithmically with the input size
  - Input size: 1 -> Cost: 1
  - Input size: 100 -> Cost: 1
  - Input size: 1000 -> Cost: 3
  - Input size: 1000000 -> Cost: 6
- Examples: 
  - Find the word `giraffe` from `aardvark` to `zebra`
    - We can split by cutting problem space in half -> `aardvark` -> `ocelot` -> `zebra`
    - Then continuely cutting problem space in half until get the result.
  - Merge sort, quick sort
- Formula:
  ``` T(n) = a T(n/b) + f(n)  ```
  - T: time complexity function in terms of the input size n.
  - n: the size of the input. duh? :)
  - a: the number of sub-problems. For our case, we only split the problem into one subproblem. So, a=1.
  - b: the factor by which n is reduced. For our example, we divide n in half each time. Thus, b=2.
  - f(n): the running time outside the recursion. Since dividing by 2 is constant time, we have f(n) = O(1).
  ```nlogba```: This value will help us to find which master method case we are solving.
    - For binary search, we have: nlogba = nlog21 = n0 = 1
- If nlogba > f(n) then runtime `O(nlogba)`
- If nlogba === f(n), then runtime `O(nlogba log(n))`
- If nlogba < f(n),`O(f(n))`
```csharp 
// Binary search

function indexOf(array, element, offset = 0) {
  // split array in half
  const half = parseInt(array.length / 2);
  const current = array[half];

  if(current === element) {
    return offset + half;
  } else if(element > current) {
    const right = array.slice(half);
    return indexOf(right, element, offset + half);
  } else {
    const left = array.slice(0, half)
    return indexOf(left, element, offset);
  }
}

// Usage example with a list of names in ascending order:
const directory = ["Adrian", "Bella", "Charlotte", "Daniel", "Emma", "Hanna", "Isabella", "Jayden", "Kaylee", "Luke", "Mia", "Nora", "Olivia", "Paisley", "Riley", "Thomas", "Wyatt", "Xander", "Zoe"];
console.log(indexOf(directory, 'Hanna'));   // => 5
console.log(indexOf(directory, 'Adrian'));  // => 0
console.log(indexOf(directory, 'Zoe'));     // => 18


// Time complexity of a loop when the loop variable is divided or multiplied by a constant amount:
int i=1;
do
{
  i = i*c;
} while(i<=n);
// n: Number of times the loop is to be executed.
```

```csharp
while(low <= high) 
{
    mid = (low + high) / 2;
    if (target < list[mid])
        high = mid - 1;
    else if (target > list[mid])
        low = mid + 1;
    else break;
}
```

# O(m) + O(n)
```csharp
// Time complexity of different loops is equal to the sum of the complexities of individual loop.
int i=1;  
do{  
    i++;  
}while(i<=m);  
  
int j=1;  
do{  
    j++;  
}while(j<=n);  
```

# O(nm)
- A function which has two- inputs that contribute to the growth
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

# O(n^c) - Polynomial time
- Polynomial running is represented as O(nc), when c > 1. As you already saw, two inner loops almost translate to O(n2) since it has to go through the array twice in most cases
## Triple nested loops O(n^3)

```csharp
function findXYZ(n) {
  const solutions = [];

  for(let x = 0; x < n; x++) {
    for(let y = 0; y < n; y++) {
      for(let z = 0; z < n; z++) {
        if( 3*x + 9*y + 8*z === 79 ) {
          solutions.push({x, y, z});
        }
      }
    }
  }

  return solutions;
}

console.log(findXYZ(10)); // => [{x: 0, y: 7, z: 2}, ...]

```
# O(2^n) - Exponential time
- Examples
  - Power Set: finding all the subsets on a set.
  - Fibonacci
  - Travelling salesman problem using dynamic programming.
## Power Set
- To understand the power set, let’s imagine you are buying a pizza. The store has many toppings that you can choose from, like pepperoni, mushrooms, bacon, and pineapple.
- Let’s call each topping A, B, C, D. What are your choices? You can select no topping (you are on a diet ;), you can choose one topping, or two or three or all of them, and so on. The power set gives you all the possibilities (BTW, there 16 with four toppings, as you will see later)
```javascript
function powerset(n = '') {
  const array = Array.from(n);
  const base = [''];

  const results = array.reduce((previous, element) => {
    const previousPlusElement = previous.map(el => {
      return `${el}${element}`;
    });
    return previous.concat(previousPlusElement);
  }, base);

  return results;
}

powerset('') // ...
// n = 0, f(n) = 1;
powerset('a') // , a...
// n = 1, f(n) = 2;
powerset('ab') // , a, b, ab...
// n = 2, f(n) = 4;
powerset('abc') // , a, b, ab, c, ac, bc, abc...
// n = 3, f(n) = 8;
powerset('abcd') // , a, b, ab, c, ac, bc, abc, d, ad, bd, abd, cd, acd, bcd...
// n = 4, f(n) = 16;
powerset('abcde') // , a, b, ab, c, ac, bc, abc, d, ad, bd, abd, cd, acd, bcd...
// n = 5, f(n) = 32;
```
- ** Note:** You should avoid functions with exponential running times (if possible) since they don’t scale well. The time it takes to process the output doubles with every additional input size. But exponential running time is not the worst yet; others go even slower

# O(n!) - Factorial time
- Factorial is the multiplication of all positive integer numbers less than itself. For instance:
```
5! = 5 x 4 x 3 x 2 x 1 = 120
20! = 2,432,902,008,176,640,000
```
- Examples of O(n!) factorial runtime algorithms:
  - Permutations of a string.
  - Solving the traveling salesman problem with a brute-force search

## Permutation

```javascript
function getPermutations(string, prefix = '') {
  if(string.length <= 1) {
    return [prefix + string];
  }

  return Array.from(string).reduce((result, char, index) => {
    const reminder = string.slice(0, index) + string.slice(index+1);
    result = result.concat(getPermutations(reminder, prefix + char));
    return result;
  }, []);
}

getPermutations('ab') // ab, ba...
// n = 2, f(n) = 2;
getPermutations('abc') // abc, acb, bac, bca, cab, cba...
// n = 3, f(n) = 6;
getPermutations('abcd') // abcd, abdc, acbd, acdb, adbc, adcb, bacd...
// n = 4, f(n) = 24;
getPermutations('abcde') // abcde, abced, abdce, abdec, abecd, abedc, acbde...
// n = 5, f(n) = 120;
```

# The order of time complexity
- O(n!) > O(2^n) > O(n^2) > O(n Logn) > O(n) > O(logn) > O(1)

# Time complexity acceptance

| Length of input (N)   |        Worst accepted algorithm |
| --- | -- |
| <= [10..11]            |          O(N!), O(N^6) |
| <= [15..18]           |           O(2^N * N^2) |
| <= [18..22]           |           O(2^N * N)        |                
| <= 100                |           O(N^4) |
| <= 400                |           O(N^3) |
| <= 2K                |            O(N^2 * logN) |
| <= 10K               |            O(N^2) |
| <= 1M                |            O(N * logN) |
| <= 100M              |            O(N), O(logN), O(1) |

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

# Why study algorithms

Their impact is broad and far-reaching.

- Internet. Web search, packet routing, distributed file sharing, ...
- Biology. Human genome project, protein folding, ...
- Computers. Circuit layout, file system, compilers, ...
- Computer graphics. Movies, video games, virtual reality, ...
- Security. Cell phones, e-commerce, voting machines, ...
- Multimedia. MP3, JPG, DivX, HDTV, face recognition, ...
- Social networks. Recommendations, news feeds, advertisements, ...
- Physics. N-body simulation, particle collision simulation, ...
