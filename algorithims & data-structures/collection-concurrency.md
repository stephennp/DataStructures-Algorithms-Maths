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
object jobsLock = new object(); 

// ...
while(jobs.Count > 0) {
  lock(jobsLock) { // Count needs to be called within the same lock scope as the call to Dequeue
    Job nextJob = jobs.Dequeue()
    nextJob.Process(); // The Process method is holding the lock open.
  }
}

```


```csharp
while(jobs.Count > 0) { // Check if the count is more than 0 while outside the lock
  Job nextJob = null;
  lock(jobsLock) { // Take the lock
    if(jobs.Count > 0) { // Check the count again while under the lock
      nextJob = jobs.Dequeue(); // While holding the lock, Dequeue the next job
    }
  }
  if(nextJob != null) {
    nextJob.Process(); // If we dequeued a job, then process it
  }
}

```