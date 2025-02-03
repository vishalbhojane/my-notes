Create a function chunk that takes an array arr and a chunk size size as input. The function should return a new array where the original array is divided into subarrays (chunks) of length size. The last chunk may be shorter if there aren't enough elements.

```javascript
var chunk = function(arr, size) {
    if(arr.length === 0){
        return arr
    }

    const result = []

    for(let i = 0; i < arr.length; i = i + size){
        result.push(arr.slice(i, i + size))
    }

    return result
};
```

Usage

```javascript
console.log(chunk([1,2,3,4,5], 1)); // [[1],[2],[3],[4],[5]]
console.log(chunk([1,9,6,3,2], 3)); // [[1,9,6],[3,2]]
console.log(chunk([8,5,3,2,6], 6)); // [[8,5,3,2,6]]
console.log(chunk([], 1)); // []
```
