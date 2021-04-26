# Intro

- Comparisons: When two values in the array being sorted are compared for
  relative equality
- Swaps: When two values in the array being sorted exchange places

# Measuring Performance

- Comparisons and swaps are expressed using Big-O notation
- The actual cost of either operation depends on multiple factors
- Reducing either operation can improve performance

# Bubble sort

- Is one of the simplest sorting algorithms
  - It is based on a repeated swap between adjacent elements if they are in wrong order. It is stable
- This algorithm is almost `never` used because of its O(N²) time complexitiy. But in computer graphics, it is popular to detect a very small error (like swap of two elements) in almost sorted array.


- Complexity:

  - Worst: `O(n²)`
  - Average: `O(n²)`
  - Best: `O(n)`
  - Memory: `O(1)`.
  - Stable: yes

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

# Insertion sort

- Complexity:
  - Best: O(n) comparisons and swaps Insertion Sort Asymptotic Analysis
  - Average: O(n^2) comparisons and swaps
  - Worst: O(n^2) comparisons
    and swaps
- Steps:
  - Iterate: Visit each item in the array from the start to the end
  - Compare: Find out of order neighboring items
  - Shift and Insert: Find the insertion point, shift, and insert

```csharp
void sort(){
  for(int i = 1 ; i < arr.length; i++ )
  {
    if(arr[i - 1] > arr[i])
    {
      for(int j = i; j> 0 ; j --)
      {
        if(arr[j-1] > arr[j])
        {
          var temp = arr[j-1];
          arr[j-1] = arr[j];
          arr[j] = temp;
        }
      }
    }
  }
}
```

- Another solution:

```javascript
sort(originalArray) {
    const array = [...originalArray];

    // Go through all array elements...
    for (let i = 0; i < array.length; i += 1) {
      let currentIndex = i;

      // Call visiting callback.
      this.callbacks.visitingCallback(array[i]);

      // Go and check if previous elements and greater then current one.
      // If this is the case then swap that elements.
      while (
        array[currentIndex - 1] !== undefined &&
        this.comparator.lessThan(array[currentIndex], array[currentIndex - 1])
      ) {
        // Call visiting callback.
        this.callbacks.visitingCallback(array[currentIndex - 1]);

        // Swap the elements.
        [array[currentIndex - 1], array[currentIndex]] = [
          array[currentIndex],
          array[currentIndex - 1],
        ];

        // Shift current index left.
        currentIndex -= 1;
      }
    }

    return array;
  }
```

- Conclusion:
  - Adaptive: Works well when the data is nearly sorted Insertion Sort Use Cases
  - In-place: Requires only O(1) additional memory
  - Online: Sorting can occur as the data is received

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
  return Merge();
}

void Merge(int[] items, int[] left, int[] right){
  var remaining = items.length;
  var leftIndex = 0, rightIndex = 0;
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
// 10 30 90 80 85 12 70 
// compare to 70(pivot): storeIndex = 2, index = 5
// -> 10 30 12 70 85 90 80
// sub sorting left: 10 30 12
// sub sorting right: 85 90 80
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