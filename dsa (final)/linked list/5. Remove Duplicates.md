Implement a member function called `removeDuplicates()` that removes all duplicate nodes from the linked list based on their values.  
  
Note: this linked list class does NOT have a `tail` which will make this method easier to implement.

Output:
- The function should modify the linked list in-place, removing all nodes with duplicate values.
 
Constraints:
- You are allowed to use the JavaScript Set data structure to keep track of unique node values.
 
Example 1:
Suppose you have a LinkedList object, list, with the following values:  
1 -> 2 -> 3 -> 2 -> 1 -> 4  
After calling the `removeDuplicates()` function:
1. list.removeDuplicates();
The linked list should now have the following values: 1 -> 2 -> 3 -> 4

Example 2:
Now suppose you have a LinkedList object, list, with the following values:  
3 -> 3 -> 3
After calling the `removeDuplicates()` function:
1.` list.removeDuplicates();`
The linked list should now have the following value: 3

Remember to update the length.
The `removeDuplicates()` function is used to remove duplicate nodes from a linked list. The function traverses the list and removes nodes with duplicate values while maintaining the relative order of the remaining nodes.  

```js
removeDuplicates() {
    // Create a Set to store unique values
    const values = new Set();
    // Initialize previous pointer as null
    let previous = null;
    // Initialize current pointer at head
    let current = this.head;
 
    // Iterate through the list
    while (current !== null) {
        // If value already exists in the set
        if (values.has(current.value)) {
            // Remove the duplicate node by updating previous' next
            previous.next = current.next;
            // Decrement list length
            this.length -= 1;
        } else {
            // Add unique value to the set
            values.add(current.value);
            // Update previous pointer to current node
            previous = current;
        }
        // Move current pointer to the next node
        current = current.next;
    }
}
```
  
Here's a step-by-step explanation of the logic:
1. Create a `Set` named `values` to store the unique values of the linked list nodes.
2. Initialize two pointers: `previous`, initially set to `null`, and `current`, pointing to the head of the linked list.
3. Iterate through the linked list using a while loop that continues as long as `current` is not `null`: a. Check if `values` contains the `current` node's value. If it does, it means the node is a duplicate. Update `previous.next` to point to `current.next` (skipping the `current` node) and decrement the list length by 1. b. If `values` does not contain the `current` node's value, add the value to the set and update `previous` to point to the `current` node. c. Move the `current` pointer to the next node.
 
The function has a time complexity of O(n), where n is the number of nodes in the list, as it traverses the list only once. The space complexity is also O(n), as it uses a set to store unique node values.