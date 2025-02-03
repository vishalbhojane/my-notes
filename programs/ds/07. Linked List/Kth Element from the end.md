Create a method `findKthFromEnd(k)` that finds and returns the kth node from the end of the linked list. The method should:
1. Handle linked lists of any length, including empty lists.
2. Return the kth node from the end without using any additional data structures.
3. Return null if k is greater than or equal to the number of nodes in the list.
4. Traverse the linked list only once.

## Solution

```javascript
findKthFromEnd(k) {
    if (!this.head) return null;

    let slow = this.head;
    let fast = this.head;

    // Move fast pointer k steps ahead
    for (let i = 0; i < k; i++) {
        if (fast === null) return null;
        fast = fast.next;
    }

    // Move both pointers until fast reaches the end
    while (fast !== null) {
        slow = slow.next;
        fast = fast.next;
    }

    return slow;
}
```

Core Logic:
1. Use two pointers: a slow pointer and a fast pointer, both starting at the head.
2. Move the fast pointer k steps ahead.
3. Move both pointers at the same pace until the fast pointer reaches the end.
4. The slow pointer will then be at the kth node from the end.

Usage

```javascript
let list = new LinkedList();
list.append(1);
list.append(2);
list.append(3);
list.append(4);
list.append(5);

console.log(list.findKthFromEnd(2).value); // 4
console.log(list.findKthFromEnd(4).value); // 2
console.log(list.findKthFromEnd(5).value); // 1
console.log(list.findKthFromEnd(6)); // null
```