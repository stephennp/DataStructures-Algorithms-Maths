# Intro

- A container where data is stored in nodes consisting of a single data item and a reference to the next node
- It likes a `chain` -> start at the first link -> Follow the chain to the last link
- Each link in the chain is called a node and a node contains two things
  - single value
  - next: it contains a references that refers to the next item in the list

```csharp
class Node{
    public Node next;
    public int value;
    public Node(Node next, int value)
    {
        this.next =next;
        this.value = value;
    }
}

Node head = new Node(1);
head.next = new Node(2);
head.next.next = new Node(3);
```

# Singly linked list

- A linked list that provides forward iteration from the start to the end of the list
- A generic class containing the data and the reference to the next node

```csharp
class LinkedListNode<TNode>{
    public LinkedListNode(LinkedListNode<TNode> next,TNode value){
      this.next = next;
      this.value = value;
    }
    public LinkedListNode<TNode> next;
    public TNode value;
}
```

# Double Linked List

- A linked list that provides forward iteration from the start to the end of the list.
  and reverse iteration, from end to start.
- You can iterate the list forwards and backwards

```csharp
class Node{
  public Node(Node next, Node previous, int value)
  {
    this.next = next;
    this.previous = previous;
    this.value = value;
  }
  public Node next;
  public Node previous;
  public int value;
}

class DoubleLinkedList: ICollection
{
  public Node head;
  public Node tail;
  // Complexity: O(1)
  public void AddHead(Node node){
    Node temp = head;

    // add new node for head
    head = node;

    // mode old head to behind the new head
    head.next = temp;

    if(count == 0)
    {
      tail = head;
    }
    else
    {
      // due to tail = head, so it also affected to:
      // tail.previous = head,
      // oldhead.previous = head
      temp.previous = head;
    }
    count ++;
  }

  // Complexity: O(1)
  public void AddTail(Node node){
    if(count == 0 )
    {
      Head = node;
    }
    else
    {
      Tail.next = node;
      node.previous = Tail;
    }
    Tail = node;
    count ++;
  }

  // Complexity: O(n)
  public void Find(T value)
  {
    var currentValue = head;
    while(currentValue != null)
    {
      if(currentValue.value.equal(value))
      {
        return currentValue;
      }
      currentValue = currentValue.next;
    }
    return null;
  }

  // Complexity: O(n)
  public T Contain(T value)
  {
    return Find(value) != null;
  }

  // Complexity: O(n)
  public bool Remove(T node)
  {
    // checking:
    // null
    // single node
    // multinode
    //  1. Head
    //  2. Tail
    //  3. Middle (glue two side of node together)

    if(Find(node) == null)
    {
      return false;
    }

    var previous = node.previous
    var next = node.next

    if(previous == null)
    {
      head = next;
      // checking a single or multi node
      if(head != null)
      {
          head.previous = null
      }
    }
    else{
      previous.next = next
    }

     if(next == null)
    {
      tail = previous;
      // checking a single or multi node
      if(tail != null)
      {
          tail.next = null
      }
    }
    else{
      next.previous = previous;
    }
    count --;
  }

  public void AddSortedNode(T node)
  {
    // checking null
    // add head = tail
    if(head == null)
    {
      head = tail = node;
    }
    // checking head
    else if(node.value < head.value)
    {
      head.previous = node;
      node.next = head;
      head = node;
    }
    //checking tail
    else if(node.value >= tail.value)
    {
      tail.next = node;
      node.previous = tail
      tail = node;
    }
    // checking insertion point between head and tail
    else{
      currentNode = head;
      while(currentNode.value < node)
      {
        currentNode = currentNode.next;
      }
    }

    // 6->(7) -> 8
    node.next = currentNode;
    node.previous = currentNode.previous;
    currentNode.previous  = node;
    currentNode.previous.next = node;
    
  }

  public void getEnumeration(){
    // begin at head
  }
  public void getReverseEnumeration(){
    //begin at tail
  }
}
```



