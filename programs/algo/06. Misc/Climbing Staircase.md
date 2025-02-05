Create a function `climbingStaircase` that calculates the number of ways to climb n stairs, given that a person can climb either 1 or 2 stairs at a time. The function should:

1. Handle any positive integer input for n.
2. Return the number of distinct ways to reach the top of the staircase.
3. Use an efficient algorithm to solve the problem.

## Solution

```javascript
function climbingStaircase(n) {
    if (n <= 1) return 1;

    const numOfWays = [1, 1];

    for (let i = 2; i <= n; i++) {
        numOfWays[i] = numOfWays[i - 1] + numOfWays[i - 2];
    }

    return numOfWays[n];
}
```

Core Logic:
1. Use dynamic programming to build up the solution.
2. Start with base cases for 0 and 1 stairs.
3. For each subsequent stair, the number of ways to reach it is the sum of ways to reach the previous two stairs.
4. This follows the Fibonacci sequence pattern.

Time Complexity: O(n), where n is the number of stairs.
Space Complexity: O(n) to store the array of ways for each step.

Usage

```javascript
console.log(climbingStaircase(1)); // 1
console.log(climbingStaircase(2)); // 2
console.log(climbingStaircase(3)); // 3
console.log(climbingStaircase(4)); // 5
console.log(climbingStaircase(5)); // 8
console.log(climbingStaircase(10)); // 89
```