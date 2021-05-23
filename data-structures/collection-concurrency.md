# Intro

- Two or more operations executing at the same time (concurrently).
- Multiple threads executing within a `single process` accessing a shared resource (e.g., a shared List<T>)
- Multiple processes running on the `same computer` accessing a shared resource (e.g., a shared file)
- Multiple processes running on `different computers` accessing a shared resource (e.g., a shared database table)

```csharp
class Job {
  readonly int Priority; // set in constructor
  public void Process() {
    ...
  }
}
```

# Job class

- A basic job class that contains a priority and a process method.

```csharp
var jobs = new PriorityQueue<Job>(); // The priority queue of jobs to execute
for(int i = 0; i < 100; i++) { // Add 100 jobs to the queue (the constructor parameter is the job priority)
  jobs.Enqueue(new Job(i));
}

while(jobs.Count > 0) { //Dequeue and process each of the job in priority order.
  var job = jobs.Dequeue();
  job.Process();
}

```

```csharp
Thread[] adders = new Thread[4]; //Add jobs using 4 threads
ThreadStart addJobs = delegate() {
  for(int i = 0; i < 25; i++) { // Each thread will add 25 jobs to the queue
    jobs.Enqueue(new Job(i));
  }
}

for(int i=0; i < adders.Length; i++) { //Create the 4 threads and start them to add the jobs to the queue concurrently
  adders[i] = new Thread(addJobs);
  adders[i].Start();
}
```

- Concurrent updates to nonconcurrency-safe collections can lead to unexpected behavior and data loss

# Caller Synchronization

- The caller is responsible for ensuring all access to the collection is performed in a `concurrency-safe` manner
- Allows concurrent-safe access to non-concurrency-safe collections
- No overhead when the collection is used non-concurrently
- The caller can determine the optimal synchronization approach

```csharp
object jobsLock = new object(); //Create the object that will be used as the shared monitor lock object
  // ...
  lock(jobsLock) { // Take the lock before enqueuing jobs
    jobs.Enqueue(new Job(...));
  }

  lock(jobsLock) { // Lock before dequeuing the next job
    Job nextJob = jobs.Dequeue();
    nextJob.Process(); //The job can be processed
  }

```

```csharp
while(jobs.Count > 0) { // Check if the count is more than 0 while outside the lock
  Job nextJob = null;
  // this lock prevent other threads can go into
  lock(jobsLock) { // Take the lock
    if(jobs.Count > 0) { // Check the count again while under the lock
      nextJob = jobs.Dequeue(); // While holding the lock, Dequeue the next job
    }
  }
  // when a thread exits lock section, another thread can into the lock serializely
  if(nextJob != null) {
    nextJob.Process(); // If we dequeued a job, then process it
  }
}

```

# Using Monitor Lock

- Pro
  - Non-concurrent-safe collections can be used in concurrent environments
  - Easy to implement
- Cons
  - Caller is responsible for all thread synchronization
  - Readers block other readers
  - Easy to implement wrong

# Monitor Locking vs Reader/Writer Locking

- ML:
  - A single monitor lock is used to serialize access to the container
  - Monitor locks are very light-weight
  - Readers block other readers
- RWL
  - A single reader/writer lock is used to serialize write-access to the container
  - The reader/writer lock allows multiple readers concurrently while blocking writes
  - Concurrent reading can overcome performance costs versus monitors

# Reader/Writer locking

- The .NET ReaderWriterLockSlim class used to provide concurrent readers while serializing all writers.

```csharp
var rwLock = new ReaderWriterLockSlim(); // A single ReaderWriterLockSlim instance serializes writes and blocks writes while allowing concurrent reads.

public void Enqueue(T value) { // The write lock is entered before a nonconcurrency-safe operation. All reads and writes are blocked until this is exited.
  rwLock.EnterWriteLock();
  try
  {
    heap.Push(value); // The non-concurrent-safe operation runs within a try-block
  }
  finally
  {
    rwLock.ExitWriteLock(); // In the finally-block the write lock is exited
  }
}

public T Peek() {
  rwLock.EnterReadLock(); // In a read-only method a read lock is used to allow concurrent readers while blocking writes
  try
  {
    return heap.Top(); // The read operation is performed within a try-block
  }
  finally
  {
    rwLock.ExitReadLock(); //When the number of readers is zero then writes will be allowed again
  }
}
```

# Queue with locking

```csharp
 public class PriorityQueue<T> : IQueue<T>
    {
        readonly Heap<T> heap;
        readonly object syncLock = new object();

        public PriorityQueue()
            : this(Comparer<T>.Default)
        {
        }

        public PriorityQueue(IComparer<T> comparer)
        {
            heap = new Heap<T>(comparer);
        }

        public void Enqueue(T value)
        {
            lock (syncLock)
            {
                heap.Push(value);
            }
        }

        public T Dequeue()
        {
            lock (syncLock)
            {
                if (heap.Empty)
                {
                    throw new QueueEmptyException();
                }

                T value = heap.Top();
                heap.Pop();

                return value;
            }
        }

        public T Peek()
        {
            lock (syncLock)
            {
                if (heap.Empty)
                {
                    throw new QueueEmptyException();
                }

                return heap.Top();
            }
        }

        public void Clear()
        {
            lock (syncLock)
            {
                heap.Clear();
            }
        }

        public int Count
        {
            get
            {
                lock (syncLock)
                {
                    return heap.Count;
                }
            }
        }
    }
```

# Concurrent .NET Collections

- ConcurrentDictionary<TK,TV>
- ConcurrentQueue<T>
- ConcurrentStack<T>
- ConcurrentBag<T>

```csharp
using System.Collections.Concurrent; // The concurrent collections are in the System.Collections.Concurrent namespace
//...
var queue = new ConcurrentQueue<int>(); //  Allocate a concurrent queue of integers
queue.Enqueue(1);  // Enqueue works the same as Queue<T>
int value;

if(queue.TryPeek(out value)) { // Peeking requires the “Try” pattern which avoids having to fail if the queue is empty
  Console.WriteLine(value);
}
if(queue.TryDequeue(out value)) { // Dequeuing also uses the “Try” pattern to avoid failure when the queue is empty
  Console.WriteLine(value);
}
```
