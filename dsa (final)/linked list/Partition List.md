Implement a member function called `partitionList(x)` that partitions the linked list such that all nodes with values less than `x` come before nodes with values greater than or equal to `x`. 

Note: this linked list class does not have a tail which will make this method easier to implement.

The original relative order of the nodes should be preserved.

Input:
- An integer `x`, the partition value.

Output:
- The function should modify the linked list in-place, such that all nodes with values less than `x` come before nodes with values greater than or equal to `x`. 

Constraints:
- You are not allowed to use any additional data structures (such as arrays) or modify the existing data structure.
- You can only traverse the linked list once.
- You can create temporary nodes to make the implementation simpler.


Example 1:
Input:
Linked List: `3 -> 8 -> 5 -> 10 -> 2 -> 1` x: `5`

Process:
- Values less than 5: `3`, `2`, `1`
- Values greater than or equal to 5: `8`, `5`, `10`

Output:
Linked List: `3 -> 2 -> 1 -> 8 -> 5 -> 10`

Example 2:
Input:
Linked List: `1 -> 4 -> 3 -> 2 -> 5 -> 2` x: `3`

Process:
- Values less than 3: `1`, `2`, `2`
- Values greater than or equal to 3: `4`, `3`, `5`

Output:
Linked List: `1 -> 2 -> 2 -> 4 -> 3 -> 5`

Tips:
1. While traversing the linked list, maintain two separate chains: one for values less than `x` and one for values greater than or equal to `x`.
2. Use dummy nodes to simplify the handling of the heads of these chains.
3. After processing the entire list, connect the two chains to get the desired arrangement.

Note:
The solution must maintain the relative order of nodes. For instance, in the first example, even though `8` appears before `5` in the original list, the partitioned list must still have `8` before `5` as their relative order remains unchanged.

Note:
You must solve the problem WITHOUT MODIFYING THE VALUES in the list's nodes (i.e., only the nodes' `next` pointers may be changed.)

```js
partitionList(x) {
    // If the list is empty, do nothing
    if (this.head === null) return;
 
    // Create dummy nodes for two sublists
    const dummy1 = new Node(0);
    const dummy2 = new Node(0);
    // Initialize prev pointers for sublists
    let prev1 = dummy1;
    let prev2 = dummy2;
    // Initialize current pointer at head
    let current = this.head;
 
    // Iterate through the list
    while (current !== null) {
        // If current value is less than x
        if (current.value < x) {
            // Add current node to the first sublist
            prev1.next = current;
            prev1 = current;
        } else {
            // Add current node to the second sublist
            prev2.next = current;
            prev2 = current;
        }
        // Move current pointer to the next node
        current = current.next;
    }
 
    // Terminate the second sublist
    prev2.next = null;
    // Merge the sublists
    prev1.next = dummy2.next;
 
    // Update the head of the list
    this.head = dummy1.next;
}
```

The `partitionList(x)` function is used to rearrange a linked list in such a way that all nodes with values less than x come before nodes with values greater than or equal to x.  

Here's a step-by-step explanation of the logic:
1. If the head of the linked list is `null`, return, as there is nothing to rearrange.
2. Create two dummy nodes, `dummy1` and `dummy2`. These dummy nodes will be used to build two separate linked lists: one for nodes with values less than x and the other for nodes with values greater than or equal to x.
3. Initialize two pointers, `prev1` and `prev2`, pointing to `dummy1` and `dummy2`, respectively. These pointers will be used to append nodes to the two separate linked lists.
4. Initialize a `current` pointer pointing to the head of the linked list.
5. Iterate through the linked list using a while loop that continues as long as `current` is not `null`: a. If the `current` node's value is less than x, update `prev1.next` to point to the `current` node and move `prev1` forward. b. If the `current` node's value is greater than or equal to x, update `prev2.next` to point to the `current` node and move `prev2` forward. c. Move the `current` pointer to the next node.
6. After the loop, set `prev2.next` to `null` to terminate the second linked list.
7. Connect the two separate linked lists by setting `prev1.next` to `dummy2.next`.
8. Update the head of the linked list to point to the `next` node of `dummy1`.

The function has a time complexity of O(n), where n is the number of nodes in the list, as it traverses the list only once.