The queue data structure is a sequential collection of elements that follows the principle of First In First Out (FIFO)
The first element inserted into the queue is first element to be removed
A queue of people. People enter the queue at one end (rear/tail) and leave the queue from the other end (front/ head).
Queue is an abstract data type. It is defined by its behavior rather than being a mathematical model
The Queue data structure supports two main operations
Enqueue, which adds an element to the rear/tail of the collection
Dequeue, which removes an element from the front/head of the collection

![[queue-enque.jpg]]

![[queue-deque.jpg]]

### Key Points:
- A queue is a linear data structure that follows the First-In-First-Out (FIFO) principle.
- Elements are added at one end (rear) and removed from the other end (front).
- Main operations: enqueue (add), dequeue (remove), peek (view front element).
- Queues can have a fixed size or be dynamic.

### Real-world examples of Queue usage:
1. Print job spooling
2. Task scheduling in operating systems
3. Breadth-First Search algorithm in graph traversal
4. Handling of requests in web servers
5. Buffering in data streams

### Implementation

Using Array

```
CLASS Queue
  items = empty array

  FUNCTION enqueue(element)
    ADD element TO END OF items

  FUNCTION dequeue()
    IF isEmpty() THEN
      RETURN "Queue is empty"
    RETURN AND REMOVE first element from items

  FUNCTION peek()
    IF isEmpty() THEN
      RETURN "Queue is empty"
    RETURN first element of items

  FUNCTION isEmpty()
    RETURN true IF items is empty, false OTHERWISE

  FUNCTION size()
    RETURN length of items

  FUNCTION clear()
    SET items to empty array

  FUNCTION print()
    IF isEmpty() THEN
      PRINT "Queue is empty"
    ELSE
      PRINT items joined by ", "

END CLASS
```

```js
class Queue {
  constructor() {
    this.items = [];  // Array to store queue elements
  }

  // Add element to the back of the queue
  enqueue(element) {
    this.items.push(element);
    console.log(`${element} added to the queue`);
  }

  // Remove and return the front element
  dequeue() {
    if (this.isEmpty()) {
      return "Queue is empty";
    }
    const item = this.items.shift();
    console.log(`${item} removed from the queue`);
    return item;
  }

  // Return the front element without removing it
  peek() {
    if (this.isEmpty()) {
      return "Queue is empty";
    }
    return this.items[0];
  }

  // Check if the queue is empty
  isEmpty() {
    return this.items.length === 0;
  }

  // Return the size of the queue
  size() {
    return this.items.length;
  }

  // Clear the queue
  clear() {
    this.items = [];
    console.log("Queue cleared");
  }

  // Print the queue elements
  print() {
    if (this.isEmpty()) {
      console.log("Queue is empty");
    } else {
      console.log(this.items.join(', '));
    }
  }
}

// Usage example
const queue = new Queue();
queue.enqueue(10);
queue.enqueue(20);
queue.enqueue(30);
queue.print();  // Output: 10, 20, 30
console.log(queue.dequeue());  // Output: 10 removed from the queue
console.log(queue.peek());     // Output: 20
console.log(queue.size());     // Output: 2
queue.clear();
console.log(queue.isEmpty());  // Output: true
```

Using Object

```
CLASS Queue
  items = empty object
  frontIndex = 0
  backIndex = 0

  FUNCTION enqueue(element)
    SET items[backIndex] TO element
    INCREMENT backIndex

  FUNCTION dequeue()
    IF isEmpty() THEN
      RETURN "Queue is empty"
    item = items[frontIndex]
    DELETE items[frontIndex]
    INCREMENT frontIndex
    RETURN item

  FUNCTION peek()
    IF isEmpty() THEN
      RETURN "Queue is empty"
    RETURN items[frontIndex]

  FUNCTION isEmpty()
    RETURN backIndex - frontIndex EQUALS 0

  FUNCTION size()
    RETURN backIndex - frontIndex

  FUNCTION clear()
    SET items TO empty object
    SET frontIndex TO 0
    SET backIndex TO 0

  FUNCTION print()
    IF isEmpty() THEN
      PRINT "Queue is empty"
    ELSE
      Initialize empty string result
      FOR i FROM frontIndex TO backIndex - 1
        APPEND items[i] AND ", " TO result
      PRINT result WITHOUT last ", "

END CLASS
```

```javascript
class Queue {
  constructor() {
    this.items = {};  // Object to store queue elements
    this.frontIndex = 0;  // Index of the front element
    this.backIndex = 0;   // Index of the back element
  }

  // Add element to the back of the queue
  enqueue(element) {
    this.items[this.backIndex] = element;
    this.backIndex++;
    console.log(`${element} added to the queue`);
  }

  // Remove and return the front element
  dequeue() {
    if (this.isEmpty()) {
      return "Queue is empty";
    }
    const item = this.items[this.frontIndex];
    delete this.items[this.frontIndex];
    this.frontIndex++;
    console.log(`${item} removed from the queue`);
    return item;
  }

  // Return the front element without removing it
  peek() {
    if (this.isEmpty()) {
      return "Queue is empty";
    }
    return this.items[this.frontIndex];
  }

  // Check if the queue is empty
  isEmpty() {
    return this.backIndex - this.frontIndex === 0;
  }

  // Return the size of the queue
  size() {
    return this.backIndex - this.frontIndex;
  }

  // Clear the queue
  clear() {
    this.items = {};
    this.frontIndex = 0;
    this.backIndex = 0;
    console.log("Queue cleared");
  }

  // Print the queue elements
  print() {
    if (this.isEmpty()) {
      console.log("Queue is empty");
    } else {
      let result = "";
      for (let i = this.frontIndex; i < this.backIndex; i++) {
        result += `${this.items[i]}, `;
      }
      console.log(result.slice(0, -2));  // Remove last comma and space
    }
  }
}

// Usage example
const queue = new Queue();
queue.enqueue(10);
queue.enqueue(20);
queue.enqueue(30);
queue.print();  // Output: 10, 20, 30
console.log(queue.dequeue());  // Output: 10 removed from the queue
console.log(queue.peek());     // Output: 20
console.log(queue.size());     // Output: 2
queue.clear();
console.log(queue.isEmpty());  // Output: true
```

This implementation uses an object to store the queue elements, with frontIndex and backIndex to keep track of the front and back of the queue. This approach provides efficient enqueue and dequeue operations, both with O(1) time complexity.


