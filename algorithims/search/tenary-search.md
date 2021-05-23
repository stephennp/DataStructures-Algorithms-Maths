# Intro
- Ternary search, like binary search, is a divide-and-conquer algorithm. It is mandatory for the array (in which you will search for an element) to be sorted before you begin the search. In this search, after each iteration it neglects ⅓ part of the array and repeats the same operations on the remaining ⅔
.
# Implementation
- Complexity O(Log(1/3)N), where N is the size of the array
```python

def tenarySearch(l, r, key ,arr):
  if(r>=l):
    mid1 = l + (r-l)/3
    mid2 = r - (r-l)/3

    if (arr[mid1] == key):
      return return arr[mid1]
    if (arr[mid2] == key):
      return arr[mid2]
    if (key < arr[mid1]):
      return tenarySearch(l,mid1-1,key,arr)
    elif(key > arr[mid2]):
      return tenarySearch(mid2+1,r,key,arr)
    else:
      return tenarySearch(mid1+1, mid2-1, key, arr)
```
