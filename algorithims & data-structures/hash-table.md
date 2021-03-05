# Intro

- A collection of key/value pairs where the key can only exist once in the collection
- Examples:
  - HTTP headers
    - Request URL
    - Response Body
    - Browser version
    - Referrer
  - Application configs
  - Environment Variables
  - Key/Value database

# HTTP headers

- The header name and value become the key and value in the associative array

```javascript
HttpHeader headers;
headers["content-length"] = "8056";
headers["content-type"] = "image/png";
```

# Complexity

- An associative array container that provides `O(1) insert, delete and search` operations.

# Hash table

## Hash Collision

- When multiple distinct keys would be inserted at the same hash table index.

## Separate Chaining

- Collisions in a hash table are chained together into a linked list whose root node is the hash table array entry

## Fill Factor

- The percentage of capacity representing the maximum number of entries before the table will grow. E.g., 0.80

## Growth Factor

- The multiple to increase the capacity of the hash table when the fill factor has been exceeded. E.g., 1.50

## Hash Table Growth

- Use the fill factor to determine if growth is needed
- Use the growth factor to allocate a larger array
- Determine the new index for the existing items in the hash table
- Update the hash table to use the new array

```csharp
class HashTableNodePair<TKey,TValue>{

  public HashTableNodePair(TKey key, TValue value)
  {
    Key = key;
    Value = value;
  }
  public TKey Key {get;set;}
  public TValue Value {get;set;}
}
class HashTableArrayNode<TKey,TValue>
{
   LinkedList<HashTableNodePair<TKey,TValue>> _items;

   void Add(TKey key, TValue value) {
     if(_items == null)
     {
       _items = new LinkedList<HashTableNodePair<TKey,TValue>>();
     }
     else
     {
       for(var item in _items)
       {
         if(item.Key.Equals(key))
         {
           throw new ArgumentExpcetion("The collection already contains the key");
         }
       }
       _items.AddHead(new HasTableNodePair<TKey,TValue>(key, value));
     }
   }

   void Update(){
     bool updated = false;
     for(var item in _items)
     {
       if(item.Key.Equals(key))
       {
         item.Value = value;
         updated = true;
         break;
       }
     }
     if(!updated)
     {
        throw new ArgumentExpcetion("The collection already contains the key");
     }
   }

   void Remove(){
       bool removed = false;
            if (_items != null)
            {
                HashTableNodePair<TKey, TValue> found = null;
                foreach(HashTableNodePair<TKey, TValue> current in _items)
                {
                    if(current.Key.Equals(key))
                    {
                        found = current;
                        break;
                    }
                }

                if(found != null)
                {
                    _items.Remove(found);
                    removed = true;
                }
            }

            return removed;
   }
}
class HashTableArray<TKey,TValue>
{
  HashTableArrayNode<TKey,TValue>[] _array;

  public HashTableArray(int capacity)
  {
    _array = new HashTableArrayNode<TKey,TValue>[capacity]();
    for(int i = 0; i< capacity>;i++)
    {
      _array[i] = = new HashTableArrayNode<TKey, TValue>();
    }
  }

  /// <summary>
  /// Finds and returns the value for the specified key.
  /// </summary>
  /// <param name="key">The key whose value is sought</param>
  /// <param name="value">The value associated with the specified key</param>
  /// <returns>True if the value was found, false otherwise</returns>
  public bool TryGetValue(TKey key, out TValue value)
  {
    return _array[GetIndex(key)].TryGetValue(key, out value);
  }

  public void Add(TKey key, TValue value)
  {
    _array[GetIndex(key)].Add(key,value);
  }

  public void Update(TKey key, TValue value)
  {
    _array[GetIndex(key)].Update(key,value);
  }

  public void Remove(TKey key)
  {
    _array[GetIndex(key)].Remove(key,value);
  }

  // Maps a key to the array index based on hash code
  private int GetIndex(TKey key)
  {
    return Math.Abs(key.GetHashCode() % Capacity);
  }

  /// <summary>
  /// The capacity of the hash table array
  /// </summary>
  public int Capacity
  {
    get
    {
      return _array.Length;
    }
  }

}

class HashTable<TKey,TValue>
{
  // If the array exceeds this fill percentage it will grow
  // In this example the fill factor is the total number of items
  // regardless of whether they are collisions or not.
  int _fillFactor = 0.75;

  // the number of items in the hash table
  int _count;

  // the maximum number of items to store before growing.
  // This is just a cached value of the fill factor calculation
  int _maxItemsAtCurrentSize;

  HashTableArray<TKey,Tvalue> _array;

  /// <summary>
  /// Constructs a hash table with the default capacity
  /// </summary>
  public HashTable() : this(1000)
  {
  }

  public HashTable(int initialCapacity){
    if(initialCapacity < 1)
    {
      throw new ArgumentOutOfRangeException("initialCapacity");
    }

     _array = new HashTableArray<TKey, TValue>(initialCapacity);

    // when the count exceeds this value, the next Add will cause the
    // array to grow
    _maxItemsAtCurrentSize = (int)(initialCapacity * _fillFactor) + 1;
  }

  void Add(TKey key, TValue value)
  {
    // if we are at capacity, the array needs to grow
    if(count >= _maxItemsAtCurrentSize)
    {
      // allocate a larger array
      var largeArray = new HashTableArray<TKey, TValue>(_array.Capacity * 2);

      // and re-add each item to the new array
      for(var item in _array)
      {
        largeArray.Add(item.Key, item.Value);
      }
       // the larger array is now the hash table storage
      _array = largeArray;

      // update the new max items cached value
      _maxItemsAtCurrentSize = (int)(_array.Capacity * _fillFactor) + 1;
    }

     _array.Add(key, value);
    _count++;
  }

  /// <summary>
  /// Removes the item from the hash table whose key matches
  /// the specified key.
  /// </summary>
  /// <param name="key">The key of the item to remove</param>
  /// <returns>True if the item was removed, false otherwise.</returns>
  public bool Remove(TKey key)
  {
    bool removed = _array.Remove(key);
    if (removed)
    {
      _count--;
    }

    return removed;
  }

  /// <summary>
  /// The number of items currently in the hash table
  /// </summary>
  public int Count
  {
    get
    {
      return _count;
    }
  }

  public TValue this[TKey key]
  {
    get{
      TValue value;
      if(!_arry.TryGetValue(key,out value))
      {
        throw new ArgumentException("key");
      }
      return value
    }
    set{
      _array.Update(key,value);
    }
  }
}


```

