Create a method `reverseBetween(m, n)` that reverses the nodes between indexes `m` and `n` (inclusive, using 0-based indexing) in the linked list. The method should:
1. Reverse the specified portion of the list in-place.
2. Handle linked lists of any length, including empty lists.
3. Assume that `m` and `n` are not out of bounds.
4. Traverse the linked list only once.

## Solution

```javascript
reverseBetween(m, n) {
    if (!this.head) return;

    const dummy = new Node(0);
    dummy.next = this.head;
    let prev = dummy;

    for (let i = 0; i < m; i++) {
        prev = prev.next;
    }

    let current = prev.next;
    for (let i = 0; i < n - m; i++) {
        const temp = current.next;
        current.next = temp.next;
        temp.next = prev.next;
        prev.next = temp;
    }

    this.head = dummy.next;
}
```

Core Logic:
1. Use a dummy node to simplify edge cases, especially when modifying the head.
2. Move a `prev` pointer to the node just before the reversal starts.
3. Reverse the specified portion by moving each node to the front of the reversed segment.
4. Update the head of the list if necessary.

Usage

```javascript
let list = new LinkedList();
list.append(1);
list.append(2);
list.append(3);
list.append(4);
list.append(5);

console.log("Before reversal:");
list.print(); // 1 -> 2 -> 3 -> 4 -> 5

list.reverseBetween(1, 3);

console.log("After reversal:");
list.print(); // 1 -> 4 -> 3 -> 2 -> 5

list.reverseBetween(0, 4);

console.log("After full reversal:");
list.print(); // 5 -> 2 -> 3 -> 4 -> 1
```