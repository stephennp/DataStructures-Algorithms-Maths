# Implementation
Complexity: O(N^2)
```python
def sort(arr):
  # reduces the effective size of the array by one in  each iteration.
  for i in range(len(arr) - 1):
    # temporary variable to store the position of minimum element
    min = i
    # gives the effective size of the unsorted  array .
    for j= i+1 in range(len(arr))
      if(arr[j] < arr[min]):
        min = j
  # putting minimum element on its proper position.
  swap(arr[i], arr[min])

```