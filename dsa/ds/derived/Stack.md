The stack data structure is a sequential collection of elements that follows the principle of Last In First Out (LIFO)
The last element inserted into the stack is first element to be removed
*A stack of plates. The last plate placed on top of the stack is also the first plate removed from the stack.*

Stack is an abstract data type. It is defined by its behaviour rather than being a mathematical model

The Stack data structure supports two main operations
- Push, which adds an element to the collection
- Pop, which removes the most recently added element from the collection

![[stack.jpg]]

## Key points:
- A stack is a linear data structure that follows the Last-In-First-Out (LIFO) principle.
- Elements are added and removed from the same end, called the "top" of the stack.
- Main operations: push (add), pop (remove), peek (view top element).
- Stacks have a fixed size in some implementations, but can be dynamic in others.

### Real-world examples of Stack usage:
1. Undo functionality in text editors
2. Browser history (back button)
3. Function call stack in programming languages
4. Expression evaluation and syntax parsing
5. Backtracking algorithms (e.g., maze solving)

## Implementation - Using Array

Pseudocode

```text
CLASS Stack
  items = empty array

  FUNCTION push(element)
    ADD element TO END OF items

  FUNCTION pop()
    IF isEmpty() THEN
      RETURN "Stack is empty"
    RETURN AND REMOVE last element from items

  FUNCTION peek()
    IF isEmpty() THEN
      RETURN "Stack is empty"
    RETURN last element of items

  FUNCTION isEmpty()
    RETURN true IF items is empty, false OTHERWISE

  FUNCTION size()
    RETURN length of items

  FUNCTION clear()
    SET items to empty array

  FUNCTION print()
    PRINT items as string

END CLASS
```

```js
class Stack {
  constructor() {
    this.items = [];  // Array to store stack elements
  }

  // Add element to the top of the stack
  push(element) {
    this.items.push(element);
  }

  // Remove and return the top element
  pop() {
    if (this.isEmpty()) {
      return "Stack is empty";
    }
    return this.items.pop();
  }

  // Return the top element without removing it
  peek() {
    if (this.isEmpty()) {
      return "Stack is empty";
    }
    return this.items[this.items.length - 1];
  }

  // Check if the stack is empty
  isEmpty() {
    return this.items.length === 0;
  }

  // Return the size of the stack
  size() {
    return this.items.length;
  }

  // Clear the stack
  clear() {
    this.items = [];
  }

  // Print the stack elements
  print() {
    console.log(this.items.toString());
  }
}

// Usage example
const stack = new Stack();
stack.push(10);
stack.push(20);
stack.push(30);
stack.print();  // Output: 10,20,30
console.log(stack.pop());  // Output: 30
console.log(stack.peek()); // Output: 20
console.log(stack.size()); // Output: 2
```

### Using Object

Pseudocode

```
CLASS Stack
  items = empty object
  count = 0

  FUNCTION push(element)
    SET items[count] TO element
    INCREMENT count

  FUNCTION pop()
    IF isEmpty() THEN
      RETURN "Stack is empty"
    DECREMENT count
    result = items[count]
    DELETE items[count]
    RETURN result

  FUNCTION peek()
    IF isEmpty() THEN
      RETURN "Stack is empty"
    RETURN items[count - 1]

  FUNCTION isEmpty()
    RETURN count EQUALS 0

  FUNCTION size()
    RETURN count

  FUNCTION clear()
    SET items TO empty object
    SET count TO 0

  FUNCTION print()
    IF isEmpty() THEN
      PRINT "Stack is empty"
    ELSE
      Initialize empty string result
      FOR i FROM 0 TO count - 1
        APPEND items[i] AND ", " TO result
      PRINT result WITHOUT last ", "

END CLASS
```

```js
class Stack {
  constructor() {
    this.items = {};  // Object to store stack elements
    this.count = 0;   // Counter to keep track of elements and serve as key
  }

  // Add element to the top of the stack
  push(element) {
    this.items[this.count] = element;
    this.count++;
    console.log(`${element} added to ${this.count - 1}`);
  }

  // Remove and return the top element
  pop() {
    if (this.isEmpty()) {
      return "Stack is empty";
    }
    this.count--;
    const result = this.items[this.count];
    delete this.items[this.count];
    console.log(`${result} removed`);
    return result;
  }

  // Return the top element without removing it
  peek() {
    if (this.isEmpty()) {
      return "Stack is empty";
    }
    return this.items[this.count - 1];
  }

  // Check if the stack is empty
  isEmpty() {
    return this.count === 0;
  }

  // Return the size of the stack
  size() {
    return this.count;
  }

  // Clear the stack
  clear() {
    this.items = {};
    this.count = 0;
    console.log("Stack cleared");
  }

  // Print the stack elements
  print() {
    if (this.isEmpty()) {
      console.log("Stack is empty");
    } else {
      let result = "";
      for (let i = 0; i < this.count; i++) {
        result += `${this.items[i]}, `;
      }
      console.log(result.slice(0, -2));  // Remove last comma and space
    }
  }
}

// Usage example
const stack = new Stack();
stack.push(10);
stack.push(20);
stack.push(30);
stack.print();  // Output: 10, 20, 30
console.log(stack.pop());  // Output: 30 removed
console.log(stack.peek()); // Output: 20
console.log(stack.size()); // Output: 2
stack.clear();
console.log(stack.isEmpty()); // Output: true
```

This implementation uses an object to store the stack elements, with the count serving as both the size of the stack and the key for the next element. This approach can be more memory-efficient for large stacks and provides constant-time O(1) performance for push and pop operations.

