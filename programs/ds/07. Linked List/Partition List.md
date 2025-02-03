Create a method `partitionList(x)` that partitions the linked list such that all nodes with values less than `x` come before nodes with values greater than or equal to `x`. The method should:
1. Preserve the original relative order of the nodes.
2. Modify the linked list in-place without using additional data structures.
3. Traverse the linked list only once.
4. Not modify the values in the list's nodes.

## Solution

```javascript
partitionList(x) {
    if (!this.head) return;

    const dummy1 = new Node(0);
    const dummy2 = new Node(0);
    let prev1 = dummy1;
    let prev2 = dummy2;
    let current = this.head;

    while (current !== null) {
        if (current.value < x) {
            prev1.next = current;
            prev1 = current;
        } else {
            prev2.next = current;
            prev2 = current;
        }
        current = current.next;
    }

    prev2.next = null;
    prev1.next = dummy2.next;

    this.head = dummy1.next;
}
```

Core Logic:
1. Use two dummy nodes to create separate chains for values less than `x` and values greater than or equal to `x`.
2. Traverse the list once, appending each node to the appropriate chain.
3. Connect the two chains at the end to form the partitioned list.

Usage

```javascript
let list = new LinkedList();
list.append(3);
list.append(8);
list.append(5);
list.append(10);
list.append(2);
list.append(1);

console.log("Before partition:");
list.print(); // 3 -> 8 -> 5 -> 10 -> 2 -> 1

list.partitionList(5);

console.log("After partition:");
list.print(); // 3 -> 2 -> 1 -> 8 -> 5 -> 10
```