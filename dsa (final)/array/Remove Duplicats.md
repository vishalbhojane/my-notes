The `**removeDuplicates**` function aims to remove duplicates from a sorted array of integers (`**nums**`) and returns the new length of the array.  
  
The function modifies the input array in-place such that each element appears only once and returns the new length.

  

**Constraints:**

- The input array is sorted in ascending order.
    
- The array can be empty or contain any number of elements.
    
- Elements in the array are integers.
    
- The function should not allocate extra space; it must do this by modifying the input array in-place (this means you cannot use another data structure like a set).
    

  

**Parameters:**

- `**nums**`: A sorted array of integers.
    

  

**Returns:**

- The function returns the new length of the array after removing duplicates.
    
- If `**nums**` is empty, the function returns `**0**`.
    

  

**Examples:**

1. **Basic Example**
    
    1. let nums = [1, 1, 2];
    2. let result = removeDuplicates(nums);
    3. // The function should return 2
    4. // The nums array should be modified to [1, 2]
    
2. **Array with All Duplicates**
    
    1. let nums = [1, 1, 1, 1];
    2. let result = removeDuplicates(nums);
    3. // The function should return 1
    4. // The nums array should be modified to [1]
    
3. **Array with No Duplicates**
    
    1. let nums = [1, 2, 3, 4];
    2. let result = removeDuplicates(nums);
    3. // The function should return 4
    4. // The nums array should remain [1, 2, 3, 4]
    
4. **Array with Multiple Sets of Duplicates**
    
    1. let nums = [1, 1, 2, 2, 3];
    2. let result = removeDuplicates(nums);
    3. // The function should return 3
    4. // The nums array should be modified to [1, 2, 3]
    
5. **Empty Array**
    
    1. let nums = [];
    2. let result = removeDuplicates(nums);
    3. // The function should return 0
    4. // The nums array should remain empty

```js
function removeDuplicates(nums) {
    if (nums.length === 0) {
        return 0;
    }
 
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
