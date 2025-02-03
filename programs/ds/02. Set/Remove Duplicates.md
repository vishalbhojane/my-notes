Create a function `removeDuplicates` that removes duplicate elements from an array and returns a new array containing only unique elements. The function should:
1. Accept an array of any type of elements as input.
2. Return a new array with all duplicate elements removed.
3. Preserve the order of the first occurrence of each element.

## Solution

```javascript
function removeDuplicates(myList) {
    const uniqueSet = new Set(myList);
    return Array.from(uniqueSet);
}
```

Core Logic:
1. Use a Set to automatically remove duplicates.
2. Convert the Set back to an array to maintain array functionality.

Usage

```javascript
console.log(removeDuplicates([1, 2, 2, 3, 4, 4, 5])); // [1, 2, 3, 4, 5]
console.log(removeDuplicates(['a', 'b', 'a', 'c', 'b'])); // ['a', 'b', 'c']
console.log(removeDuplicates([true, false, true, true])); // [true, false]
console.log(removeDuplicates([])); // []
```