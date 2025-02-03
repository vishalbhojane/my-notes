Create a function `findPairs` that finds all pairs of numbers from two arrays that sum up to a given target value. The function should:
1. Accept two arrays of numbers (arr1 and arr2) and a target sum.
2. Return an array of pairs, where each pair consists of one number from arr1 and one from arr2 that sum to the target.
3. Handle cases where multiple pairs or no pairs are found.

## Solution

```javascript
function findPairs(arr1, arr2, target) {
    const set = new Set(arr1);
    const pairs = [];

    for (const num of arr2) {
        const complement = target - num;
        if (set.has(complement)) {
            pairs.push([complement, num]);
        }
    }

    return pairs;
}
```

Core Logic:
1. Create a Set from arr1 for efficient lookups.
2. Iterate through arr2, calculating the complement (target - current number).
3. If the complement exists in the Set (i.e., in arr1), add the pair to the result.

Usage

```javascript
console.log(findPairs([1, 2, 3], [4, 5, 6], 7)); // [[3, 4], [2, 5], [1, 6]]
console.log(findPairs([1, 2], [3, 4], 5)); // [[2, 3], [1, 4]]
console.log(findPairs([1, 2], [3, 4], 10)); // []
console.log(findPairs([], [1, 2], 3)); // []
```