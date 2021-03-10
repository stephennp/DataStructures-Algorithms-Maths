# Linear Search

- Scan the array, from start to end, comparing each array item against the value
  being sought

```csharp
public bool Search(int[] data, int value) {
  for(int i = 0; i < data.Length; i++) {
      if(data[i] == value) {
          return true;
      }
  }
  return false;
}
```

## Performance O(n)

- Linear search performance: Linear searching must examine each array item until the value is found giving it O(n) algorithmic complexity

# Binary Search

- Starting with a sorted array, check the middle array value.
- If the value is a match, then the value has been found.
- If the value is greater than the sought value, repeat this process for the values to the left, otherwise for the values to the right.

```csharp
// 1 2 3 4 5 9 11 13
// 7 /2 = 3.5 ~ 3(index)
// 4 > 2 -> range 0 ~ 2(3- 1)
// -> 2/2 = 1 -> 2 > 1 -> 1 - 1 = 0 (start=end)
public bool Search(int[] data, int value) {
  int start = 0;
  int end = data.Length - 1;
  while (start <= end) {
    int middle = (start + end) / 2;
    if (data[middle] == value)
      return true;
    // If the value is greater than the array index… Cut the range in half by increasing start
    // Cut the range in half by increasing start
    else if (data[middle] < value)  
      start = middle + 1;
    // Else cut the range in half by decreasing end
    else 
      end = middle - 1;
  }
  return false;
}
```
## Performance O(log n)
- Binary search is a divide-and conquer algorithm giving it `O(log n)` algorithmic complexity