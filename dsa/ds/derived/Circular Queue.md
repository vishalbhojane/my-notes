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

### Circular queue usage
Clock
Streaming data
Traffic light

### Implementation

```js
class CircularQueue {
    constructor(capacity){
        this.capacity = capacity
        this.items = new Array(this.capacity)
        this.rear = -1
        this.front = -1
        this.currentLength = 0
    }

    isFull(){
        return this.currentLength === this.capacity
    }

    isEmpty(){
        return this.currentLength === 0
    }

    size(){
        return this.currentLength
    }

    enqueue(item){
        if(this.isFull()){
            return
        }
        this.rear = (this.rear + 1) % this.capacity
        this.items[this.rear] = item
        this.currentLength += 1
        if(this.front === -1){
            this.front = this.rear
        }
    }

    dequeue(){
        if(this.isEmpty()){
            return null
        }
        const item = this.items[this.front]
        this.items[this.front] = null
        this.front = (this.front + 1) % this.capacity
        this.currentLength -= 1
        if(this.isEmpty()){
            this.front = -1
            this.rear = -1
        }
        return item
    }

    peek(){
        if(this.isEmpty()){
            return null
        }
        return this.items[this.front]
    }

    print(){
        if(this.isEmpty()){
            console.log('Queue is empty')
            return
        }
        let i
        let str = ""
        for(i = this.front; i !== this.rear; i = (i + 1) % this.capacity){
            str += this.items[i] + " "
        }
        str += this.items[i] // appending last element, since loops exits on that condition
        console.log(str);
    }
}

const queue = new CircularQueue(5);
console.log(queue.isEmpty());
queue.enqueue(10);
queue.enqueue(20);
queue.enqueue(30);
queue.enqueue(40);
queue.enqueue(50);
console.log(queue.size());
queue.print();
console.log(queue.isFull());
console.log(queue.dequeue());
console.log(queue.peek());
queue.print();
queue.enqueue(60);
queue.print();
```