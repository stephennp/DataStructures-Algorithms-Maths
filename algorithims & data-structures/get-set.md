# Set

- A data structure that stores unique values in an
  undetermined order.

## Properties

- Contains only distinct items
- Items are iterated in an implementation-defined order
- Set operations are O(log n)

## Examples

Name Values
Integers … -4, -3, -2, -1, 0, 1, 2, 3, 4 …
Positives 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 …
Negatives … -7, -8,-6, -5, -4, -3, -2, -1
Evens 0, 2, 4, 6, 8, 10, 12, 14, 16, …
Odds 1, 3, 5, 7, 9, 11, 13, 15, 17, …

Name Values
Teams “LA Galaxy”, “Portland Timbers”, …
Players “Diego Valeri”, “Ike Opara”, …

```csharp
public interface ISet<T> : IEnumerable<T>    // Set interface is enumerable
where T: IComparable<T>                      //  Set type must be comparable
{
    bool Add(T value);                      // Basic container operations
    bool Remove(T value);
    bool Contains(T value);
    int Count { get; }
    ISet<T> Union(ISet<T> other);                // Set algebra operations
    ISet<T> Intersection(ISet<T> other);
    ISet<T> Difference(ISet<T> other);
    ISet<T> SymmetricDifference(ISet<T> other);
    }
```

```csharp
public class Set<T> : ISet<T>   // Set type implements ISet interface
where T : IComparable<T>
{
    private readonly AVLTree<T> _store;  // AVL tree used as backing store
    public Set()
    {
        _store = new AVLTree<T>(); // Empty tree created in empty ctor
    }
    public Set(IEnumerable<T> values)  // Constructor for adding existing values
    : this()
    {
        AddRange(values);
    }

public bool Add(T value) {
    if (!_store.Contains(value)) {  //Items are only added if they are not already in the set.
        _store.Add(value);
        return true;  // Returns true if the item was added
    }
  return false; // False otherwise
}
private void AddRange(IEnumerable<T> values) { // Private method to help add multiple items
  foreach (T value in values) {
    Add(value);
  }
}

public bool Contains(T value) {  //Checks if the value is in the set
  return _store.Contains(value);
}
public bool Remove(T value) { // Removes a value from the set (if it exists)
  return _store.Remove(value);
}
public int Count { // Removes a value from the set (if it exists)
  get {
    return _store.Count;
  }
}
public IEnumerator<T> GetEnumerator() { // IEnumerable<T> methods defer to the AVL tree for enumeration. This AVL tree defaults to in-order traversal
return \_store.GetEnumerator();
}
IEnumerator IEnumerable.GetEnumerator() {
return \_store.GetEnumerator();
}
```

# Union

- The set of all distinct items that exist within any of the input sets Union

## Union “or” Questions

Which players have played for the Sounders or and Galaxy?
Union “or” Questions
Which students are in Algebra or Biology?
What books are available at the library or the bookstore?
What animals are birds or mammals?

```
Set<Player> sounders = players.Where(p => p.Team == ”Sounders");
Set<Player> galaxy = players.Where(p => p.Team == ”Galaxy");
Set<Player> either = galaxy.Union(sounders);
```

## Union Algorithm

- Create an output set that contains the distinct items from both input sets

```csharp
public ISet<T> Union(ISet<T> other) {
  Set<T> result = new Set<T>(other);
  result.AddRange(_store);
  return result;
}
yield return new object[]{ new TestCaseData<int>
{
   Left = new int[] { 1, 2, 3, 4 },
   Right = new int[] { 5, 6, 7, 8 },
   Expected = new int[] { 1, 2, 3, 4, 5, 6, 7, 8 }
  } };
 yield return new object[]{  new TestCaseData<int>
  {
    Left = new int[] { 1, 2, 3, 4 },
    Right = new int[] { 1, 2, 3, 5 },
    Expected = new int[] { 1, 2, 3, 4, 5 },
    } };
 yield return new object[]{  new TestCaseData<int>
  {
    Left = new int[] { 1, 2, 3, 4 },
    Right = new int[] { },
    Expected = new int[] { 1, 2, 3, 4 }
 } };
 yield return new object[]{  new TestCaseData<int>
  {
    Left = new int[] { },
    Right = new int[] { 1, 2, 3, 4 },
    Expected = new int[] { 1, 2, 3, 4 }
  } };
 yield return new object[]{  new TestCaseData<int>
 {
  Left = new int[] { },
  Right = new int[] { },
  Expected = new int[] { }
 } };
```