# Hash Function

- A function that maps data of arbitrary size to data of a fixed size.
- Examples:
  - Verifying downloaded data
  - Storing passwords in a database
  - Hash tables key lookup

# Stability

- A hash function always generates the same output given the same input

- Stable

  ```csharp

  public int StableHash(string input)
  {
  int result = 0;
  foreach(byte ascii in input)
  {
  result += ascii;
  }
  return result;
  }
  ```

- Unstable

  ```csharp
  public int UnstableHash(string input)
  {
  int result = DateTime.Now.Second;
  foreach(byte ascii in input)
  {
  result += ascii;
  }
  return result;
  }
  ```

- Examples
- Stable

  ```
  StableHash("foo");
  StableHash("foo");
  StableHash("foo");
  324
  324
  324
  ```

- Unstable

  ```
  UnstableHash("foo");
  UnstableHash("foo");
  UnstableHash("foo");
  1449447443
  1449447444
  1449447445
  ```

# Uniformity

- A hash algorithm should distribute its resulting hash value uniformly throughout the output space.
- (More) Uniform

```csharp
public uint SDBMHash(string input)
{
uint hash = 0;
foreach (byte ascii in input)
{
hash = hash * 65599 + ascii;
}
return hash;
}
```

- Non-uniform

```csharp
public int StableHash(string input)
{
int result = 0;
foreach(byte ascii in input)
{
result += ascii;
}
return result;
}
```

- (More) Uniform

```
SDBMHash(”foo");
SDBMHash(”oof");
SDBMHash(”ofo");
849955110
924308646
923718264
```

- Non-uniform

```
StableHash("foo");
StableHash(”oof");
StableHash(”ofo");
324
324
324
```

# Security

- A secure hashing algorithm cannot be inverted (the input derived from the output hash).

```
Username Password Hash (sdbm)
evelyn    3471203675
brian     969889485
will      1978836480
```

