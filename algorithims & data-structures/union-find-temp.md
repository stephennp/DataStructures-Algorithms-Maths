```csharp
class Graph
{
    int Vector;
    int E;
    Edge[] Edges;
  
  // parent[A] = -1
  // parent[B] = -1
  // parent[C] = -1
  // A -> B -> Parent[A] = B
  // B -> C -> Parent[B] = C
  int FindParent(int[] parent, int value)
  {
    if(parent[value] == -1)
    {
      return value;
    }

    FindParent(parent, parent[value])
  }
  // edge A -> B : parent[A] = B;
  // edge B -> C : parent[B] = C;
  void Union(int[] parent, int x, int y)
  {
      parent[x] = y;
  }
  int isCycle(){

      int[] Parent = new int[Graph.Vector];
      for(int i = 0; i < Graph.Vector; i++)
      {
        Parent[i] = -1;
      }

      // edge A->B
      // edge B->C
      // edge A->C
      for(int i = 0; i < Graph.E ; i++)
      {
        // Scenarios:
        // A->B : Parent[A] = -1 => A, Parent[B] = -1 => B
        // Union A & B

        // B->C : Parent[B] = -1 => B, Parent[C] = -1 => C
        // Union B & C

        // A->C : Parent[A] = B => Parent[B] = C => return C
        //        Parent[C] = -1 => C
        // C = C => cycle
        var x = FindParent(Parent,Graph.Edge[i].Source);
        var y = FindParent(Parent,Graph.Edge[i].Destination);

        // cycle
        if(x==y)
        {
          return 1;
        }

        Union(Parent, x, y);
      }
  }
}
class Edge {
    public int Source { get; set; }
    public int dSestination { get; set; }
}
```
