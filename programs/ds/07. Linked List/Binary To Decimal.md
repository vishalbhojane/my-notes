Create a method `binaryToDecimal()` that converts a binary number represented by a linked list to its decimal equivalent. The method should:
1. Traverse the linked list once.
2. Convert the binary representation to decimal.
3. Handle linked lists of any length, including empty lists.
## Solution

```javascript
binaryToDecimal() {
    let num = 0;
    let current = this.head;

    while (current !== null) {
        num = num * 2 + current.value;
        current = current.next;
    }

    return num;
}
```

Core Logic:
1. Initialize a variable `num` to store the decimal result.
2. Traverse the linked list from left to right (most significant bit to least significant bit).
3. For each node, multiply the current `num` by 2 and add the node's value (0 or 1).

Usage

```javascript
let list = new LinkedList();
list.append(1);
list.append(0);
list.append(1);

console.log(list.binaryToDecimal()); // 5

let emptyList = new LinkedList();
console.log(emptyList.binaryToDecimal()); // 0

let singleNodeList = new LinkedList();
singleNodeList.append(1);
console.log(singleNodeList.binaryToDecimal()); // 1
```