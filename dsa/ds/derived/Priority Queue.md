Introduction to Priority Queue:
- A Priority Queue is an abstract data type similar to a regular queue.
- Elements in a priority queue have associated priorities.
- Elements with higher priority are dequeued before elements with lower priority.
- Can be implemented using various data structures, but heaps are most common.
- Supports operations like enqueue (insert), dequeue (extract max/min), and peek.

Real-world examples of Priority Queue usage:
1. Task scheduling in operating systems
2. Bandwidth management in computer networks
3. Dijkstra's shortest path algorithm
4. Huffman coding for data compression
5. Emergency room patient management

JavaScript Implementation of a Priority Queue (using Max Heap):

```js
class PriorityQueue {
  constructor() {
    this.heap = [];
  }

  // Helper method to get parent index
  getParentIndex(index) {
    return Math.floor((index - 1) / 2);
  }

  // Helper method to get left child index
  getLeftChildIndex(index) {
    return 2 * index + 1;
  }

  // Helper method to get right child index
  getRightChildIndex(index) {
    return 2 * index + 2;
  }

  // Helper method to swap elements
  swap(index1, index2) {
    const temp = this.heap[index1];
    this.heap[index1] = this.heap[index2];
    this.heap[index2] = temp;
  }

  // Insert an element with a priority
  enqueue(element, priority) {
    const node = { element, priority };
    this.heap.push(node);
    this.heapifyUp(this.heap.length - 1);
  }

  // Heapify up to maintain max heap property
  heapifyUp(index) {
    let currentIndex = index;
    while (currentIndex > 0 && 
           this.heap[currentIndex].priority > this.heap[this.getParentIndex(currentIndex)].priority) {
      this.swap(currentIndex, this.getParentIndex(currentIndex));
      currentIndex = this.getParentIndex(currentIndex);
    }
  }

  // Remove and return the highest priority element
  dequeue() {
    if (this.isEmpty()) return null;
    if (this.heap.length === 1) return this.heap.pop().element;

    const max = this.heap[0].element;
    this.heap[0] = this.heap.pop();
    this.heapifyDown(0);

    return max;
  }

  // Heapify down to maintain max heap property
  heapifyDown(index) {
    let largest = index;
    const leftChild = this.getLeftChildIndex(index);
    const rightChild = this.getRightChildIndex(index);

    if (leftChild < this.heap.length && 
        this.heap[leftChild].priority > this.heap[largest].priority) {
      largest = leftChild;
    }

    if (rightChild < this.heap.length && 
        this.heap[rightChild].priority > this.heap[largest].priority) {
      largest = rightChild;
    }

    if (largest !== index) {
      this.swap(index, largest);
      this.heapifyDown(largest);
    }
  }

  // Get the highest priority element without removing it
  peek() {
    if (this.isEmpty()) return null;
    return this.heap[0].element;
  }

  // Check if the priority queue is empty
  isEmpty() {
    return this.heap.length === 0;
  }

  // Get the size of the priority queue
  size() {
    return this.heap.length;
  }

  // Print the priority queue
  print() {
    console.log(this.heap.map(node => `${node.element}(${node.priority})`).join(', '));
  }
}

// Usage example
const pq = new PriorityQueue();
pq.enqueue("Task 1", 3);
pq.enqueue("Task 2", 1);
pq.enqueue("Task 3", 4);
pq.enqueue("Task 4", 2);

pq.print(); // Task 3(4), Task 1(3), Task 2(1), Task 4(2)
console.log(pq.dequeue()); // Task 3
console.log(pq.peek()); // Task 1
console.log(pq.size()); // 3
```

```
CLASS PriorityQueue
  heap = empty array

  FUNCTION getParentIndex(index)
    RETURN floor((index - 1) / 2)

  FUNCTION getLeftChildIndex(index)
    RETURN 2 * index + 1

  FUNCTION getRightChildIndex(index)
    RETURN 2 * index + 2

  FUNCTION swap(index1, index2)
    temp = heap[index1]
    heap[index1] = heap[index2]
    heap[index2] = temp

  FUNCTION enqueue(element, priority)
    node = {element, priority}
    ADD node TO heap
    heapifyUp(last index of heap)

  FUNCTION heapifyUp(index)
    WHILE index > 0 AND heap[index].priority > heap[getParentIndex(index)].priority
      swap(index, getParentIndex(index))
      index = getParentIndex(index)

  FUNCTION dequeue()
    IF heap is empty RETURN null
    IF heap has only one element RETURN that element
    max = heap[0].element
    heap[0] = last element of heap
    REMOVE last element of heap
    heapifyDown(0)
    RETURN max

  FUNCTION heapifyDown(index)
    largest = index
    left = getLeftChildIndex(index)
    right = getRightChildIndex(index)
    
    IF left < heap size AND heap[left].priority > heap[largest].priority
      largest = left
    IF right < heap size AND heap[right].priority > heap[largest].priority
      largest = right
    
    IF largest is not index
      swap(index, largest)
      heapifyDown(largest)

  FUNCTION peek()
    IF heap is empty RETURN null
    RETURN heap[0].element

  FUNCTION isEmpty()
    RETURN true if heap is empty, false otherwise

  FUNCTION size()
    RETURN length of heap

  FUNCTION print()
    PRINT each node's element and priority in heap

END CLASS
```

This implementation provides a basic structure for a priority queue using a max heap. Each node in the heap contains both the element and its priority. The priority is used for comparisons to maintain the heap property.

The pseudocode offers a quick overview of the logic behind each operation. Remember that this implementation gives higher priority to larger numbers. If you want smaller numbers to have higher priority, you would need to change the comparison operators in heapifyUp and heapifyDown.