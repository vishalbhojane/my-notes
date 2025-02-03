Create a function `longestConsecutiveSequence` that finds the length of the longest consecutive sequence of integers in an unsorted array. The function should:
1. Accept an array of integers as input.
2. Return the length of the longest consecutive sequence of numbers.
3. Handle empty arrays and arrays of any length.
4. Consider numbers as consecutive if they differ by 1, regardless of their order in the input array.

## Solution

```javascript
function longestConsecutiveSequence(nums) {
    const numSet = new Set(nums);
    let longestStreak = 0;

    for (const num of numSet) {
        if (!numSet.has(num - 1)) {
            let currentNum = num;
            let currentStreak = 1;

            while (numSet.has(currentNum + 1)) {
                currentNum++;
                currentStreak++;
            }

            longestStreak = Math.max(longestStreak, currentStreak);
        }
    }

    return longestStreak;
}
```

Core Logic:
1. Create a Set from the input array for O(1) lookups.
2. Iterate through each number in the Set.
3. For each number that could be the start of a sequence (i.e., no smaller consecutive number exists), count the length of the consecutive sequence.
4. Keep track of the longest sequence found.

Usage

```javascript
console.log(longestConsecutiveSequence([1, 2, 3, 4, 5])); // 5
console.log(longestConsecutiveSequence([1, 3, 5, 2, 4])); // 5
console.log(longestConsecutiveSequence([2, 1, 4, 7, 3])); // 4
console.log(longestConsecutiveSequence([9, 1, 3, 10, 2, 20, 21])); // 2
console.log(longestConsecutiveSequence([100, 4, 200, 1, 3, 2])); // 4
console.log(longestConsecutiveSequence([])); // 0
```