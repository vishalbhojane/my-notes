Create a function `subarraySum(nums, target)` that finds a subarray in the given array whose sum equals the target. The function should:
1. Use a Map to store cumulative sums and their indices.
2. Return an array containing the start and end indices of the subarray that sums to the target.
3. Return an empty array if no such subarray exists.
4. Handle arrays of any length, including empty arrays.

## Solution

```javascript
function subarraySum(nums, target) {
    const sumIndex = new Map();
    sumIndex.set(0, -1);
    let currentSum = 0;

    for (let i = 0; i < nums.length; i++) {
        currentSum += nums[i];

        if (sumIndex.has(currentSum - target)) {
            return [sumIndex.get(currentSum - target) + 1, i];
        }

        sumIndex.set(currentSum, i);
    }

    return [];
}
```

Core Logic:
1. Create a Map to store cumulative sums and their indices.
2. Initialize the Map with a sum of 0 at index -1.
3. Iterate through the array, maintaining a running sum.
4. For each sum, check if (currentSum - target) exists in the Map.
5. If it exists, we've found a subarray that sums to the target.
6. If not, add the current sum and its index to the Map.

Usage

```javascript
console.log(subarraySum([1, 4, 20, 3, 10, 5], 33));  // [2, 4]
console.log(subarraySum([1, 2, 3], 3));              // [0, 1]
console.log(subarraySum([1, 2, 3, 4, 5], 9));        // [1, 3]
console.log(subarraySum([1, 2, 3], 6));              // [0, 2]
console.log(subarraySum([1, 2, 3], 10));             // []
```

## Complexity

Time = O(n), where n is the length of the input array, as it iterates through the array once
Space = O(n) in the worst case, where we might need to store all cumulative sums in the Map.