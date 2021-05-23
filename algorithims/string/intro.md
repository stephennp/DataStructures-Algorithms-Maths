# Intro

String searching overview
Naive search algorithm

- Algorithm
- Performance
  Boyer-Moore-Horspool algorithm
- Algorithm
- Performance

```csharp
public interface IStringSearchAlgorithm
{
    IEnumerable<ISearchMatch> Search(string pattern, string toSearch);
}
```

# Search Algorithm

- The IStringSearchAlgorithm defines the function, Search, which will be called to
  find all of the matches of the search string (pattern) within the input (toSearch)
  string

```csharp
public interface ISearchMatch
{
    int Start { get; }
    int Length { get; }
}
```

# Search Matches

- The ISearchMatch interface defines the index and length of a search match in
  the input string

```csharp
string pattern = "fox";
string toSearch = "The quick brown fox jumps over the lazy dog";
foreach(ISearchMatch match in algorithm.Search(pattern, toSearch))
{
...
}
```

- Examples: Finding "is" in
  Lorem ipsum dolor sit amet,
  consectetur adip`is`cing elit.
  Suspend`is`se sodales, enim
  id lobort`is` consectetur,
  neque lacus ultricies n`is`l, at
  feugiat.
  - Start: 44, 64, 92, 131
  - Length: 2, 2, 2, 2

# Naive Search

```csharp
// content: THECATJUMPEDINTORIVER
// search: AT
IEnumerable<int> Search(string content, string search)
{
  for(int i = 0; i < content.length, i++)
  {
    int maxCount = 0;
    while(content[i + maxCount] == search[maxCount])
    {
      maxCount++;
      if(search.length == maxCount)
      {
        // found match
        i += maxCount - 1;
        yeld return i;
        break;
      }
    }
  }
}

```

## Performance

- Average : O(n+m)
- Worst: O(nm)

# Boyer-Moore-Horspool

- A 2-stage searching algorithm that uses a table that contains the length to shift when a bad match occurs

## Steps

- Stage 1: Pre-process the string to find to build a bad match table
- Stage 2: The string to find is search right-toleft using the bad match table to skip ahead at a mismatch

```csharp
// this hash table used for shifting value when mismatch comparing
// e.g:    A B C C
// search: B C
// Hash table: B = 1, will shift `B C` to right 1 offset ->
// A B C C
//   B C
//       B C
Dictionary<int,int> BadMatch(string search){
  var dic = new Dictionary<int,int>();
  for(int i=0;i<search.length - 1;i++)
  {
    dic[search[i]] = search.length - i - 1;
  }
  return dic;
}

void BoyerMooreHandler(string content, string search){
  if(content == null || search == null)
  {
    throw new Expcetion();
  }
  var badMatchTable = BadMatch(search);

  var currentIndex;
  while(currentIndex <= content.length - search.length)
  {
    // get the right most item in search to compare
    var mostRightIndex = search.length - 1;
    // check the search and content match or not from right to left
    while(mostRightIndex >=0 && search[mostRightIndex] == content[mostRightIndex + currentIndex])
    {
      mostRightIndex -- ;
    }
    // if they are all matched , return the index and move next items
    if(mostRightIndex < 0)
    {
      yield return currentIndex;
      currentIndex += search.length;
    }
    // if either match partly or not, then move next items with bad mapping table
    else
    {
      currentIndex += badMatchTable[content[search.length - 1 + currentIndex]]
    }
  }
}
```
