Create a function `sortStack(stack)` that sorts a stack in ascending order. The function should:
1. Use an additional stack to help in sorting.
2. Sort the elements in-place without using any other data structures.
3. Handle stacks of any size, including empty stacks.
4. Maintain the stack property (Last-In-First-Out) throughout the sorting process.

## Solution

```javascript
function sortStack(stack) {
    const additionalStack = new Stack();

    while (!stack.isEmpty()) {
        const temp = stack.pop();

        while (!additionalStack.isEmpty() && additionalStack.peek() > temp) {
            stack.push(additionalStack.pop());
        }

        additionalStack.push(temp);
    }

    while (!additionalStack.isEmpty()) {
        stack.push(additionalStack.pop());
    }
}
```

Core Logic:
1. Create an additional stack to temporarily store sorted elements.
2. Pop elements from the original stack one by one.
3. For each popped element, move larger elements from the additional stack back to the original stack.
4. Insert the popped element in its correct position in the additional stack.
5. After processing all elements, transfer them back to the original stack to maintain the correct order.

Usage

```javascript
const stack = new Stack();
stack.push(3);
stack.push(1);
stack.push(4);
stack.push(2);

console.log("Before sorting:", stack.toString());
sortStack(stack);
console.log("After sorting:", stack.toString());

// Output:
// Before sorting: 2 4 1 3
// After sorting: 4 3 2 1
```

## Complexity

Time = O(n^2) in the worst case, where n is the number of elements in the stack. This is because for each element, we might need to move all other elements between the two stacks.
Space = O(n) as we use an additional stack that might need to store all the elements at some point.