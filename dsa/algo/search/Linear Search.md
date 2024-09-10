```
go through all the elements in an array from the beginning
return index of matching element
return -1 if nothing found
```

```js
function linearSearch(arr, target) {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] === target) {
            return i
        }
    }
    return -1
}

console.log(linearSearch([1, 2, 3, 4], 3))
console.log(linearSearch([1, 2, 3, 4], 5))
```

Time Complexity
O(n)

