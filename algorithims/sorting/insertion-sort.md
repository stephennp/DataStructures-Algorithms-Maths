
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