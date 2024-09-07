The queue data structure is a sequential collection of elements that follows the principle of First In First Out (FIFO)
The first element inserted into the queue is first element to be removed
A queue of people. People enter the queue at one end (rear/tail) and leave the queue from the other end (front/ head).
Queue is an abstract data type. It is defined by its behavior rather than being a mathematical model
The Queue data structure supports two main operations
Enqueue, which adds an element to the rear/tail of the collection
Dequeue, which removes an element from the front/head of the collection

![[queue-enque.jpg]]

![[queue-deque.jpg]]

### Queue Usage
Printers
CPU task scheduling
Callback queue in JavaScript runtime

### Implementation

Using Array

```js
class Queue {
    constructor(){
        this.items = []
    }

    enqueue(element){
        this.items.push(element)
    }

    dequeue(){
        return this.items.shift()
    }

    peek(){
        return this.items[this.items.length - 1]
    }

    size(){
        return this.items.length
    }

    isEmpty(){
        return this.items.length === 0
    }

    print(){
        console.log(this.items.toString())
    }
}
```

Using Object

```js
class Queue{
    constructor(){
        this.items = {}
        this.rear = 0
        this.front = 0
    }

    enqueue(element){
        this.items[this.rear] = element
        this.rear++
    }

    dequeue(){
        const item = this.items[this.front]
        delete this.items[this.front]
        this.front++
        return item
    }

    peek(){
        return this.items[this.front]
    }

    size(){
        return this.rear - this.front
    }

    isEmpty(){
        return this.rear - this.front === 0
    }
    
    print(){
      console.log(this.items)
    }
}

const queue = new Queue();
console.log(queue.isEmpty());
queue.enqueue(10);
queue.enqueue(20);
queue.enqueue(30);
console.log(queue.size());
queue.print();
console.log(queue.dequeue());
console.log(queue.peek());
console.log(queue.isEmpty());
```

