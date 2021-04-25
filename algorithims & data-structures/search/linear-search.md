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
