```js
function swap(arr, firstIndex, lastIndex) {
  let temp = arr[firstIndex];
  arr[firstIndex] = arr[lastIndex];
  arr[lastIndex] = temp;
}

function pivot(array, pivotIndex = 0, endIndex = array.length - 1) {
  let swapIndex = pivotIndex;
  for (let i = pivotIndex + 1; i <= endIndex; i++) {
    if (array[i] < array[pivotIndex]) {
      swapIndex++;
      swap(array, swapIndex, i);
    }
  }
  swap(array, pivotIndex, swapIndex);

  return swapIndex;
}

function quickSort(array, left = 0, right = array.length - 1) {
  if (left >= right) return;

  let pivotIndex = pivot(array, left, right);
  quickSort(array, left, pivotIndex - 1);
  quickSort(array, pivotIndex + 1, right);
}

```

##### Big O
Space Complexity: O(1)
We are not creating any new array, we are manipulating the existing array

Time Complexity: O(n log n)
For pivot we have to go through entire array, it is O(n)
For quickSort we call it 3 times for 8 array elements, it is O(log n)

For already sorted array it is O(n^2)
For nearly sorted array `insertionSort` is better