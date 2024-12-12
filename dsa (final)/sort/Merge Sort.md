```js
function merge(array1, array2) {
  let combined = [];
  let i = 0;
  let j = 0;
  while (i < array1.length && j < array2.length) {
    if (array1[i] < array2[j]) {
      combined.push(array1[i]);
      i++;
    } else {
      combined.push(array2[j]);
      j++;
    }
  }
  while (i < array1.length) {
    combined.push(array1[i]);
    i++;
  }
  while (j < array2.length) {
    combined.push(array2[j]);
    j++;
  }
  return combined;
}

function mergeSort(array) {
  if (array.length === 1) return array;

  let midIndex = Math.floor(array.length / 2);
  let left = mergeSort(array.slice(0, midIndex));
  let right = mergeSort(array.slice(midIndex));

  return merge(left, right);
}
```

##### Big O
Space Complexity: O(n)
Creates number of arrays equal to number of elements present in the original array 

Time Complexity: O(n log n)
`mergeSort` Takes 3 steps to break down array of 8 elements to 8 arrays, that is O(log n)
`merge` need to iterate through each item in to merge them, so that is O(n)

