Create a method `swapFirstLast()` that swaps the values of the first and last nodes of a doubly linked list. The method should:
1. Modify the doubly linked list in-place.
2. Handle lists of any length, including empty lists and lists with a single node.
3. Only swap the values, not the nodes themselves.

## Solution

```javascript
swapFirstLast() {
    if (this.length < 2) return;

    const temp = this.head.value;
    this.head.value = this.tail.value;
    this.tail.value = temp;
}
```

Core Logic:
1. Check if the list has at least two nodes.
2. Use a temporary variable to store the head's value.
3. Assign the tail's value to the head.
4. Assign the temporary (original head) value to the tail.

Usage

```javascript
let list = new DoublyLinkedList();
list.append(1);
list.append(2);
list.append(3);
list.append(4);
list.append(5);

console.log("Before swapping:");
list.print(); // 1 <-> 2 <-> 3 <-> 4 <-> 5

list.swapFirstLast();

console.log("After swapping:");
list.print(); // 5 <-> 2 <-> 3 <-> 4 <-> 1

// Test with a list of two nodes
let list2 = new DoublyLinkedList();
list2.append(1);
list2.append(2);

console.log("Before swapping:");
list2.print(); // 1 <-> 2

list2.swapFirstLast();

console.log("After swapping:");
list2.print(); // 2 <-> 1

// Test with a single node (should not change)
let list3 = new DoublyLinkedList();
list3.append(1);

console.log("Before swapping:");
list3.print(); // 1

list3.swapFirstLast();

console.log("After swapping:");
list3.print(); // 1
```