# Intro
- The time complexity is O(N + k) where k is the largest integer present in the input array. This algorithm is only used when the input array's length is very very high and the largest element (k) present in the array is smaller than the length of array (N). For example, sort an array of length around a billion containing age of people
- It is basically using the frequency of each element (a kind of hashing)
- Determining the minimum and maximum value and then iterating between them to place each element based on its frequency.
- It is efficient if the range of input is not significantly greater than the number of elements.
- Time complexity: O(n+k) where n is the number of elements in input array and k is the range of input.
- Space complexity:O(n+k)
# Implementation
.
- Complexity: O(N+K)
  - N is the number of elements in input array 
  - K is the range of input.
```python
# arr = [3,5,1,2,6,2]
# count = [0,1,2,3,4,5,6...256] = [0,1,2,1,0,1,1] => summ acc => [0,1,3,4,4,5,6]
# output index = [0,1,2,3,4,5] => get value of summ account to indexing of output => [1,2,2,3,5,6]
def sort(arr):

  count = [0 for i in range(256)]:
    
  for i in arr
    count[ord(i)] += 1

  for i in range(256):
    count[i] += count[i-1]

  for i in range(len(arr)):
    output[count[ord(arr[i])]]
    countount[ord(arr[i])] = -1 

sort("mortalkombat")
```