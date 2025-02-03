Create a function `findDuplicates(nums)` that finds all duplicate numbers in an array. The function should:
1. Use a Map to count occurrences of each number in the array.
2. Return an array containing all numbers that appear more than once.
3. Handle arrays of any length, including empty arrays.

## Solution

```javascript
function findDuplicates(nums) {
    const numCounts = new Map();
    
    for (let num of nums) {
        numCounts.set(num, (numCounts.get(num) || 0) + 1);
    }
    
    const duplicates = [];
    
    for (let [key, value] of numCounts.entries()) {
        if (value > 1) {
            duplicates.push(key);
        }
    }
    
    return duplicates;
}
```

Core Logic:
1. Create a Map to store the count of each number in the input array.
2. Iterate through the input array, updating the count for each number in the Map.
3. Iterate through the Map entries, adding numbers with a count greater than 1 to the duplicates array.
4. Return the array of duplicates.

Usage

```javascript
console.log(findDuplicates([1,2,3,4,5]));     // []
console.log(findDuplicates([1,1,2,2,3]));     // [1,2]
console.log(findDuplicates([1,1,1,1,1]));     // [1]
console.log(findDuplicates([]));              // []
console.log(findDuplicates([1,2,3,3,2,1,4])); // [1,2,3]
```