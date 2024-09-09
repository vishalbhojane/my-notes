Introduction to Heap:
- A Heap is a specialized tree-based data structure.
- It satisfies the heap property: in a max heap, for any given node, the node's value is greater than or equal to the values of its children. In a min heap, the node's value is less than or equal to the values of its children.
- Heaps are typically implemented as arrays, where for a node at index i, its left child is at 2i+1 and right child at 2i+2.
- The root of the heap is always the maximum element in a max heap or the minimum element in a min heap.
- Heaps are not sorted structures; they only guarantee that the root is the max/min element.

Real-world examples of Heap usage:
1. Priority queues in operating systems
2. Dijkstra's algorithm for finding shortest paths in graphs
3. Heap sort algorithm
4. Memory management in programming languages
5. Job scheduling in computer systems

JavaScript Implementation of a Max Heap:

```js
class MaxHeap {
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

  // Insert an element into the heap
  insert(value) {
    this.heap.push(value);
    this.heapifyUp(this.heap.length - 1);
  }

  // Heapify up to maintain max heap property
  heapifyUp(index) {
    let currentIndex = index;
    while (currentIndex > 0 && this.heap[currentIndex] > this.heap[this.getParentIndex(currentIndex)]) {
      this.swap(currentIndex, this.getParentIndex(currentIndex));
      currentIndex = this.getParentIndex(currentIndex);
    }
  }

  // Remove and return the maximum element (root)
  extractMax() {
    if (this.heap.length === 0) return null;
    if (this.heap.length === 1) return this.heap.pop();

    const max = this.heap[0];
    this.heap[0] = this.heap.pop();
    this.heapifyDown(0);

    return max;
  }

  // Heapify down to maintain max heap property
  heapifyDown(index) {
    let largest = index;
    const leftChild = this.getLeftChildIndex(index);
    const rightChild = this.getRightChildIndex(index);

    if (leftChild < this.heap.length && this.heap[leftChild] > this.heap[largest]) {
      largest = leftChild;
    }

    if (rightChild < this.heap.length && this.heap[rightChild] > this.heap[largest]) {
      largest = rightChild;
    }

    if (largest !== index) {
      this.swap(index, largest);
      this.heapifyDown(largest);
    }
  }

  // Get the maximum element without removing it
  peek() {
    return this.heap[0];
  }

  // Get the size of the heap
  size() {
    return this.heap.length;
  }

  // Check if the heap is empty
  isEmpty() {
    return this.heap.length === 0;
  }

  // Print the heap
  print() {
    console.log(this.heap);
  }
}

// Usage example
const maxHeap = new MaxHeap();
maxHeap.insert(10);
maxHeap.insert(5);
maxHeap.insert(17);
maxHeap.insert(3);
maxHeap.insert(8);

maxHeap.print(); // [17, 10, 5, 3, 8]
console.log(maxHeap.extractMax()); // 17
maxHeap.print(); // [10, 8, 5, 3]
console.log(maxHeap.peek()); // 10
```

```
CLASS MaxHeap
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

  FUNCTION insert(value)
    ADD value TO heap
    heapifyUp(last index of heap)

  FUNCTION heapifyUp(index)
    WHILE index > 0 AND heap[index] > heap[getParentIndex(index)]
      swap(index, getParentIndex(index))
      index = getParentIndex(index)

  FUNCTION extractMax()
    IF heap is empty RETURN null
    IF heap has only one element RETURN that element
    max = heap[0]
    heap[0] = last element of heap
    REMOVE last element of heap
    heapifyDown(0)
    RETURN max

  FUNCTION heapifyDown(index)
    largest = index
    left = getLeftChildIndex(index)
    right = getRightChildIndex(index)
    
    IF left < heap size AND heap[left] > heap[largest]
      largest = left
    IF right < heap size AND heap[right] > heap[largest]
      largest = right
    
    IF largest is not index
      swap(index, largest)
      heapifyDown(largest)

  FUNCTION peek()
    RETURN heap[0]

  FUNCTION size()
    RETURN length of heap

  FUNCTION isEmpty()
    RETURN true if heap is empty, false otherwise

  FUNCTION print()
    PRINT heap array

END CLASS
```

This implementation provides a basic structure for a max heap. To create a min heap, you would simply change the comparison operators in heapifyUp and heapifyDown (< instead of >).

The pseudocode offers a quick overview of the logic behind each operation. Remember that the actual implementation uses zero-based indexing for array representation of the heap.