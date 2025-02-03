Create a function `twoSum(nums, target)` that finds two numbers in an array that add up to a target sum. The function should:
1. Use a Map to store numbers and their indices.
2. Return an array containing the indices of the two numbers that sum to the target.
3. Return an empty array if no such pair exists.
4. Handle arrays of any length, including empty arrays.

## Solution

```javascript
function twoSum(nums, target) {
    const numMap = new Map();

    for (let i = 0; i < nums.length; i++) {
        const num = nums[i];
        const complement = target - num;

        if (numMap.has(complement)) {
            return [numMap.get(complement), i];
        }
        numMap.set(num, i);
    }

    return [];
}
```

Core Logic:
1. Create a Map to store numbers and their indices.
2. Iterate through the array once.
3. For each number, calculate its complement (target - number).
4. If the complement exists in the Map, return its index and the current index.
5. If not, add the current number and its index to the Map.
6. If no pair is found, return an empty array.

Usage

```javascript
console.log(twoSum([2, 7, 11, 15], 9));  // [0, 1]
console.log(twoSum([3, 2, 4], 6));       // [1, 2]
console.log(twoSum([3, 3], 6));          // [0, 1]
console.log(twoSum([1, 2, 3, 4, 5], 10)); // []
console.log(twoSum([], 0));              // []
```

## Complexity

Time  = O(n), where n is the length of the input array, as it iterates through the array once.
Space = O(n), in the worst case, where we might need to store all numbers in the Map before finding a pair.