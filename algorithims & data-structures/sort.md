# Intro

- Comparisons: When two values in the array being sorted are compared for
  relative equality
- Swaps: When two values in the array being sorted exchange places

# Measuring Performance

- Comparisons and swaps are expressed using Big-O notation
- The actual cost of either operation depends on multiple factors
- Reducing either operation can improve performance

# Bubble sort

- Complexity:

  - Worst: O(n²)
  - Average: O(n²)
  - Best: O(n)
  - Memory: O(1).
    Steps:

- Iterate: Visit each item in the array from the start to the end
  Bubble Sort
- Swap: If two neighboring items are out of order, swap them
- Repeat: Repeat this process until the array is sorted
- Conclusion: Bubble Sort’s O(n2) average case makes it a poor general-purpose sorting algorithm

```csharp
void SortAsc() {
  // [5,1,3,6,7]
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

// optimization
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

```csharp

void MergeSort(int[] arr){

  if(arr.length == 1)
  {
    return arr;
  }
  var middle = arr.length / 2;
  var left = arr.CopyTo(0,middle)
  var right = arr.CopyTo(middle,arr.length);
  MergeSort(left);
  MergeSort(right);
  return Merge();
}
void Merge(int[] items, int[] left, int[] right){
  var remaining = items.length;
  var leftIndex = 0, rightIndex = 0;
  while(remaining > 0)
  {
    if(leftIndex >= left.Length)
    {
      items[rightIndex] = right[rightIndex++];
    }
    else if(rightIndex >= right.Length)
    {
      items[leftIndex] = left[leftIndex++];
    }
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
