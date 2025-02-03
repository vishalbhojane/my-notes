Create a method `reverse()` that reverses the nodes of a doubly linked list. The method should:
1. Modify the doubly linked list in-place.
2. Reverse the nodes themselves, not just their values.
3. Handle lists of any length, including empty lists and lists with a single node.
4. Update both the head and tail pointers of the list.

## Solution

```javascript
reverse() {
    let current = this.head;
    let temp = null;

    while (current !== null) {
        // Swap prev and next pointers
        temp = current.prev;
        current.prev = current.next;
        current.next = temp;

        // Move to the next node (which is now current.prev)
        current = current.prev;
    }

    // Swap head and tail
    temp = this.head;
    this.head = this.tail;
    this.tail = temp;
}
```

Core Logic:
1. Traverse the list, swapping the `prev` and `next` pointers for each node.
2. Use a temporary variable to facilitate the swapping.
3. After reversing all connections, swap the head and tail of the list.

Usage

```javascript
let list = new DoublyLinkedList();
list.append(1);
list.append(2);
list.append(3);
list.append(4);
list.append(5);

console.log("Before reversal:");
list.print(); // 1 <-> 2 <-> 3 <-> 4 <-> 5

list.reverse();

console.log("After reversal:");
list.print(); // 5 <-> 4 <-> 3 <-> 2 <-> 1

// Test with a list of two nodes
let list2 = new DoublyLinkedList();
list2.append(1);
list2.append(2);

console.log("Before reversal:");
list2.print(); // 1 <-> 2

list2.reverse();

console.log("After reversal:");
list2.print(); // 2 <-> 1

// Test with a single node (should not change)
let list3 = new DoublyLinkedList();
list3.append(1);

console.log("Before reversal:");
list3.print(); // 1

list3.reverse();

console.log("After reversal:");
list3.print(); // 1
```