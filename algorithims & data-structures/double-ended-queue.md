# Intro

- A deque, also known as a double-ended queue, is an ordered collection of items similar to the queue.
- It has two ends, a front and a rear, and the items remain positioned in the collection. What makes a deque different is the unrestrictive nature of adding and removing items.
- New items can be added at either the front or the rear. Likewise, existing items can be removed from either end.
- Since Deque supports both `stack and queue` operations, it can be used as both.

```csharp
class Dequeue{
    readonly DoubleLinkedList store = new DoubleLinkedList();

    public void EnqueueHead(T value){
        store.addHead(value);
    }
    public void EnqueueTail(T value){
        store.addTail(value);
    }
    public void DequeueHead(T value){
        if(store.getHead(value))
            store.removeHead(value)
    }
    public void DequeueTail(T value){
        if(store.getTail(value))
            store.removeTail(value)
    }
    public bool PeekHead(out T value){
        return store.getHead();
    }
    public bool PeekTail(out T value){
        return store.getTail();
    }
    public int Count{get;set;}
}
```

# Queue

- First in, first out pattern

```csharp
class Queue{
   var dequeue = new Dequeue();

  void Enqueue(T value){
    dequeue.EnqueueTail(value)
  }
  void Peek(){
    dequeue.PeekHead();
  }
  void Pop(){
    dequeue.DequeueHead();
  }
}
```

# Stack

- First in, last out pattern

```csharp
class Stack{
  var dequeue = new Dequeue();

  void Push(T value){
    dequeue.EnqueueHead(value)
  }
  void Peek(){
    dequeue.PeekHead();
  }
  void Pop(){
    dequeue.DequeueHead();
  }
}
```

## Contact Manager

```csharp
interface ICommand{
  public string verb;
  public string[] args{get;set}
  public CommandResult results{get;set;}
}
abstract class Command: ICommand{
  public void Executed();
}
class AddCommand : Command{
  public CommandResult Execute(){
    // add new contact to store
  }
  public ICommand GetUndoCommand(){
    return new DirectRemoveCommand();
  }
}

class RemoveCommand : Command{
   public CommandResult Execute(){
    // filterd from args
    // remove contact to store
  }
  public ICommand GetUndoCommand(){
    return new DirectAddCommand();
  }
}

class DirectAddCommand: ICommand{
  private ContactStore store;
  private readonly IEnumerable<Contact> contacts;

  public CommandResult Execute(){
    // add contact to store
  }
}

class DirectRemoveCommand: ICommand{
  private ContactStore store;
  private readonly IEnumerable<Contact> contacts;

  public CommandResult Execute(){
    List<Contact> removed = new List<Contact>();
    foreach (Contact c in contacts)
    {
      Contact r;
      if (store.Remove(c, out r))
      {
        removed.Add(r);
      }
    }
  }
}
class FactoryCommand{
  public ICommand Add(IReadOnlyDictionary<string, string> args)
  {
    return new AddCommand(store, args);
  }

  public ICommand Remove(IReadOnlyDictionary<string, string> args)
  {
    return new RemoveCommand(store, args);
  }

  public ICommand Find(IReadOnlyDictionary<string, string> args)
  {
     return new FindCommand(store, args);
  }

  public ICommand Quit()
    {
      return new QuitCommand();
    }

}

class Program{
  public static void Run(){
    var factoryCmd = new FactoryCommand();
    switch()
    {
      case 'Add':
        var addCmd = factoryCmd.Add();
        RecordUndo(addCmd.Execute());
      break;
      case 'Remove':
        var removeCmd = factoryCmd.Remove();
        RecordUndo(removeCmd.Execute());
      break;

    }
  }
  public void RecordUndo(CommandResult result){
    if(result.CanUndo)
    {
      undo.push(result.GetUndoCommand())
    }
  }
}
```
