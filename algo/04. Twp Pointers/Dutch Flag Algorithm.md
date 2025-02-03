Create a function `sortColors(nums)` that sorts an array of numbers representing colors (0 for red, 1 for white, and 2 for blue) in-place. The function should:
1. Use the three-pointer approach (Dutch National Flag algorithm).
2. Handle arrays of any length, including empty arrays.
3. Modify the input array in-place without using any built-in sort functions.

## Solution

```javascript
function sortColors(nums) {
    let start = 0;
    let end = nums.length - 1;
    let curr = 0;

    function swap(arr, a, b) {
        let temp = arr[a];
        arr[a] = arr[b];
        arr[b] = temp;
    }

    while (curr <= end) {
        if (nums[curr] === 0) {
            swap(nums, curr, start);
            curr++;
            start++;
        } else if (nums[curr] === 1) {
            curr++;
        } else if (nums[curr] === 2) {
            swap(nums, curr, end);
            end--;
        }
    }

    return nums;
}
```

Core Logic:
1. Initialize three pointers: `start` (for 0s), `end` (for 2s), and `curr` (current element).
2. Iterate through the array using `curr` pointer:
   - If the current element is 0, swap it with the element at `start`, increment both `curr` and `start`.
   - If the current element is 1, just move `curr` forward.
   - If the current element is 2, swap it with the element at `end`, decrement `end`.
3. Continue until `curr` pointer crosses `end` pointer.

Usage

```javascript
console.log(sortColors([2,0,2,1,1,0])); // [0,0,1,1,2,2]
console.log(sortColors([2,0,1]));       // [0,1,2]
console.log(sortColors([0]));           // [0]
console.log(sortColors([1]));           // [1]
console.log(sortColors([]));            // []
```

## Complexity

Time = O(n), where n is the length of the input array, as it iterates through the array once.
Space = O(1), as it sorts the array in-place without using any extra space proportional to the input size.