Write a method called `hasLoop` that is part of the linked list class.
The method should be able to detect if there is a cycle or loop present in the linked list.
You are required to use Floyd's cycle-finding algorithm (also known as the "tortoise and the hare" algorithm) to detect the loop.
This algorithm uses two pointers: a slow pointer and a fast pointer. The slow pointer moves one step at a time, while the fast pointer moves two steps at a time. If there is a loop in the linked list, the two pointers will eventually meet at some point. If there is no loop, the fast pointer will reach the end of the list.

The method should follow these guidelines:
1. Create two pointers, `slow` and `fast`, both initially pointing to the head of the linked list.
2. Traverse the list with the `slow` pointer moving one step at a time, while the `fast` pointer moves two steps at a time.
3. If there is a loop in the list, the `fast` pointer will eventually meet the `slow` pointer. If this occurs, the method should return `true`.
4. If the `fast` pointer reaches the end of the list or encounters a `null` value, it means there is no loop in the list. In this case, the method should return `false`.

Output:
- Return `true` if the linked list has a loop.
- Return `false` if the linked list does not have a loop.

Constraints:
- You are not allowed to use any additional data structures (such as arrays) or modify the existing data structure.
- You can only traverse the linked list once.

![[dsa-ll-q-has-loop-1.png]]

![[dsa-ll-q-has-loop-2.png]]

![[dsa-ll-q-has-loop-3.png]]

The `hasLoop()` function is used to detect if a linked list contains a loop (cycle) or not.  
It also utilizes the "tortoise and hare" algorithm. 

Here's a step-by-step explanation of the logic:
1. Initialize two pointers, `slow` and `fast`, both pointing to the head of the linked list.  
2. Traverse the linked list using a while loop. The loop continues as long as `fast` is not `null` (i.e., it has not reached the end of the list), and `fast.next` is also not `null` (i.e., there is at least one more node after the current `fast` node).  
3. Inside the loop, move the `slow` pointer one step forward (i.e., `slow = slow.next`) and the `fast` pointer two steps forward (i.e., `fast = fast.next.next`).  
4. Check if the `slow` and `fast` pointers have become equal. If they have, it means there is a loop in the linked list, and the function returns `true`.  
5. If the loop terminates without the `slow` and `fast` pointers becoming equal, it means the linked list has no loop, and the function returns `false`.  

The "tortoise and hare" algorithm works by having two pointers move at different speeds through the linked list. If there is a loop, the faster pointer (the hare) will eventually catch up to the slower pointer (the tortoise) inside the loop. If there is no loop, the faster pointer will reach the end of the list.

```js
hasLoop() {
    // Initialize 'slow' and 'fast' pointers at the head node
    // 'slow' will move 1 step at a time
    // 'fast' will move 2 steps at a time
    let slow = this.head;
    let fast = this.head;
 
    // Continue loop if 'fast' pointer and 'fast.next'
    // are not null. This also prevents errors
    while (fast !== null && fast.next !== null) {
        // Move 'slow' 1 step forward in the list
        slow = slow.next;
 
        // Move 'fast' 2 steps forward in the list
        fast = fast.next.next;
 
        // Check if 'slow' and 'fast' pointers meet
        if (slow === fast) {
            // If they meet, it confirms a loop
            // Return true to indicate a loop
            return true;
        }
    }
 
    // If loop ends without meeting of pointers,
    // it confirms absence of loop in the list
    return false;
}
```