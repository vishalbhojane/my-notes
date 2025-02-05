Create a function `towerOfHanoi` that solves the Tower of Hanoi puzzle for n disks. The function should:

1. Handle any positive integer input for n.
2. Print the steps to move the disks from the source rod to the destination rod.
3. Use recursion to solve the problem efficiently.

## Solution

```javascript
function towerOfHanoi(n, source, destination, auxiliary) {
    if (n === 1) {
        console.log(`Move disk 1 from ${source} to ${destination}`);
        return;
    }

    towerOfHanoi(n - 1, source, auxiliary, destination);
    console.log(`Move disk ${n} from ${source} to ${destination}`);
    towerOfHanoi(n - 1, auxiliary, destination, source);
}
```

Core Logic:
1. Use recursion to break down the problem into smaller subproblems.
2. For n disks:
   a. Move n-1 disks from source to auxiliary rod.
   b. Move the nth disk from source to destination rod.
   c. Move the n-1 disks from auxiliary to destination rod.
3. The base case is when there's only one disk to move.

Time Complexity: O(2^n - 1), where n is the number of disks.
Space Complexity: O(n) due to the recursive call stack.

Usage

```javascript
console.log("For 2 disks:");
towerOfHanoi(2, 'A', 'C', 'B');

console.log("\nFor 3 disks:");
towerOfHanoi(3, 'A', 'C', 'B');

console.log("\nFor 4 disks:");
towerOfHanoi(4, 'A', 'C', 'B');
```

```text
For 2 disks:
Move disk 1 from A to B
Move disk 2 from A to C
Move disk 1 from B to C

For 3 disks:
Move disk 1 from A to C
Move disk 2 from A to B
Move disk 1 from C to B
Move disk 3 from A to C
Move disk 1 from B to A
Move disk 2 from B to C
Move disk 1 from A to C

For 4 disks:
Move disk 1 from A to B
Move disk 2 from A to C
Move disk 1 from B to C
Move disk 3 from A to B
Move disk 1 from C to A
Move disk 2 from C to B
Move disk 1 from A to B
Move disk 4 from A to C
Move disk 1 from B to C
Move disk 2 from B to A
Move disk 1 from C to A
Move disk 3 from B to C
Move disk 1 from A to B
Move disk 2 from A to C
Move disk 1 from B to C
```

This solution efficiently solves the Tower of Hanoi problem using recursion, demonstrating the steps to move the disks according to the rules of the puzzle. The time complexity grows exponentially with the number of disks, making it impractical for large values of n.