Create a function `maxSubarray` that finds the contiguous subarray with the largest sum within an array of integers and returns that sum. The function should:
1. Handle arrays of any length, including empty arrays.
2. Work with both positive and negative integers.
3. Return the largest sum of any contiguous subarray.
4. Return 0 for an empty array.

## Solution

```javascript
function maxSubarray(nums) {
    if (nums.length === 0) return 0;

    let maxSum = nums[0];
    let currentSum = nums[0];

    for (let i = 1; i < nums.length; i++) {
        currentSum = Math.max(nums[i], currentSum + nums[i]);
        maxSum = Math.max(maxSum, currentSum);
    }

    return maxSum;
}
```

Core Logic:
1. Initialize the maximum sum and current sum with the first element.
2. For each subsequent element, decide whether to start a new subarray or extend the existing one.
3. Keep track of the overall maximum sum encountered.

Usage

```javascript
console.log(maxSubarray([-2, 1, -3, 4, -1, 2, 1, -5, 4])); // 6
console.log(maxSubarray([1])); // 1
console.log(maxSubarray([-1, -2, -3])); // -1
console.log(maxSubarray([])); // 0
console.log(maxSubarray([0, -1, -2])); // 0
```