# Fenwick (Binary Indexed) Trees
- Binary Indexed Tree also called `Fenwick Tree` provides a way to represent an array of numbers in an array, allowing prefix sums to be calculated efficiently. For example, an array `[2, 3, -1, 0, 6]` is given, then the prefix sum of first 3 elements `[2, 3, -1] is 2 + 3 + -1 = 4`. Calculating prefix sum efficiently is useful in various scenarios. Let's start with a simple problem.

- Given an array , and two types of operations are to be performed on it.
  - Change the value stored at an index i. (This is called a point update operation)
  - Find the sum of a prefix of length k. (This is called a range sum query)
  - A straightforward implementation of the above would look like this.
```csharp
int a[] = {2, 1, 4, 6, -1, 5, -32, 0, 1};
void update(int i, int v)   //assigns value v to a[i]
{
    a[i] = v;   
}
int prefixsum(int k)    //calculate the sum of all a[i] such that 0 <= i < k
{
   int sum = 0;
   for(int i = 0; i < k; i++)
        sum += a[i];
   return sum;
}
```
- This is a perfect solution, but unfortunately, the time required to calculate a prefix sum is proportional to the length of the array, so this will usually `time out when large numbers` of such intermingled operations are performed.

- One efficient solution is to use `segment tree` that can perform both operations in  time.

- Using binary Indexed tree also, we can perform both the tasks in `O(logN)` time. But then why to learn another data structure when segment tree can do the work for us. It’s because binary indexed trees require `less space` and are very easy to implement during programming contests (the total code is not more than `8-10 lines`).

- Before starting with the binary indexed tree, have a look at a particular bit manipulation trick.

# Isolating the last set bit
- Example: x = `1110` (in binary)
| Binary digit | 1 | 1 | 1 | 0 |
| -- | -- | -- | -- | -- |
| Index | 3 | 2 | 1 | 0 |

# Psudo code

```csharp
   {2, 1, 1, 3, 2, 3,  4, 5, 6, 7, 8, 9} 

=> index in BIT {1, 2, 3, 4, 5, 6, 7, 8,9, 10, 11, 12}

=> convert {2, 3, 1, 7, 2, 5, 4, 21, 6, 13, 8, 30}

use: split right most bit 
0 = 0000
1 = 0001 => 0000
2 = 0010 => 0000
8 = 1000 => 0000
4 = 0100 => 0000


3 = 0011 => 0010 (2)
5 = 0101 => 0100 (4)
6 = 0110 => 0100 (4)
7 = 0111 => 0110 (6)
9 = 1001 => 1000 (8)
10 = 1010 => 1000
11 = 1011 => 1010
12 = 1100 => 1000
=>
index=			0
		(0,0)  (0,1)	(0,3)			  (0,7)
		 1[2]   2[3]	 4[7]   		  8[21]		
		 
		 (2,2)			 (4,0) (4,1)    (8,0) (8,1)   (8,3)
		  3[1]	 		  5[2] 6[5]      9[6] 10[13]   12[30]
							    (6,0)		  (10,0)
						        7[4]		  11[8]
	
1 = 0 + 2^0 = [0,0]
2 = 0 + 2^1 = [0,1] -> 0 to next 2
  => 3 = 2^ 1 + 2^0 = [2,2] -> 2 to next 2
4 = 0 + 2^ 2 = [0,3] -> 0 to next 4
5 = 2^2 + 2^0 = [4,0] -> 4 next to 1
6 = 2^2 + 2^1 = [4,1] -> 4 next to 2
7 = 2^3 + 2^0 = [6,0] -> 6 next to 1
8 = 0+ 2^3 = [0,7] -> 0 next to 8
9 = 2^3 + 2^0 = [8,0] -> 8 next to 1
10 = 2^3 + 2^1  = [8,1]-> 8 next to 2
11 = 2^3 + 2^1 + 2^0 = [10,1] -> 10 next to 1
12 = 2^3 + 2^2 = [8,3] -> 8 next to 4
```