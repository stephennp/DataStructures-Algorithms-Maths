
# Merge sort

- Split: Split the array into sub-arrays of a single item
- Compare: Compare the individual items
- Merge: Merge the items into a sorted array


## Complexity

- Best: `O(n log n)` comparisons and swaps
- Average: `O(n log n)` comparisons and swaps
- Worst: `O(n log n)` comparisons and swaps
- Memory: `O(n)`

## Properties
- Merge sort has uniform algorithmic complexity in the worse, average, and best case
- Divide and Conquer: Reduces the problem down to the most basic form
- Memory Requirements: Requires `O(n)` additional memory
- Stable: Equal items retain their relative position

```csharp
// 1 3 5 1 - > (4 swap) + (1 recursion)
// 1 3   5 1 - > 1 3 (1 swap)  1 5 (1 swap) + (1 recursion)
// 1  3  5   1
// total : 8 operations = O(n * logn)
void MergeSort(int[] arr){

  if(arr.length == 1)
  {
    return arr;
  }
  var middle = arr.length / 2;
  var left = arr.CopyTo(0,middle)
  var right = arr.CopyTo(middle,arr.length);
  // sort the 1st part of array .
  MergeSort(left);
  // sort the 2nd part of array.
  MergeSort(right);
 // merge the both parts by comparing elements of both the parts
  return Merge(arr,left,right);
}

void Merge(int[] items, int[] left, int[] right){
  var remaining = items.length;
  // why set index = 0, because we useeee postorder traversal,
  // that make sure the last leaf will firstly traversal from left -> right
  var index = 0, leftIndex = 0, rightIndex = 0;
  while(remaining > 0)
  {
    //checks if first part comes to an end or not .
    if(leftIndex >= left.Length)
    {
      items[rightIndex] = right[rightIndex++];
    }
    //checks if second part comes to an end or not
    else if(rightIndex >= right.Length)
    {
      items[leftIndex] = left[leftIndex++];
    }
    //checks which part has smaller element.
    else if(left[leftIndex] < right[rightIndex])
    {
      items[index] = left[leftIndex++];
    }
    else{
      items[index] = right[rightIndex++];
    }
    remaining --;
    index ++ ;
  }
}
```
