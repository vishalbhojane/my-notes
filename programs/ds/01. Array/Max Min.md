Create a function `findMaxMin` that takes an array of numbers and returns an array containing the maximum and minimum values from the input array. The function should:
1. Work with arrays containing at least one element.
2. Handle both integers and floating-point numbers.
3. Not use built-in Math.max() or Math.min() functions.
4. Not sort the array.
5. Return an array `[maximum, minimum]` with the largest and smallest numbers found.

## Solution

```javascript
function findMaxMin(myArray) {
    let maximum = myArray[0];
    let minimum = myArray[0];
    
    for (let i = 1; i < myArray.length; i++) {
        if (myArray[i] > maximum) {
            maximum = myArray[i];
        }
        if (myArray[i] < minimum) {
            minimum = myArray[i];
        }
    }
    
    return [maximum, minimum];
}
```

Usage

```javascript
console.log(findMaxMin([3, 2, 4, 1])); // [4, 1]
console.log(findMaxMin([-1, -2, -3, -4])); // [-1, -4]
console.log(findMaxMin([5, 5, 5, 5])); // [5, 5]
console.log(findMaxMin([7])); // [7, 7]
console.log(findMaxMin([1.1, 2.2, 0.9, 3.7])); // [3.7, 0.9]
console.log(findMaxMin([-1, 2, -3, 4])); // [4, -3]
```