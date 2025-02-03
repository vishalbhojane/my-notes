Create a function `findMiddleNode()` that finds and returns the middle node of a linked list. The function should:
1. Handle linked lists of any length, including empty lists.
2. Return the middle node without using any additional data structures.
3. If the list has an even number of nodes, return the second middle node (the one closer to the end).
4. Traverse the linked list only once.

## Solution

```javascript
findMiddleNode() {
    if (!this.head) return null;

    let slow = this.head;
    let fast = this.head;

    while (fast !== null && fast.next !== null) {
        slow = slow.next;
        fast = fast.next.next;
    }

    return slow;
}
```

Core Logic:
1. Use two pointers: a slow pointer and a fast pointer, both starting at the head.
2. Move the slow pointer one step at a time and the fast pointer two steps at a time.
3. When the fast pointer reaches the end or goes beyond, the slow pointer will be at the middle node.

Usage

```javascript
let list1 = new LinkedList();
list1.append(1);
list1.append(2);
list1.append(3);
list1.append(4);
list1.append(5);
console.log(list1.findMiddleNode().value); // 3

let list2 = new LinkedList();
list2.append(1);
list2.append(2);
list2.append(3);
list2.append(4);
list2.append(5);
list2.append(6);
console.log(list2.findMiddleNode().value); // 4

let emptyList = new LinkedList();
console.log(emptyList.findMiddleNode()); // null
```
