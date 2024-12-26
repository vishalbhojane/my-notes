The `removeElement` function takes an array of integers (`nums`) and an integer value (`val`).  
  
The function's purpose is to remove all instances of `val` in the array `nums` in-place and return the new length of the array.  
  
In simpler terms, the function modifies the given array by shifting all elements that are not equal to `val` to the start of the array, and it returns the length of the array after the removal of `val`.

Constraints:

- The array could have zero or more elements.

- Do not allocate extra space for another array; you must do this by modifying the input array in-place with O(1) extra memory.

- The order of elements can be changed. It doesn't matter what you leave beyond the new length.

Parameters:

- `nums`: An array of integers, possibly containing duplicates.

- `val`: An integer value that needs to be removed from `nums`.


Returns:

- The function returns an integer representing the new length of the array `nums`.


Examples

1. Basic Example
 ```js
let nums = [3, 2, 2, 3];
let val = 3;
let len = removeElement(nums, val);
// The array nums should be modified to [2, 2]
// The function should return 2
```

2. Array with Different Elements
```jx
let nums = [0, 1, 2, 2, 3, 0, 4, 2];
let val = 2;
let len = removeElement(nums, val);
// The array nums should be modified to [0, 1, 3, 0, 4]
// The function should return 5
```

3. Array with No Match
```js
let nums = [1, 2, 3, 4];
let val = 5;
let len = removeElement(nums, val);
// The array nums should be unchanged: [1, 2, 3, 4]
// The function should return 4
```

4. Empty Array
```js
let nums = [];
let val = 3;
let len = removeElement(nums, val);
// The array nums should be unchanged: []
// The function should return 0
```

5. All Elements are `val`

```js
let nums = 7, 7, 7, 7;
let val = 7;
let len = removeElement(nums, val);
// The array nums should be empty: 
// The function should return 0
```

##### Solution

```js
function removeElement(nums, val) {
    let i = 0;
    for (let j = 0; j < nums.length; j++) {
        if (nums[j] !== val) {
            nums[i] = nums[j];
            i++;
        }
    }
    return i;
}
```