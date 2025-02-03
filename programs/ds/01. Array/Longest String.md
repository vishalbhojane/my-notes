Create a function `findLongestString` that takes an array of strings and returns the longest string in the array. The function should:
1. Handle arrays of any length, including empty arrays.
2. Work with arrays containing only string elements.
3. Return the first encountered string if multiple strings have the same longest length.
4. Return an empty string if the input array is empty.

## Solution

```javascript
function findLongestString(stringArray) {
    let longestString = "";
    for (let str of stringArray) {
        if (str.length > longestString.length) {
            longestString = str;
        }
    }
    return longestString;
}
```

Usage

```javascript
console.log(findLongestString(["apple", "banana", "pea"])); // "banana"
console.log(findLongestString(["a", "b", "c"])); // "a"
console.log(findLongestString(["orange", "cherry", "banana"])); // "orange"
console.log(findLongestString(["", "", ""])); // ""
console.log(findLongestString(["apple", "a", "banana", "bb"])); // "banana"
console.log(findLongestString([])); // ""
```