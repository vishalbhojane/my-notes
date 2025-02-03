Create a method `removeDuplicates()` that removes all duplicate nodes from the linked list based on their values. The method should:
1. Modify the linked list in-place.
2. Remove all nodes with duplicate values.
3. Preserve the relative order of the remaining nodes.
4. Update the length of the list accordingly.
5. Use a JavaScript Set to keep track of unique node values.

## Solution

```javascript
removeDuplicates() {
    if (!this.head) return;

    const values = new Set();
    let previous = null;
    let current = this.head;

    while (current !== null) {
        if (values.has(current.value)) {
            previous.next = current.next;
            this.length--;
        } else {
            values.add(current.value);
            previous = current;
        }
        current = current.next;
    }
}
```

Core Logic:
1. Use a Set to store unique values encountered in the list.
2. Traverse the list once, removing nodes with duplicate values.
3. Update the list's length when removing duplicates.

Usage

```javascript
let list = new LinkedList();
list.append(1);
list.append(2);
list.append(3);
list.append(2);
list.append(1);
list.append(4);

console.log("Before removing duplicates:");
list.print(); // 1 -> 2 -> 3 -> 2 -> 1 -> 4
console.log("Length:", list.length); // 6

list.removeDuplicates();

console.log("After removing duplicates:");
list.print(); // 1 -> 2 -> 3 -> 4
console.log("Length:", list.length); // 4
```