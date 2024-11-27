Implement a member function called `findMiddleNode()` that finds and returns the middle node of the linked list.  
  
**Note: this** `LinkedList` **implementation does not have a** `length` **member variable.**

Output:
- Return the middle node of the linked list.
- If the list has an even number of nodes, return the second middle node (the one closer to the end).

Constraints:
- You are not allowed to use any additional data structures (such as arrays) or modify the existing data structure.
- **You can only traverse the linked list once.**


Example 1:

Suppose you have a `LinkedList` object, list, with the following values:  
1 -> 2 -> 3 -> 4 -> 5
After calling the `findMiddleNode()` function:
`let middle = list.findMiddleNode();`
The middle node should have the value 3.

Example 2:

Now suppose you have a LinkedList object, list, with the following values:  
1 -> 2 -> 3 -> 4 -> 5 -> 6
After calling the `findMiddleNode()` function:
`let middle = list.findMiddleNode();`
The middle node should have the value 4.

---
##### My Solution
Create a helper function to get length of the `LinkedList`

```js
getLength(){
    let length = 0;
    let temp = this.head
    while(temp){
        length++;
        temp = temp.next
    }
    return length;
}

findMiddleNode(){
    let length = this.getLength();
    let mid = Math.floor(length/2);
    let temp = this.head;
    for(let i = 0; i < mid; i++){
        temp = temp.next
    }
    return temp
}
```

##### Solution 2

The `findMiddleNode()` function uses the "tortoise and hare" algorithm to find the middle node of a linked list.  
  
Here's a step-by-step explanation of the logic:

1. Initialize two pointers, `slow` and `fast`, both pointing to the head of the linked list.
2. Traverse the linked list using a while loop. The loop continues as long as `fast` is not `null` (i.e., it has not reached the end of the list), and `fast.next` is also not `null` (i.e., there is at least one more node after the current `fast` node).    
3. Inside the loop, move the `slow` pointer one step forward (i.e., `slow = slow.next`) and the `fast` pointer two steps forward (i.e., `fast = fast.next.next`).
4. Since the `fast` pointer moves twice as fast as the `slow` pointer, by the time the `fast` pointer reaches the end of the list or goes beyond it, the `slow` pointer will be at the middle node.
5. When the loop terminates, return the `slow` pointer, which now points to the middle node.

In the case of an even number of nodes, the `fast` pointer will reach the end of the list, while the `slow` pointer will point to the first middle node (the one closer to the head). For an odd number of nodes, the `fast` pointer will go beyond the end of the list, and the `slow` pointer will point to the exact middle node.

```js
findMiddleNode() {
    // Initialize slow and fast pointers at head
    let slow = this.head;
    let fast = this.head;
    // Iterate through the list
    while (fast !== null && fast.next !== null) {
        // Move slow pointer one step
        slow = slow.next;
        // Move fast pointer two steps
        fast = fast.next.next;
    }
    // Return middle node when fast reaches end
    return slow;
}
```