```
Password Hash
aaaaaaaa 3834880256
aaaaaaab 3834880257
aaaaaaac 3834880258
aaaaaaad 3834880259
… …
zzzzzzzz 528284160
```

```
Hash        Match       Actual
3471203675  aagkDhA4    password
969889485   aac0xWRs    football
1978836480  aaabhqCy    jedi
```

- Output size: 32, 64, 128, 256, 512

  - 2^32 (4294967296)

  ```
  Checks/sec      Time
  1000            49 Days
  10,000          4.9 Days
  100,000         12 hours
  1,000,000       1 hour
  10,000,000      7 minutes
  100,000,000     42 seconds
  1,000,000,000   4 seconds
  ```

  - 2^512 (1.340781e+154)

  ```
  Checks/sec      Time
  1000            4.25e+143 years
  10,000          4.25e+142 years
  100,000         4.25e+141 years
  1,000,000       4.25e+140 years
  10,000,000      4.25e+139 years
  100,000,000     4.25e+138 years
  1,000,000,000   4.25e+137 years
  ```

# Sample Hash algorithim

## Additive Hash

Pro: Stable, fast
Cons: Poor Uniformity and Security

```
f    o   o
102 111 111
102 213 324
```

## Folding hash

- Pro: Stable, fast , better uniformity
- Cons: Poor security

```
l o r e    m i p      s u m      d o l o     r
1701998444 1885937773 544044403  1869377380  114
1701998444 -707031079 -162986676 1706390704  1706390818
```

## Dbj2 Hash

```csharp
public ulong Dbj2Hash(string input)
{
  ulong hash = 5381;
  foreach(byte c in input)
  {
  hash = hash * 33 + c;
  }
  return hash;
}
```

```
f      o       o
177675 5863386 193491849
```

## Hash Function Comparison

```
Name      Output Size Stable Uniform Secure
Additive      32        YES   NO      NO
Folding       32        YES   YES     NO
Dbj2          64        YES   YES     NO
MD5           128       YES   YES     NO*
SHA-1         160       YES   YES     NO*
SHA-2         224/384   YES   YES     NO*
SHA-2         256-512   YES   YES     YES
```

# Examples

- Using state-level caching for contacts finding with state
  - Find with a first name of a user in 25k users : took 51 ms
  - Find with a first name of a user and a state : took 1.7 ms with state caching using hash table structure
    - Note: it takes more memory to store them in hash table

```csharp
public Contact Add(Contact contact)
{
  int id = contact.ID.HasValue ? contact.ID.Value : nextId++;
  nextId = Math.Max(nextId, id + 1);

  Contact withId = Contact.CreateWithId(id, contact);

  Log.Verbose("Add: adding new contact with ID {0} ({1} {2})", withId.ID, withId.FirstName, withId.LastName);
  contacts.Add(withId);

  // Add to the state-level cache.
  // If the state does not currently exist in the cache - add the binary tree
  if (!stateCache.ContainsKey(withId.State))
  {
    stateCache.Add(withId.State, new BinaryTree<Contact>());
  }

  // now we know the state exists so add the contact
  stateCache[withId.State].Add(withId);

  Log.Verbose("Add: complete ({0})", withId.ID);

  return withId;
  }

  public bool Remove(Contact contact, out Contact removed)
  {
    if (contacts.Remove(contact))
    {
      if (stateCache.ContainsKey(contact.State))
      {
        // remove from the state-level cache
        stateCache[contact.State].Remove(contact);
      }

      Log.Info("Remove: removed contact {0} ({1} {2})", contact.ID.Value, contact.FirstName, contact.LastName);
      removed = contact;
      return true;
    }

    Log.Warning("Remove: Contact not found.  No action taken.");
    removed = default;
    return false;
  }
   public IEnumerable<Contact> Search(ContactFieldFilter filter)
   {
    Log.Verbose("Searching for contacts with filter: {0}", filter);

    // If the file has a state component
    // get the items from the cache instead of checking everything
    if (filter.State.HasValue)
    {
      if (stateCache.ContainsKey(filter.State.Value))
      {
        return filter.Apply(stateCache[filter.State.Value]);
      }
       else
      {
         return new SortedList<Contact>();
      }
    }
    else
    {
      return filter.Apply(this.Contacts);
    }
   }
```
