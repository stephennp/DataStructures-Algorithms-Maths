# Intro 
- A circular queue is an improvement over the standard queue structure. In a standard queue, when an element is deleted, the` vacant space is not reutilized`. However, in a `circular queue, vacant spaces are reutilized`.

- While inserting elements, when you reach the end of an array and you need to insert another element, you must insert that element at the beginning `(given that the first element has been deleted and the space is vacant)`.

```csharp
// size : 5
// front=rear= -1
// 1. enqueue : 1
// front = 0
// rear = -1 + 1 / 5 = 0

// 2. enqueue : 2
// front = 0
// rear = 0 + 1 / 5 = 1

// 3. enquery : 3
// front = 0
// rear = 1 + 1 / 5 = 2

// 4. enquery : 4
// front = 0
// rear = 2 + 1 / 5 = 3

// 5. enqueue : 5
// front = 0
// rear = 3 + 1 / 5 = 4

// 6. dequeue
// front = (0 + 1) % 5 = 1

// 7. dequeue
// front = (1 + 1) % 5 = 2

// 8. enqueue : 6
// rear = ( 4 + 1 ) % 5 = 0

// 9. enqueue : 7
// rear = ( 0 + 1 ) % 5 = 1


void enqueue(int queue[], int element, int& rear, int arraySize, int& count) {
    if(count == arraySize)            // Queue is full
            printf(“OverFlow\n”);
    else{
        if (front == -1)
          front = 0;
        queue[rear] = element;
        rear = (rear + 1)%arraySize;
        count = count + 1;
    }
}

void dequeue(int queue[], int& front, int rear, int& count) {
    if(count == 0)            // Queue is empty
        printf(“UnderFlow\n”);
    else {
       if (front == rear) {
          front = -1;
          rear = -1;
        } 
        else
        {
          queue[front] = 0;        // Delete the front element
          front = (front + 1)%arraySize;
        }
        count = count - 1;
    }
}

int Front(int queue[], int front) {
    return queue[front];
}

int size(int count) {
    return count;
}

bool isEmpty(int count) {
    return (count == 0);
}

```