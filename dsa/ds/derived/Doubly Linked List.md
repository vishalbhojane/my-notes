Introduction to Doubly Linked List:
- A Doubly Linked List is a linear data structure where each node contains data and two pointers.
- One pointer references the next node, and the other references the previous node.
- It allows traversal in both forward and backward directions.
- The first node's previous pointer and the last node's next pointer typically point to null.
- Key operations: insertion, deletion, forward traversal, backward traversal.

Real-world examples of Doubly Linked List usage:
1. Browser's forward and back button functionality
2. Undo and redo functionality in text editors
3. Music player's next and previous song feature
4. Image viewer's navigation
5. Implementation of LRU (Least Recently Used) cache

JavaScript Implementation of a Doubly Linked List:

```js
class Node {
  constructor(data) {
    this.data = data;
    this.prev = null;  // Reference to the previous node
    this.next = null;  // Reference to the next node
  }
}

class DoublyLinkedList {
  constructor() {
    this.head = null;  // First node in the list
    this.tail = null;  // Last node in the list
    this.size = 0;     // Size of the list
  }

  // Add a node to the end of the list
  append(data) {
    const newNode = new Node(data);

    if (!this.head) {
      // If the list is empty, set both head and tail to the new node
      this.head = newNode;
      this.tail = newNode;
    } else {
      // Add the new node after the tail
      this.tail.next = newNode;
      newNode.prev = this.tail;
      this.tail = newNode;
    }

    this.size++;
  }

  // Add a node to the beginning of the list
  prepend(data) {
    const newNode = new Node(data);

    if (!this.head) {
      // If the list is empty, set both head and tail to the new node
      this.head = newNode;
      this.tail = newNode;
    } else {
      // Add the new node before the head
      newNode.next = this.head;
      this.head.prev = newNode;
      this.head = newNode;
    }

    this.size++;
  }

  // Insert a node at a specific position
  insert(data, position) {
    if (position < 0 || position > this.size) {
      console.log("Invalid position");
      return;
    }

    if (position === 0) {
      this.prepend(data);
    } else if (position === this.size) {
      this.append(data);
    } else {
      const newNode = new Node(data);
      let current = this.head;
      let index = 0;

      while (index < position) {
        current = current.next;
        index++;
      }

      newNode.next = current;
      newNode.prev = current.prev;
      current.prev.next = newNode;
      current.prev = newNode;

      this.size++;
    }
  }

  // Remove a node from a specific position
  remove(position) {
    if (position < 0 || position >= this.size) {
      console.log("Invalid position");
      return;
    }

    let current = this.head;

    if (position === 0) {
      this.head = current.next;
      if (this.head) this.head.prev = null;
      else this.tail = null;
    } else if (position === this.size - 1) {
      current = this.tail;
      this.tail = current.prev;
      this.tail.next = null;
    } else {
      let index = 0;
      while (index < position) {
        current = current.next;
        index++;
      }
      current.prev.next = current.next;
      current.next.prev = current.prev;
    }

    this.size--;
    return current.data;
  }

  // Print the list forward
  printForward() {
    let current = this.head;
    let result = '';
    while (current) {
      result += current.data + ' <-> ';
      current = current.next;
    }
    result += 'null';
    console.log(result);
  }

  // Print the list backward
  printBackward() {
    let current = this.tail;
    let result = '';
    while (current) {
      result += current.data + ' <-> ';
      current = current.prev;
    }
    result += 'null';
    console.log(result);
  }

  // Get the size of the list
  getSize() {
    return this.size;
  }

  // Check if the list is empty
  isEmpty() {
    return this.size === 0;
  }
}

// Usage example
const list = new DoublyLinkedList();
list.append(10);
list.append(20);
list.prepend(5);
list.insert(15, 2);
list.printForward();  // Output: 5 <-> 10 <-> 15 <-> 20 <-> null
list.printBackward(); // Output: 20 <-> 15 <-> 10 <-> 5 <-> null
console.log(list.remove(1));  // Output: 10
list.printForward();  // Output: 5 <-> 15 <-> 20 <-> null
console.log(list.getSize());  // Output: 3
console.log(list.isEmpty());  // Output: false
```

```
CLASS Node
  data
  prev = null
  next = null

CLASS DoublyLinkedList
  head = null
  tail = null
  size = 0

  FUNCTION append(data)
    newNode = NEW Node(data)
    IF head is null THEN
      head = newNode
      tail = newNode
    ELSE
      tail.next = newNode
      newNode.prev = tail
      tail = newNode
    INCREMENT size

  FUNCTION prepend(data)
    newNode = NEW Node(data)
    IF head is null THEN
      head = newNode
      tail = newNode
    ELSE
      newNode.next = head
      head.prev = newNode
      head = newNode
    INCREMENT size

  FUNCTION insert(data, position)
    IF position is 0 THEN
      prepend(data)
    ELSE IF position equals size THEN
      append(data)
    ELSE
      newNode = NEW Node(data)
      current = head
      FOR i = 0 TO position - 1
        current = current.next
      newNode.next = current
      newNode.prev = current.prev
      current.prev.next = newNode
      current.prev = newNode
      INCREMENT size

  FUNCTION remove(position)
    IF position is 0 THEN
      data = head.data
      head = head.next
      IF head is not null THEN head.prev = null
      ELSE tail = null
    ELSE IF position equals size - 1 THEN
      data = tail.data
      tail = tail.prev
      tail.next = null
    ELSE
      current = head
      FOR i = 0 TO position - 1
        current = current.next
      data = current.data
      current.prev.next = current.next
      current.next.prev = current.prev
    DECREMENT size
    RETURN data

  FUNCTION printForward()
    current = head
    WHILE current is not null
      PRINT current.data
      current = current.next

  FUNCTION printBackward()
    current = tail
    WHILE current is not null
      PRINT current.data
      current = current.prev

  FUNCTION getSize()
    RETURN size

  FUNCTION isEmpty()
    RETURN size EQUALS 0

END CLASS
```

This implementation provides a basic structure for a doubly linked list with methods for appending, prepending, inserting, removing, and printing elements in both directions. The pseudocode offers a quick overview of the logic behind each operation.