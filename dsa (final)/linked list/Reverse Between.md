Implement a member function called `reverseBetween(m, n)` that reverses the nodes between indexes (using 0-based indexing)  `m` and `n` (inclusive) in the linked list.  
  
Note: this linked list class does NOT have a `tail` which will make this method easier to implement.  
  
Assumption: You can assume that `m` and `n` are not out of bounds.

Output:
- The function should reverse the nodes between the indexes `m` and `n` in the linked list. The reversal should be done in-place.

Constraints:
- You are not allowed to use any additional data structures (such as arrays) or modify the existing data structure.
- You can only traverse the linked list once.


Example 1:
Suppose you have a LinkedList object, list, with the following values:  
1 -> 2 -> 3 -> 4 -> 5
After calling the `reverseBetween(1, 3)` function:
1. list.reverseBetween(1, 3);
The linked list should now have the following values:  
1 -> 4 -> 3 -> 2 -> 5


Example 2:
Now suppose you have a LinkedList object, list, with the following values:  
1 -> 2 -> 3 -> 4 -> 5 -> 6
After calling the `reverseBetween(3, 5)` function:
1. list.reverseBetween(3, 5);
The linked list should now have the following values:  
1 -> 2 -> 3 -> 6 -> 5 -> 4

```js
// Function to reverse nodes in a linked list between positions m and n (0-based index)
reverseBetween(m, n) {
    // Check if the list is empty. If it is, no action is needed.
    if (this.head === null) return;

    // Create a dummy node. This is a common technique used in linked list problems
    // to simplify edge cases, like when modifying the head of the list.
    const dummy = new Node(0);

    // Link this dummy node to the head of the list.
    // Now, dummy acts as a precursor to the head node.
    dummy.next = this.head;

    // 'prev' will eventually point to the node just before the start of the reversal.
    // Initially, 'prev' is set to the dummy node.
    let prev = dummy;

    // Iterate to position 'prev' to the node just before where reversal begins.
    // Since indices are 0-based, this loop moves 'prev' 'm' nodes forward.
    for (let i = 0; i < m; i++) {
        prev = prev.next;
    }

    // 'current' points to the first node that will be reversed.
    // This is the mth node in the list (considering 0-based indexing).
    let current = prev.next;

    // The loop for the actual reversal of the segment between m and n.
    // It runs (n - m) times, moving each node in turn to the position after 'prev'.
    for (let i = 0; i < n - m; i++) {
        // 'temp' temporarily stores the next node in line to be moved.
        const temp = current.next;

        // Bypass 'temp' in the current positioning.
        current.next = temp.next;

        // Insert 'temp' between 'prev' and 'prev.next'.
        // This step effectively moves 'temp' to the front of the reversal segment.
        temp.next = prev.next;
        prev.next = temp;
    }

    // Update the head of the list if the head was part of the reversal.
    // This is where the dummy node becomes useful, as it simplifies this operation.
    this.head = dummy.next;
}
```

The `reverseBetween(m, n)` function is used to reverse a portion of a linked list between positions m and n, inclusive.  

Here's a step-by-step explanation of the logic:
1. If the head of the linked list is `null`, return, as there is nothing to reverse.    
2. Create a dummy node and set its `next` pointer to the head of the linked list. This dummy node simplifies the manipulation of pointers, especially at the beginning of the list.
3. Initialize a `prev` pointer and set it to the dummy node. Move the `prev` pointer m steps forward using a for loop. After the loop, `prev` will point to the node right before the mth node. 
4. Initialize a `current` pointer to the mth node by setting it to `prev.next`.
5. Iterate through the list n - m times using a for loop, reversing the portion of the list between positions m and n: a. Create a `temp` pointer and set it to the next node of `current`. b. Update the `next` pointer of `current` to point to the node after `temp`. c. Update the `next` pointer of `temp` to point to the node right after `prev`. d. Update the `next` pointer of `prev` to point to `temp`.
6. After the loop, the portion of the linked list between positions m and n has been reversed. Set the head of the linked list to the `next` pointer of the dummy node.

The function traverses the list only once, making it efficient with a time complexity of O(n), where n is the number of nodes in the list.