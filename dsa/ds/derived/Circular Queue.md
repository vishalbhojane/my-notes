The size of the queue is fixed and a single block of memory is used as if the first element is connected to the last element
Also referred to as circular buffer or ring buffer and follows the FIFO principle
A circular queue will reuse the empty block created during the dequeue operation When working with queues of fixed maximum size, a circular queue is a great implementation choice
The Circular Queue data structure supports two main operations
Enqueue, which adds an element to the rear/tail of the collection
Dequeue, which removes an element from the front/head of the collection

Once full, cannot add more elements

![[circular-queue-enque.jpg]]

Dequeue, now empty space can be reused

![[circular-queue-deque.jpg]]

Introduction to Circular Queue:
- A Circular Queue is a linear data structure that follows the FIFO principle.
- It's a variation of a regular queue where the last position is connected to the first position.
- It efficiently uses memory by reusing empty spaces.
- Main operations: enqueue, dequeue, isFull, isEmpty.
- Also known as a Ring Buffer.

Real-world examples of Circular Queue usage:
1. CPU scheduling in operating systems
2. Memory management in embedded systems
3. Traffic light control systems
4. Buffering for data streams (e.g., keyboard inputs)
5. Implementing round-robin scheduling algorithms

### Implementation

```
CLASS CircularQueue
  items = empty object
  capacity = given capacity
  currentLength = 0
  rear = -1
  front = -1

  FUNCTION enqueue(element)
    IF isFull() THEN
      RETURN false
    rear = (rear + 1) % capacity
    items[rear] = element
    INCREMENT currentLength
    IF front is -1 THEN
      front = rear
    RETURN true

  FUNCTION dequeue()
    IF isEmpty() THEN
      RETURN null
    item = items[front]
    DELETE items[front]
    DECREMENT currentLength
    IF isEmpty() THEN
      front = -1
      rear = -1
    ELSE
      front = (front + 1) % capacity
    RETURN item

  FUNCTION peek()
    IF isEmpty() THEN
      RETURN null
    RETURN items[front]

  FUNCTION isEmpty()
    RETURN currentLength EQUALS 0

  FUNCTION isFull()
    RETURN currentLength EQUALS capacity

  FUNCTION size()
    RETURN currentLength

  FUNCTION print()
    IF isEmpty() THEN
      PRINT "Queue is empty"
    ELSE
      Initialize empty string str
      FOR i FROM front TO rear
        APPEND items[i] AND space TO str
      PRINT str

END CLASS
```

```js
class CircularQueue {
  constructor(capacity) {
    this.items = {};
    this.capacity = capacity;
    this.currentLength = 0;
    this.rear = -1;
    this.front = -1;
  }

  // Add element to the queue
  enqueue(element) {
    if (this.isFull()) {
      console.log("Queue is full");
      return false;
    }
    this.rear = (this.rear + 1) % this.capacity;
    this.items[this.rear] = element;
    this.currentLength++;
    if (this.front === -1) {
      this.front = this.rear;
    }
    console.log(`${element} added to the queue`);
    return true;
  }

  // Remove and return the front element
  dequeue() {
    if (this.isEmpty()) {
      console.log("Queue is empty");
      return null;
    }
    const item = this.items[this.front];
    delete this.items[this.front];
    this.currentLength--;
    if (this.isEmpty()) {
      this.front = -1;
      this.rear = -1;
    } else {
      this.front = (this.front + 1) % this.capacity;
    }
    console.log(`${item} removed from the queue`);
    return item;
  }

  // Return the front element without removing it
  peek() {
    if (this.isEmpty()) {
      console.log("Queue is empty");
      return null;
    }
    return this.items[this.front];
  }

  // Check if the queue is empty
  isEmpty() {
    return this.currentLength === 0;
  }

  // Check if the queue is full
  isFull() {
    return this.currentLength === this.capacity;
  }

  // Return the size of the queue
  size() {
    return this.currentLength;
  }

  // Print the queue elements
  print() {
    if (this.isEmpty()) {
      console.log("Queue is empty");
    } else {
      let i;
      let str = "";
      for (i = this.front; i !== this.rear; i = (i + 1) % this.capacity) {
        str += this.items[i] + " ";
      }
      str += this.items[i];
      console.log(str);
    }
  }
}

// Usage example
const queue = new CircularQueue(5);
queue.enqueue(10);
queue.enqueue(20);
queue.enqueue(30);
queue.enqueue(40);
queue.enqueue(50);
queue.print();  // Output: 10 20 30 40 50
console.log(queue.dequeue());  // Output: 10 removed from the queue
queue.enqueue(60);
queue.print();  // Output: 20 30 40 50 60
console.log(queue.peek());  // Output: 20
console.log(queue.size());  // Output: 5
```

This implementation uses an object to store the queue elements and maintains front and rear pointers to keep track of the queue's state. The modulo operation `% capacity` is used to wrap around the queue, creating the circular behavior.