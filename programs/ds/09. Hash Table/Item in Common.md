Create a function `itemInCommon(array1, array2)` that checks if two arrays have at least one item in common. The function should:
1. Use a Map to efficiently store and check for items from the first array.
2. Return `true` if a common item is found, `false` otherwise.
3. Handle arrays of any length, including empty arrays.

## Solution

```javascript
function itemInCommon(array1, array2) {
    const myMap = new Map();

    for (let i of array1) {
        myMap.set(i, true);
    }

    for (let j of array2) {
        if (myMap.has(j)) {
            return true;
        }
    }

    return false;
}
```

Core Logic:
1. Create a Map to store items from the first array.
2. Iterate through the first array, adding each item to the Map.
3. Iterate through the second array, checking if each item exists in the Map.
4. If a common item is found, immediately return true.
5. If no common items are found after checking all items, return false.

Usage

```javascript
console.log(itemInCommon([1,3,5], [2,4,5]));  // true
console.log(itemInCommon([1,3,5], [2,4,6]));  // false
console.log(itemInCommon([], [2,4,6]));       // false
console.log(itemInCommon([1,2,3], []));       // false
console.log(itemInCommon([1,2,3], [4,5,6,1])); // true
```

