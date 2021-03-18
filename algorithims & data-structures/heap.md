# Intro
- A tree-based container type that provides `O(1)` access to the minimum (min-heap) or maximum (max-heap) value while satisfying the heap property.
# Complexity
- Building MAX HEAP: O(N) 
  -  `max_heapify` function has complexity  and the build_maxheap functions runs only  times, but the amortized complexity for this function is actually linear.
# Heap Property

- The value in the current tree node is greater than, or equal to, its children `(max-heap)`.

```
- Max-heap
        8
    5       6
  4   2   1   3

- Min-heap
        1
    3       2
  8   4   5   6
```

# Complete Tree
- A tree where every level is filled out from left-to-right be starting the next level.

```
- complete tree

        8
    5       6
  4   2   1   3

- imcomplete tree

        8
          6

        8
      5   6
    4   1   

        8
      5
    4   2
```

# Trees as Arrays
- Complete binary trees can be compactly stored as arrays eliminating all structural overhead and providing `O(1)` data access.
```
            0
      1         2
    3   4     5   6
  7 8   9 10

- Array: 0 1 2 3 4 5 6 7 8 9 10

Index:   0 1 2 3 4  5  6  7  8  9  10
Parent:  x 0 0 1 1  2  2  3  3  4  4
Left:    1 3 5 7 9  11 13 15 17 19 21
Right:   2 4 6 8 10 12 14 16 18 20 22
```
```csharp
int parent(const int index) {
  return (index - 1) / 2;
}
int left(const int index) {
  return 2 * index + 1;
}
int right(const int index) {
  return 2 * index + 2;
}
```
# Heap Operations
- Adding values (push)
- Retrieving min or max value (top)
- Removing min or max value (pop)

#  Push
- Adds an item to the heap, placing it in the first valid position that retains the tree rules.
  - Add the new value to the end of the heap array
  - While the heap property is not satisfied, swap the new item with its parent

```
      8
  5       6
4   2

- Add new value to end of heap: 9

      8
  5       6
4   2   9

- While the heap property is not satisfied, swap with parent

      8
  5       9 
4   2   6

- Do it until satisfied
      9
  5       8
4   2   6
```
# Top
- Returns the first item (min or max) in the heap.
```csharp
public T Top() {
  if (Count > 0) {
    return data[0];
}
  throw new Exception("Top called on empty heap");
}
```

# Pop
- Removes the top item from the heap, moving the replacement item into the first valid position in the heap tree.
  - Move the last item in the heap array into the zero (root) index
  - While the heap property is not satisfied, swap the item with one of its children

```
- Step 1: Replace top value with right-most child

        9
    5       8
  4   2   6

->
        6
    5       8
  4   2  
- Step 2: Swap new top with children until heap property is satisfied 
        5
    6       8
  4   2  

->
        6
    5       8
  4   2 
->
        8
    5       6
  4   2 
```

# Priority Queue
- A queue that pops item in priority, not FIFO, order.

```
urgent->job1->job2->job3->job4
->
job1->job2->job3->job4->urgent

```

```csharp
public class PriorityQueue<T> {
  readonly Heap<T> heap = new Heap<T>();
  public void Enqueue(T value) {
    heap.Push(value);
  }
  public T Deque() {
    T value = heap.Top();
    heap.Pop();
    return value;
  }
}
```