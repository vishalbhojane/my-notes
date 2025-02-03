Create a function sortBy that takes an array arr and a function fn as input. The function should return a new array sorted in ascending order based on the values returned by fn when applied to each element of arr.

```javascript
function sortBy(arr, fn) {
    return arr.sort((a, b) => fn(a) - fn(b));
}
```

Usage

```javascript
console.log(sortBy([5, 4, 1, 2, 3], x => x));
// [1, 2, 3, 4, 5]

console.log(sortBy([{"x": 1}, {"x": 0}, {"x": -1}], d => d.x));
// [{"x": -1}, {"x": 0}, {"x": 1}]

console.log(sortBy([[3, 4], [5, 2], [10, 1]], x => x[1]));
// [[10, 1], [5, 2], [3, 4]]
```