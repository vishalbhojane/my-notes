Create a function flat that takes a multi-dimensional array arr and a depth n as input. The function should return a new array where subarrays are flattened up to the specified depth.

```javascript
var flat = function (arr, n) {
    if(n === 0) {
        return arr.slice()
    }

    let result = []

    for(let i = 0; i < arr.length; i++){
        if(Array.isArray(arr[i]) && n > 0){
            result.push(...flat(arr[i], n - 1))
        } else {
            result.push(arr[i])
        }
    }

    return result
};
```

Usage

```javascript
const arr = [1, 2, 3, [4, 5, 6], [7, 8, [9, 10, 11], 12], [13, 14, 15]];
console.log(flat(arr, 0)); // [1, 2, 3, [4, 5, 6], [7, 8, [9, 10, 11], 12], [13, 14, 15]]
console.log(flat(arr, 1)); // [1, 2, 3, 4, 5, 6, 7, 8, [9, 10, 11], 12, 13, 14, 15]
console.log(flat(arr, 2)); // [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]
```