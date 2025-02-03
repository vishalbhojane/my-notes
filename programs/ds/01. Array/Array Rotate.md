Create a function `rotate(nums, k)` that rotates an array `nums` to the right by `k` steps. The function should:
1. Modify the array in-place without using extra space.
2. Handle arrays of integers with any length, including empty arrays.
3. Work with any integer value of `k` (positive, negative, or zero).
4. Handle cases where `k` is larger than the array length.

## Solution

```javascript
function rotate(nums, k) {
    k = ((k % nums.length) + nums.length) % nums.length;
    reverse(nums, 0, nums.length - 1);
    reverse(nums, 0, k - 1);
    reverse(nums, k, nums.length - 1);
}

function reverse(nums, start, end) {
    while (start < end) {
        [nums[start], nums[end]] = [nums[end], nums[start]];
        start++;
        end--;
    }
}
```

Steps Explanation:
1. Normalize k: `k = ((k % nums.length) + nums.length) % nums.length;`
   - Handles both positive and negative k
   - Ensures k is within array bounds
2. Reverse the entire array
3. Reverse the first k elements
4. Reverse the remaining n-k elements

Usage

```javascript
let arr1 = [1, 2, 3, 4, 5];
rotate(arr1, 2);
console.log(arr1); // [4, 5, 1, 2, 3]

let arr2 = [1, 2];
rotate(arr2, 3);
console.log(arr2); // [2, 1]

let arr3 = [1, 2, 3];
rotate(arr3, -1);
console.log(arr3); // [2, 3, 1]

let arr4 = [];
rotate(arr4, 1);
console.log(arr4); // []
```