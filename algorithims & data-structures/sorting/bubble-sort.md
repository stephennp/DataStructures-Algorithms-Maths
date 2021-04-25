# Bubble sort

- Complexity:

  - Worst: `O(n²)`
  - Average: `O(n²)`
  - Best: `O(n)`
  - Memory: `O(1)`.

- Steps:

- Iterate: Visit each item in the array from the start to the end
  Bubble Sort
- Swap: If two neighboring items are out of order, swap them
- Repeat: Repeat this process until the array is sorted
- Conclusion: Bubble Sort’s O(n^2) average case makes it a poor general-purpose sorting algorithm

```csharp
void SortAsc() {
  // [5,3,1]
  // loop 1(i = 0): [3,1,5]
  // loop 2(i = 1): [1,3,5]
  // loop 3(i = 2): [1,3,5]
  do
  {
    swap = false;
    for(int i = 1; i<arr.length; i++)
    {
      if(arr[i - 1].CompareTo(arr[i]) > 0)
      {
        arr[i] = arr[i -1];
        arr[i - 1 ] = arr[i]
        swap = true;
      }
    }
  } while(swap)
}

// Optimization
void SortAsc(){
  var swap;
  for(int i = 1; i< arr.length; i++)
  {
    swap = false;
    for(int j = 0; i< arr.length - i; j++)
    {
      if(arr[j] > arr[i])
      {
        var temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
        swap = true;
      }
    }
  }

  // If there were no swaps then array is already sorted and there is
  // no need to proceed.
  if (!swapped) {
    return arr;
  }
  return arr;
}
```