Introduction to Linked List:
- A Linked List is a linear data structure where elements are stored in nodes.
- Each node contains data and a reference (or link) to the next node.
- The last node typically points to null, indicating the end of the list.
- Main types: Singly Linked List, Doubly Linked List, Circular Linked List.
- Key operations: insertion, deletion, traversal.

Real-world examples of Linked List usage:
1. Implementation of stacks and queues
2. Music playlists (for next and previous song functionality)
3. Undo functionality in software applications
4. Hash tables for handling collisions
5. Memory management in operating systems

```js
// Node class to represent each element in the linked list
class Node {
  constructor(data) {
    this.data = data;
    this.next = null;
  }
}

class LinkedList {
  constructor() {
    this.head = null;  // Head of the list
    this.size = 0;     // Size of the list
  }

  // Add a node to the end of the list
  append(data) {
    const newNode = new Node(data);

    if (!this.head) {
      this.head = newNode;
    } else {
      let current = this.head;
      while (current.next) {
        current = current.next;
      }
      current.next = newNode;
    }

    this.size++;
  }

  // Insert a node at a specific position
  insert(data, position) {
    if (position < 0 || position > this.size) {
      console.log("Invalid position");
      return;
    }

    const newNode = new Node(data);

    if (position === 0) {
      newNode.next = this.head;
      this.head = newNode;
    } else {
      let current = this.head;
      let prev = null;
      let index = 0;

      while (index < position) {
        prev = current;
        current = current.next;
        index++;
      }

      newNode.next = current;
      prev.next = newNode;
    }

    this.size++;
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
    } else {
      let prev = null;
      let index = 0;

      while (index < position) {
        prev = current;
        current = current.next;
        index++;
      }

      prev.next = current.next;
    }

    this.size--;
    return current.data;
  }

  // Print the linked list
  print() {
    let current = this.head;
    let result = '';
    while (current) {
      result += current.data + ' -> ';
      current = current.next;
    }
    result += 'null';
    console.log(result);
  }

  // Get the size of the linked list
  getSize() {
    return this.size;
  }

  // Check if the linked list is empty
  isEmpty() {
    return this.size === 0;
  }
}

// Usage example
const list = new LinkedList();
list.append(10);
list.append(20);
list.append(30);
list.print();  // Output: 10 -> 20 -> 30 -> null
list.insert(15, 1);
list.print();  // Output: 10 -> 15 -> 20 -> 30 -> null
console.log(list.remove(2));  // Output: 20
list.print();  // Output: 10 -> 15 -> 30 -> null
console.log(list.getSize());  // Output: 3
console.log(list.isEmpty());  // Output: false
```

```
CLASS Node
  data
  next = null

CLASS LinkedList
  head = null
  size = 0

  FUNCTION append(data)
    newNode = NEW Node(data)
    IF head is null THEN
      head = newNode
    ELSE
      current = head
      WHILE current.next is not null
        current = current.next
      current.next = newNode
    INCREMENT size

  FUNCTION insert(data, position)
    IF position < 0 OR position > size THEN
      RETURN
    newNode = NEW Node(data)
    IF position is 0 THEN
      newNode.next = head
      head = newNode
    ELSE
      current = head
      prev = null
      index = 0
      WHILE index < position
        prev = current
        current = current.next
        INCREMENT index
      newNode.next = current
      prev.next = newNode
    INCREMENT size

  FUNCTION remove(position)
    IF position < 0 OR position >= size THEN
      RETURN
    current = head
    IF position is 0 THEN
      head = current.next
    ELSE
      prev = null
      index = 0
      WHILE index < position
        prev = current
        current = current.next
        INCREMENT index
      prev.next = current.next
    DECREMENT size
    RETURN current.data

  FUNCTION print()
    current = head
    result = ""
    WHILE current is not null
      APPEND current.data and " -> " to result
      current = current.next
    APPEND "null" to result
    PRINT result

  FUNCTION getSize()
    RETURN size

  FUNCTION isEmpty()
    RETURN size EQUALS 0

END CLASS
```

This implementation provides a basic structure for a singly linked list with methods for appending, inserting, removing, and printing elements. The pseudocode offers a quick overview of the logic behind each operation.