
# Quick sort

- Pivot: Pick the pivot value in the array
- Partition: Reorder the elements around the pivot point
- Repeat: Repeat for each partition

## Complexity
- Best: `O(n log n)` comparisons and swaps
- Average: `O(n log n)` comparisons and swaps
- Worst: `O(n^2)` comparisons and swaps
- Memory: `O(log n)`

## Properties
- Divide and Conquer: Reduces the problem down to the most basic form
- In-place: Requires only `O(log n)` additional memory
- Optimizable: There exist many optimizations to improve performance
- Quicksort is the `default sorting algorithm` for many programming languages
## Pivot value

- A value in the array where all the values to the left of the pivot are less than (or equal to) the pivot value, and all the values to the right are greater.

## Steps

- Selecting a Pivot Value
  - Select a random array item
  - Select the first or last array item
    - Requires `O(n^2)` operations in the pre-sorted case
  - Select the median of the first, last, and middle items

```csharp
// 10, 90, 30, 45, 80, 50, 12, 70 => pivot = 45
// => i = 0, storeIndex = 0 > 10, 90, 30, 70, 80, 50, 12, 45 => 
// => i = 2, storeIndex = 1 > 10 , 30 ,90, 70, 80, 50, 12, 45 => swapped => storeIndex = 2
// => i = 5, storeIndex = 2 > 10, 30 , 12, 70, 80, 50, 90, 45 => swapped => storeIndex = 3
// => 10 , 30, 12, 45, 80, 50, 90, 70
// repeat with pivotIndex = 4, left = (0, pivot-1), right = (pivot+1, end)
void quickSort(int[] items, int left, int right){

  if(left < right)
  {
    var pivot = partition(items,left,right);
    // divide and conquer left items without pivot index
    quickSort(items, left, pivot -1);

    // divide and conquer right items without pivot index
    quickSort(items, pivot + 1,right);
  }
}

int partition(int[] items, int left, int right)
{
  // get random pivot
  var newPivot = items.Range(left,right);

  // swap random pivot to last item index of array
  swap(items,newPivot,right);

  var storedIndex = left;

  // compare and swap
  for(int i = left; i < items.length; i++)
  {
    if(items[i] < newPivot)
    {
      swap(items,i,storedIndex);
      storedIndex++;
    }
  }
  // finallly swap and get the new pivot index
  swap(items,right,storedIndex)
  return storedIndex;
}

```

# Comparison
```
Executing: Bubble Sort
       Length: 20000
  Comparisons: 395540222
        Swaps: 100128488
      Seconds: 14.1925947
------------------
Executing: Insertion Sort
       Length: 20000
  Comparisons: 100168467
        Swaps: 100128488
      Seconds: 4.2475366
------------------
Executing: Merge Sort
       Length: 20000
  Comparisons: 260844
        Swaps: 287232
      Seconds: 0.0143705
------------------
Executing: Quick Sort
       Length: 20000
  Comparisons: 332064
        Swaps: 180894
      Seconds: 0.0116324
------------------
```