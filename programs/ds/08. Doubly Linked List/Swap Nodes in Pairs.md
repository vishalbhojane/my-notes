Create a method `swapPairs()` that swaps every two adjacent nodes of a doubly linked list. The method should:
1. Modify the doubly linked list in-place.
2. Handle lists of any length, including empty lists and lists with an odd number of nodes.
3. Traverse the doubly linked list only once.
4. Update all necessary pointers, including the head of the list.

## Solution

```javascript
swapPairs() {
    const dummy = new Node(0);
    dummy.next = this.head;
    let prev = dummy;

    while (this.head !== null && this.head.next !== null) {
        const firstNode = this.head;
        const secondNode = this.head.next;

        // Swap the pairs
        prev.next = secondNode;
        firstNode.next = secondNode.next;
        secondNode.next = firstNode;

        // Update prev pointers
        secondNode.prev = prev;
        firstNode.prev = secondNode;
        if (firstNode.next !== null) {
            firstNode.next.prev = firstNode;
        }

        // Move to the next pair
        this.head = firstNode.next;
        prev = firstNode;
    }

    // Update the head of the list
    this.head = dummy.next;
    if (this.head) this.head.prev = null;
}
```

Core Logic:
1. Use a dummy node to simplify handling the head of the list.
2. Iterate through the list, swapping pairs of nodes.
3. Update both next and prev pointers for each swapped pair.
4. Handle the case where the list has an odd number of nodes.

Usage

```javascript
let list = new DoublyLinkedList();
list.append(1);
list.append(2);
list.append(3);
list.append(4);
list.append(5);

console.log("Before swapping pairs:");
list.print(); // 1 <-> 2 <-> 3 <-> 4 <-> 5

list.swapPairs();

console.log("After swapping pairs:");
list.print(); // 2 <-> 1 <-> 4 <-> 3 <-> 5

// Test with odd number of nodes
let list2 = new DoublyLinkedList();
list2.append(1);
list2.append(2);
list2.append(3);

console.log("Before swapping pairs:");
list2.print(); // 1 <-> 2 <-> 3

list2.swapPairs();

console.log("After swapping pairs:");
list2.print(); // 2 <-> 1 <-> 3

// Test with empty list
let emptyList = new DoublyLinkedList();
emptyList.swapPairs();
console.log("Empty list after swapping pairs:");
emptyList.print(); // (empty)
```