# Intersection

- The of items that exist within both input sets

```
Biology          Algebra
Ahmed             Lucy
Sarah             Michael
David             Sarah
Divyang           Mia
Candice           Divyang
                  Ahmed
                  Intersection

Result:
Ahmed
Sarah
Divyang
```

## Intersection answers “AND questions

Which players have played for the Sounders and Galaxy?
Which students are in Algebra and Biology?
What books are available at the library and the bookstore?
What animals are birds and mammals?

```csharp
Set<Player> sounders = players.Where(p => p.Team == ”Sounders");
Set<Player> galaxy = players.Where(p => p.Team == ”Galaxy");
Set<Player> both = galaxy.Intersection(sounders);
```

```csharp
ISet<T> Intersection(ISet<T> other) { // Accepts the set to intersect with
  ISet<T> result = new Set<T>(); //Create an empty result set
  foreach (T item in other) { //If an item is in the current set and in the other set
    if (Contains(item)) {
      result.Add(item); //Add it to the result set
    }
  }
return result; // Return the set of intersecting items
}

     public IEnumerator<object[]> GetEnumerator()
        {
            yield return new object[]{ new TestCaseData<int>
                {
                    Left = new int[] { 1, 2, 3, 4 },
                    Right = new int[] { 5, 6, 7, 8 },
                    Expected = new int[] {  }
                }};
            yield return new object[]{ new TestCaseData<int>
                {
                    Left = new int[] { 1, 2, 3, 4 },
                    Right = new int[] { 1, 2, 5, 6 },
                    Expected = new int[] { 1, 2 }
                }};
            yield return new object[]{ new TestCaseData<int>
                {
                    Left = new int[] { 1, 2, 3, 4 },
                    Right = new int[] { },
                    Expected = new int[] { }
                }};
            yield return new object[]{ new TestCaseData<int>
                {
                    Left = new int[] { },
                    Right = new int[] { 1, 2, 3, 4 },
                    Expected = new int[] { }
                }};
            yield return new object[]{ new TestCaseData<int>
                {
                    Left = new int[] { },
                    Right = new int[] { },
                    Expected = new int[] { }
                } };

```

## Difference

- The set of items which exist in one set which do not exist in the other.
- Difference answers “BUT NOT” questions for a single input set

## Properties

- Which players have played for the Sounders but not Galaxy
- Difference “but not” Question
- Which students are in Algebra but not Biology?
- What books are available at the library but not the book
- What animals are birds but not mammals?

```csharp
ISet<T> Difference(ISet<T> other) {
  ISet<T> result = new Set<T>(_store);
  foreach (T item in other)
  {
    result.Remove(item);
  }
  return result;
}
public IEnumerator<object[]> GetEnumerator()
        {
            yield return new object[] {new TestCaseData<int>
            {
                Left = new int[] { 1, 2, 3, 4 },
                Right = new int[] { 5, 6, 7, 8 },
                Expected = new int[] { 1, 2, 3, 4 }
            } };
            yield return new object[] {new TestCaseData<int>
            {
                Left = new int[] { 1, 2, 3 },
                Right = new int[] { 1, 7, 8 },
                Expected = new int[] { 2, 3 }
            }};
            yield return new object[] {new TestCaseData<int>
            {
                Left = new int[] { 1, 2, 3, 4 },
                Right = new int[] { 1, 2, 5, 6 },
                Expected = new int[] { 3, 4 }
            }};
            yield return new object[] {new TestCaseData<int>
            {
                Left = new int[] { 1, 2, 3, 4 },
                Right = new int[] { },
                Expected = new int[] { 1, 2, 3, 4 }
            }};
            yield return new object[] {new TestCaseData<int>
            {
                Left = new int[] { },
                Right = new int[] { 1, 2, 3, 4 },
                Expected = new int[] { }
            }};
            yield return new object[] {new TestCaseData<int>
            {
                Left = new int[] { },
                Right = new int[] { },
                Expected = new int[] { }
            } };
        }
```

# Symmetric Difference
- The set of items which exist in either of the two input sets, but which are not in their intersection.
- Symmetric Difference answers “OR … BUT NOT BOTH” questions

```csharp
ISet<T> SymmetricDifference(ISet<T> other) { // Accepts the set to symmetric difference
  ISet<T> ntr = Intersection(other); //  Intersects with the input set
  ISet<T> union = Union(other); // Union with the other set
  return union.Difference(ntr); // Returns the difference of the union and the
intersection
}
```