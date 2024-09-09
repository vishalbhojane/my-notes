[75. Sort Colors](https://leetcode.com/problems/sort-colors/)

Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

We will use the integers 0, 1, and 2 to represent the color red, white, and blue, respectively.

You must solve this problem without using the library's sort function.

Example 1:
Input: `nums = [2,0,2,1,1,0]`
Output: `[0,0,1,1,2,2]`

Example 2:
Input: nums = `[2,0,1]`
Output: `[0,1,2]`

Constraints:
`n == nums.length`
`1 <= n <= 300`
`nums[i]` is either 0, 1, or 2.

```
create start and end pointer
create curr pointer and iterate through array
if curr is 0, swap with start, start++ curr++
if curr is 1, curr++
if curr is 2, swap with end, end--
```

```js
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var sortColors = function(nums){
  let start = 0
  let end = nums.length - 1
  let curr = 0
  
  function swap(arr,a,b){
    let temp = arr[a]
    arr[a] = arr[b]
    arr[b] = temp
  }
  
  while(curr <= end){
    if(nums[curr] === 0) {
      swap(nums, curr, start)
      curr++
      start++
    } else if(nums[curr] === 1){
       curr++
    } else if(nums[curr] === 2){
      swap(nums, curr, end)
      end--
    }
  }
  
  return nums
};
```

