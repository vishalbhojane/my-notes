Create a method `merge(otherList)` within the LinkedList class that merges the current sorted list with another sorted list. The method should:
1. Merge the two lists in ascending order.
2. Modify the current list in-place.
3. Handle lists of any length, including empty lists.
4. Update the head, tail, and length of the current list appropriately.

## Solution

```javascript
merge(otherList) {
    let otherHead = otherList.head;
    let dummy = { value: 0, next: null };
    let current = dummy;

    while (this.head !== null && otherHead !== null) {
        if (this.head.value < otherHead.value) {
            current.next = this.head;
            this.head = this.head.next;
        } else {
            current.next = otherHead;
            otherHead = otherHead.next;
        }
        current = current.next;
    }

    if (this.head !== null) {
        current.next = this.head;
    } else {
        current.next = otherHead;
        this.tail = otherList.tail;
    }

    this.head = dummy.next;
    this.length += otherList.length;
}
```

Core Logic:
1. Use a dummy node to simplify handling the head of the merged list.
2. Iterate through both lists, comparing values and linking nodes in ascending order.
3. After one list is exhausted, link the remaining nodes of the other list.
4. Update the head, tail, and length of the current list.

Usage

```javascript
const list1 = new LinkedList(1);
list1.push(3);
list1.push(5);

const list2 = new LinkedList(2);
list2.push(4);
list2.push(6);

list1.merge(list2);
console.log(list1.toString()); // Output: 1 -> 2 -> 3 -> 4 -> 5 -> 6
```
