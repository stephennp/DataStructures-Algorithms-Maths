# Intro
- Strings can essentially be viewed as the most important and common topics for a variety of programming problems. String processing has a variety of real world applications too, such as:
  - Search Engines
  - Genome Analysis
  - Data Analytics

- All the content presented to us in textual form can be visualized as nothing but just strings.

- Tries:
  - Tries are an extremely special and useful data-structure that are based on the prefix of a string. They are used to represent the “Retrieval” of data and thus the name Trie.

- Prefix : What is prefix:

  - The prefix of a string is nothing but any n letters n <= |S| that can be considered beginning strictly from the starting of a string. For example , the word “abacaba” has the following prefixes:
```
a
ab
aba
abac
abaca
abacab
```
- A Trie is a special data structure used to store strings that can be visualized like a graph. It consists of nodes and edges. Each node consists of at max 26 children and edges connect each parent node to its children. These 26 pointers are nothing but pointers for each of the 26 letters of the English alphabet A separate edge is maintained for every edge.

- Strings are stored in a top to bottom manner on the basis of their prefix in a trie. All prefixes of length 1 are stored at until level 1, all prefixes of length 2 are sorted at until level 2 and so on.

```csharp
            NULL
       a          b           // a b, a b c, a d
    b     d       a           // b a, b a d, b a g
  a   c         d   g
```

# Psuedo code

```csharp
void insert(String s)
{
    for(every char in string s)
    {
        if(child node belonging to current char is null)
        {
            child node=new Node();
        }
        current_node=child_node;
    }
}

boolean check(String s)
{
    for(every char in String s)
    {
        if(child node is null)    
        {
            return false;
        }
    }
    return true;
}
```

# Implement

```csharp
class Trie{
  int AlphabetSize = 26;
  TrieNode root;


  class TrieNode {
      TrieNode[] children = new TrieNode[AlphabetSize];
      bool isEndOfTheWord {get; set;}
      public TrieNode(){
        isEndOfTheWord = false;
        for(int i = 0; i< AplhabetSize ; i++)
        {
          children[i] = null;
        }
      }
  }

  void Insert(string key)
  {
    var crawler = root;
      for(int i= 0; i<key.length; i++)
      {
        // get order of the alphabet
        var index = key[i] - 'a';
        if(crawler.children[index] == null)
        {
          crawler.children[index] = new TrieNode();
        }
        crawler = crawler.children[index];
      }

      // mark last node as leaf
      crawler.isEndOfTheWord = true;
  }

  bool Search(string key){
    var crawler = root;
    for(int i= 0; i<key.length; i++)
      {
       // get order of the alphabet
        var index = key[i] - 'a';
        if(crawler.children[index] == null)
        {
          return;
        }
        crawler = crawler.children[index];
      } 
    return crawler != null && crawler.isEndOfTheWord;

  }

  
}
```