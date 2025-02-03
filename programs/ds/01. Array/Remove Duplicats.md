Create a function `removeDuplicates` that removes duplicates from a sorted array of integers in-place and returns the new length of the array. The function should:
1. Handle arrays of any length, including empty arrays.
2. Modify the input array in-place without using extra space.
3. Preserve the relative order of elements.
4. Return the new length of the array after removing duplicates.

## Solution

```javascript
function removeDuplicates(nums) {
    if (nums.length === 0) return 0;
 
    let writePointer = 1;
 
    for (let readPointer = 1; readPointer < nums.length; readPointer++) {
        if (nums[readPointer] !== nums[readPointer - 1]) {
            nums[writePointer] = nums[readPointer];
            writePointer++;
        }
    }
 
    return writePointer;
}
```

Core Logic:
1. Use two pointers: a write pointer for the position of the next unique element, and a read pointer to scan the array.
2. Copy unique elements to the write pointer position as they are encountered.
3. The write pointer's final position indicates the count of unique elements.

Usage

```javascript
console.log(removeDuplicates([1, 1, 2])); // 2
console.log(removeDuplicates([1, 1, 1, 1])); // 1
console.log(removeDuplicates([1, 2, 3, 4])); // 4
console.log(removeDuplicates([1, 1, 2, 2, 3])); // 3
console.log(removeDuplicates([])); // 0
```