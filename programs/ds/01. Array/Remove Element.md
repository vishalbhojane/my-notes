Create a function `removeElement` that removes all instances of a given value from an array of integers in-place and returns the new length of the array. The function should:
1. Handle arrays of any length, including empty arrays.
2. Modify the input array in-place without using extra space.
3. Return the new length of the array after removing the specified value.
4. Allow for changing the order of elements in the array.

## Solution

```javascript
function removeElement(nums, val) {
    let writeIndex = 0;
    
    for (let readIndex = 0; readIndex < nums.length; readIndex++) {
        if (nums[readIndex] !== val) {
            nums[writeIndex] = nums[readIndex];
            writeIndex++;
        }
    }
    
    return writeIndex;
}
```

Core Logic:
1. Use two pointers: a write index for the position to place non-matching elements, and a read index to scan the array.
2. Copy elements not equal to the given value to the write index position.
3. The final write index position indicates the count of elements not equal to the given value.

Usage

```javascript
console.log(removeElement([3, 2, 2, 3], 3)); // 2
console.log(removeElement([0, 1, 2, 2, 3, 0, 4, 2], 2)); // 5
console.log(removeElement([1, 2, 3, 4], 5)); // 4
console.log(removeElement([], 3)); // 0
console.log(removeElement([7, 7, 7, 7], 7)); // 0
```