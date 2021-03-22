# Intro

- A tree-based container type that provides `O(1)` access to the minimum (min-heap) or maximum (max-heap) value while satisfying the heap property.

# Complexity

- Building MAX HEAP: O(N)
  - `max_heapify` function has complexity and the build_maxheap functions runs only times, but the amortized complexity for this function is actually linear.

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

# Push

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
4
8 4
8 4 1
8 7 4 1
8 7 4 3 1

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

# Psuedo code

```csharp
class Heap<T>{
  int Capacity;
  int Count;
  T[] Data;

  // Complexity: O(logN)
  /*
       8                8               8
    7     4     =>    7    4   =>    7     6
  3   1             3   1 6         3  1 4   
  */
  void Push(T Value){
    Data[count] = value;
    int index = Count;
    while(index >0 && value < arr[parent(index)])
    {
        swap(Data[parent(index)],Data[index]);
        i = parent(i);
    }
    Count ++
  }
  
  // Complexity: O(logN)
  void Pop(){
      if(Count ==0)
      {
        throw new Exception("Empty heap.")
      }

      Data[0] = Data[Count - 1];

      Count = Count - 1;

      MaxHeapify(Data,0,Count);
  }

  // Complexity: O(N)
  // Build max heap every sub-tree
  /*
       1                1                1
    4     3     =>    4    10   =>    8    10
  7   8 9   10      7   8 9   3     7   4 9   3
  => 
      10                10               
    8     1     =>    8    9   
  7   4 9   3      7   4 1   3     
  */
  void BuildMaxHeap(int[] arr, int N){
      for(int i = N/2 - 1; i>= 0 ; i--)
      {
          MaxHeapify(array,i, N);
      }
  }

  // Complexity : O(logN)
  // Replace the highest value will be the root node of tree
  // N :total of elements
  /*
        4                8                8
    7       8   =>    7     4     =>  7       6
  3   2   6   6     3   2 6   6     3   2    4  5
  */
  void MaxHeapify(int[] array, int i, int N){
    int left = Left(i);
    int right = Right(i);
    int largest;
    if(left < N && array[left] > array[i])
    { 
      largest = left;
    }
    else
    {
      largest = i;
    }

    if(right < N && array[right] > array[i])
    {
      largest = right;
    }

    if(largest != i)
    {
      swap(array[i], array[largest])
      MaxHeapify(array, largest, N);
    }
  }

  // BuildMaxHeapify : O(N)
  // MaxHeapify: O(logN)
  // Complexity: O(NLogN)
  void SortAsc(int[] arr, int N){
    int heapSize = N;
    BuildMaxHeapify(arr, 0, N);
    for(int i =N; i >=1 ; i--)
    {
      swap(arr[0], arr[N -1]);
      heapSize --;
      MaxHeapify(arr, 0, heapSize);
    }
  }
  int Left(int i)
  {
    return i * 2 + 1;
  }
  int Right(int i)
  {
    return i * 2 + 2;
  }
  int Parent(int i)
  {
    return (i - 1) /2;
  }

  T Top(){
    if(Count == 0)
    {
      throw new Exception("Empty heap.")
    }
    return Data[0];
  }
}
```
